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

- IFeatureFilter
- Built-in Feature Providers

## Two ways to create a custom feature provider

There are two ways to create a custom feature provider for Microsoft.FeatureManagement library:

1. Using existing json configuration format, and use built-in feature filter. You need to convert 3rd party feature flag configuration format to Microsoft.FeatureManagement configuration format.
2. Using IFeatureFilter, and use custom feature flag configuration format. You keep the feature flag code in the application, but it's totally a new feature flag service.


## IFeatureFilter

IFeatureFilter allow you to create a custom feature filter for Microsoft.FeatureManagement library. The IFeatureFilter interface has only one method: `EvaluateAsync`. You can write your own logic to evaluate the feature flag. The method should return a boolean value to indicate whether the feature is enabled or not.

It's all depends on your requirements. 

Get context parameter configuration, this are texts, so this can be the configuration of FeatBit.

## Built-in Feature Providers

Microsoft.FeatureManagement library provides many customizable interfaces for feature management. The most important interfaces are:


## Shortage of Microsoft Feature Management