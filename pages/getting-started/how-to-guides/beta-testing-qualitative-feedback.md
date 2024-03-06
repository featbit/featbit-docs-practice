# Beta testing (qualitative feedback)

## **What is Beta testing?**

**Beta Testing** is performed by “real users” of the software application in “real environment” and it can be considered as a form of external User Acceptance Testing. It is the final test before shipping a product to the customers. Direct feedback from customers is a major advantage of Beta Testing. This testing helps to test products in customer’s environment.

![](../../getting-started/assets/beta-testing/001.webp)

Beta version of the software is released to a limited number of end-users of the product to obtain feedback on the product quality. [Beta testing](https://www.featbit.co) reduces product failure risks and provides increased quality of the product through customer validation.

Beta testing with [feature management](https://www.featbit.co/blogs/Free-and-Open-Source-Feature-Flag-Tools) is far less painful than without. In a feature management setting, developers build the new incomplete feature — while attaching a feature flag to it, of course — and then empower product managers to release it to select beta users. In addition to controlling the beta test itself, PMs can also control who to include in the beta group. With PMs thus empowered, developers can spend less time administering beta tests and more time building high-value functionality. And both parties can manage all of this in the FeatBit dashboard.

Owing to the ease of running beta tests with FeatBit, teams end up conducting more tests than they would otherwise. Consequently, they gather more customer feedback earlier in the development process. Product updates are more thoroughly vetted by customers as a result. In heeding customer feedback, developers avoid wasting months building things that flop when brought to market. Instead, they devote their time to creating features and services that customers love.

## The difference between beta testing and alpha testing

The primary difference between an alpha test and a beta test is who is doing the testing—alpha tests are typically performed by internal employees in a lab or stage environment, while actual users in a production setting conduct beta tests.

The goal of the alpha test is to catch as many issues as possible before the product has any public exposure or usage. A test aims to ensure that real users can complete their tasks, get a wide range of users interacting with the product, and test the product’s scalability, performance, and reliability under real-world usage scenarios.

## Prerequisites

We assume that you've already completed the last three tutorials in "Get Started":

* You have successfully created two feature flags, `game runner` and `difficulty mode` in the tutorial [Create 2 flags for the demo](../create-two-feature-flags.md).
* You have essential experience with how to [interact with the "`Dino Game` " demo](../try-interacting-with-the-demo.md).
* You know how to [connect an SDK](../connect-an-sdk/) to your program or the "Dino Game" demo:
  * Download a demo code sample
  * Initialize SDK
  * Identify a user with customized properties.
  * Implement a feature flag to deliver, and control the feature

## Practice with Dino Game

Now we are going to do a simple beta testing to Dino Game with FeatBit.

We want to release Dino Game to：

* a set of external users (age < 20)&#x20;
* some internal internal users

and to collect their feedbacks.

1. Go to Segments page and create a segment with following configuration

![](../../getting-started/assets/beta-testing/002.webp)

&#x20; With this configurations, users in the **Including users** are added in the segment.

2. Go to the feature flag **game runner**'s targeting page, set the default rule to return false and add the following two rules

![](../../getting-started/assets/beta-testing/003.webp)

With this configuration, the feature is released to only internal users and all external users younger than 20 years old.

Currently, collecting user feedbacks is not supported yet by FeatBit, but you can do it your self,  by adding a user survey to the Dino game page for example, or use any tools in the market.
