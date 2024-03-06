# SDK

The use of SDK is an essential skill for understanding how to deliver, control, and experiment with the software through feature flags.

Our official offered SDK is the best choice for you to get started with Feature Flag. It is also the best choice for you to implement the best practices of Feature Flag. All SDKs are considering the following best practices:

1. **Local cache**, if the network is not available, the SDK will use the local cache to get the feature flag evaluation result.
2. **Local cache update**, if the network is available, the SDK will update the local cache with the latest feature flag evaluation result.
3. **Real time update**, the SDK will receive the latest feature flag evaluation result from the server in real time.
4. **High Performance**, the SDK will not affect the performance of your application.
5. **Compatible**, the SDK will be compatible with the old version of the SDK. You can upgrade the SDK without any impact on your application.
6. **Server Side Evaluation**, the server-side SDK will evaluate the feature flag on the server side. So you don't need to worry about the network latency and security of your feature flag.
7. **Client side Evaluation**, the client-side SDK will retrieve the final result from server, so you don't worry about the performance impact of the feature flag.
8. **Custom Event & Feature Flags Insights**, the SDK will send the custom event and feature flags insights to the server. So you can get the insights of your feature flags and custom events.
9. **Custom Event for feature experiments**, the SDK will send the custom event to the server. So you can use the custom event to do the feature experiments.
10. **Retry mechansim**, the SDK will retry to connect to the server automatically if the network is not available.
11. **Feature Flag & evluation update listener**, the SDK will notify you when the feature flag or evaluation result is updated.

To getting started with our SDKs, we offer two ways:

- Follow the guide in the portal to quickly implement SDK in your project. You can read quick start guide [here](../getting-started/connect-an-sdk).
- Read the README file of the SDK on GitHub to manually implement SDK in your project.

## Connect SDKs manually

We provide a variety of client-side, server-side, and mobile SDKs to choose from. You can select the language you're good at to accelerate completing your quick start.

### Javascript

We provide a client-side [Javascript/Typescript SDK](https://github.com/featbit/featbit-js-client-sdk). We also provide a "Dino Game" sample for [React](https://github.com/featbit/featbit-samples/tree/main/samples/dino-game/interactive-demo-react) and [Vue](https://github.com/featbit/featbit-samples/tree/main/samples/dino-game/interactive-demo-vue). This SDK works perfectly with Typescript, React, Vue, Angular, etc.

The SDK's GitHub repository contains a full tutorial on how to use it. It also provides a sample project for you to try out.

### Node.js

We provide a [server-side Node.js SDK](https://github.com/featbit/featbit-node-server-sdk) for you to use. This SDK can be used in your console APP or Express.js and other web application framework APP.

The SDK's GitHub repository contains a full tutorial on how to use it. It also provides a sample project for you to try out.


### .NET

We provide a [server-side .NET SDK](https://github.com/featbit/featbit-dotnet-sdk) for you to use. This SDK can be used in your console APP or ASP.NET Core APP.

It can also work for front-end application such as WPF, WinForm, MAUI, etc. But we don't recommend you to use it in mobile application because it consumes more battery power than a real mobile SDK.

The SDK's GitHub repository contains a full tutorial on how to use it. It also provides a sample project for you to try out.

### Java

We provide a [Java SDK](https://github.com/featbit/featbit-java-sdk) for you to use. This SDK can be used in your console APP or Spring Boot APP. 

The SDK's GitHub repository contains a full tutorial on how to use it. It also provides a sample project for you to try out.



### Python

We provide a [Python SDK](https://github.com/featbit/featbit-python-sdk). The SDK's GitHub repository contains a full tutorial on how to use it. It also provides a sample project for you to try out.

### Go

We provide a [Go SDK](https://github.com/featbit/featbit-go-sdk). The SDK's GitHub repository contains a full tutorial on how to use it. It also provides a sample project for you to try out.

### REST APIs & WebSocket

We are continuously dedicated to expanding our platform support. However, it is possible that the specific platform you are targeting may not currently have an available SDK. In such instances, we offer two alternatives:

- Use our REST APIs to get feature flags and evaluation result. See the documentation [Evaluation with REST APIs](retrieve-feature-flags-with-api). 
- Use our WebSocket interface to get real-time feature flags update and evaluation result of a feature flag. Please join our [Slack channel](https://join.slack.com/t/featbit/shared_invite/zt-1ew5e2vbb-x6Apan1xZOaYMnFzqZkGNQ) to get more information about this feature.



### OpenFeature Providers

#### Javascript

We provide a [OpenFeature provider for Javascript SDK](https://github.com/featbit/featbit-js-client-openfeature-provider) for you to use. Be aware, this is a client side SDK, it is intended for use in a single-user context, which can be mobile, desktop or embedded applications. This SDK can only be ran in a browser environment, it is not suitable for NodeJs applications.

The SDK's GitHub repository contains a full tutorial on how to use it. It also provides a sample project for you to try out.

#### Node.js

We provide a [OpenFeature provider for Node.js SDK](https://github.com/featbit/openfeature-provider-node-server) for you to use. This SDK can be used in your console APP or Express.js and other web application framework APP.

The SDK's GitHub repository contains a full tutorial on how to use it. It also provides a sample project for you to try out.

#### Java

We provide a [OpenFeature provider for Java Server SDK](https://github.com/featbit/featbit-openfeature-provider-java-server) for you to use. This SDK can be used in your console APP or Spring Boot APP. 

The SDK's GitHub repository contains a full tutorial on how to use it. It also provides a sample project for you to try out.


## Contribution

We actively encourage and welcome contributions from developers who can help us bridge the gap by creating missing SDKs. If you successfully develop an SDK that aligns with our standards and are interested in collaborating, we would be thrilled to include your work as one of our community SDKs.
