# Microsoft Feature Management Custom Feature Provider

Microsof.FeatureManagement is a feature flag library that allows you to control the availability of features in your .NET application. Along with Azure App Configuration service, it provides a way to separate feature rollout from code deployment, allows you to turn features on and off without redeploying new code. This can be useful for testing in production, canary releases, targeting rollout and A/B testing.

## Why custom feature provider

But many teams don't want to use Azure App Configuration (AAC) service for feature management. Because of:

- Performance limitations, AAC has a limit rate of requests per second and can't support high traffic applications.
- Technical limitations, AAC doesn't support all programming languages and frameworks, but only .NET, Java.
- Vendor lock-in, AAC is a Microsoft service, so you can't use it in other cloud providers or in on-premises environments.
- User friendly limitations, AAC is azure resource based unit, so you need to create a new resource for each environment and project.
- And so on.

So we need to let Microsoft.FeatureManagement library to be used with other feature flag providers. In this article, I will show you how to create a custom feature provider for Microsoft.FeatureManagement library.

## Three methods to implement a custom feature provider

There are 3 methods to create a custom feature provider for Microsoft.FeatureManagement library:

1. Using existing json configuration format, and use built-in feature filter. You need to convert 3rd party feature flag configuration format to Microsoft.FeatureManagement configuration format.
2. Using IFeatureFilter or IContextualFeatureFilter, and use custom feature flag configuration format. You keep the feature flag code in the application, but it's totally a new feature flag service.
3. Using IFeatureFilter or IContextualFeatureFilter, use built-in configuration format. You need to rewrite the built-in feature flag evaluation logic.

FeatureFilter and Built-int Feature Providers can be used together. You can use FeatureFilter to create a custom feature flag service, and use Built-in Feature Providers to create a feature flag service based on existing feature flag service.

```json
"MyFeature": {
    "EnabledFor": [
        {
            "Name": "MyCriteria"
        },
        {
            "Name": "Microsoft.Percentage",
            "Parameters": {
                "Value": 50
            }
        }
    ]
}
```

## Method 1: Convert from custom configuration to Microsoft.FeatureManagement's configuration

Here's an example: FeatBit (an open-source feature flag service built with .NET) has a different configuration format from Microsoft.FeatureManagement. The two services are not 100% compatible with each other. For example:

- FeatBit can have multiple variants for a feature flag, while Microsoft.FeatureManagement only supports boolean values.
- FeatBit allows multiple customized rule conditions, whereas Microsoft.FeatureManagement only supports a few built-in rule conditions.
- Microsoft.FeatureManagement supports recurrence schedules, but FeatBit does not support this feature.
- And so on.

Therefore, you need to find a compromise way to convert your custom feature flag's configuration to Microsoft.FeatureManagement's configuration, such as:

- Only support boolean values for feature flags.
- Map the custom rule conditions to Microsoft.FeatureManagement's built-in rule conditions.
- Ignore the recurrence schedule.

Below is a sample (simplified) of FeatBit's feature flag configuration:


```json
{
    ...
    "key": "featureflagname",
    "variationType": "boolean",
    "variations": [
        {
            ...
            "value": "true"
        },
        {
            ...
            "value": "false"
        }
    ],
    ...
    "rules": [
        {
            "id": "8ee2951d-a121-47d6-b7d0-b33cf633a2ff",
            "name": "Groups",
            ...
            "conditions": [
                {
                    "id": "4c37d50d-81cb-4caa-b3b3-fa91bd80f431",
                    "property": "Groups",
                    "op": "IsOneOf",
                    "value": ["group1"]
                }
            ],
            "variations": [
                {
                    "id": "201909b4-0c7f-4fec-92da-9980f648e2be",
                    "rollout": [
                        0,
                        1
                    ],
                    "exptRollout": 1
                }
            ]
        }
    ],
    ...
}
```

Below is a Microsoft.FeatureManagement's configuration format:

```json
"featureflagname": {
    "EnabledFor": [
        {
            "Name": "Microsoft.Targeting",
            "Parameters": {
                "Audience": {
                    ...
                    "Groups": [
                        {
                            "Name": "group1",
                            "RolloutPercentage": 100
                        },
                    ],
                    ...
                }
            }
        }
    ]
}
```

To convert the FeatBit's feature flag configuration to Microsoft.FeatureManagement's configuration, you need to implement `IFeatureDefinitionProvider` interface and complete the `GetAllFeatureDefinitionsAsync` and `GetFeatureDefinitionAsync` methods. In the `GetAllFeatureDefinitionsAsync` method:

1. Get feature flags from FeatBit service.
2. Convert each feature flag's configuration of FeatBit to Microsoft.FeatureManagement's feature flag configuration.
3. Return the converted feature flags configuration.

```csharp
public class FeatBitFeatureDefinitionProvider : IFeatureDefinitionProvider
{
    private readonly IFbClient _fbClient;
    private IEnumerable<FeatureDefinition> _definitions;

    public FeatBitFeatureDefinitionProvider(IFbClient fbClient)
    {
        _fbClient = fbClient;
        _definitions = Array.Empty<FeatureDefinition>();
    }

#pragma warning disable CS1998 // Async method lacks 'await' operators and will run synchronously
    public async IAsyncEnumerable<FeatureDefinition> GetAllFeatureDefinitionsAsync()
#pragma warning restore CS1998 // Async method lacks 'await' operators and will run synchronously
    {
        // get feature flags from FeatBit
        var flags = _fbClient.AllFlags();

        // convert FeatBit's feature flags to Microsoft.FeatureManagement's feature flag configuration
        _definitions = flags.Select(x => x.ToFeatureDefinition());

        foreach (var definition in _definitions)
        {
            yield return definition;
        }
    }

    public Task<FeatureDefinition> GetFeatureDefinitionAsync(string featureName)
    {
        var feature = _definitions.FirstOrDefault(x => x.Name == featureName);
        return Task.FromResult(feature!);
    }
}
```

You can initialize the Microsoft Feature Management's custom provider `FeatBitFeatureDefinitionProvider` in the `Program.cs` file:

```csharp
...

services.AddSingleton<IFbClient, FbClient>();
services.AddSingleton<IFeatureDefinitionProvider, FeatBitFeatureDefinitionProvider>()
        .AddFeatureManagement();

...
```

## Method 2: Customize IFeatureFilter's method "EvaluateAsync"

IFeatureFilter or IContextualFeatureFilter allow you to create a custom feature filter for Microsoft.FeatureManagement library. The IFeatureFilter interface has only one method: `EvaluateAsync`. You can write your own logic to evaluate the feature flag. The method should return a boolean value to indicate whether the feature is enabled or not.

It's all depends on your requirements. 

![](../original-articles/assets/microsoft-feature-management-custom-feature-provider/pic1.png)

## Solution: Built-in Feature Providers

Microsoft.FeatureManagement library provides many customizable interfaces for feature management. The most important interfaces are:


## Shortage of Microsoft Feature Management