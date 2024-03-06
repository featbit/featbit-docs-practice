# AB Testing

**Documentation is under construction.**

> Traditional experimentation tools tend to support front-end experiments while neglecting back-end ones. Moreover, they often fail to integrate well with your software deployment process. FeatBit supports “holistic experimentation," letting you seamlessly run both front-end and server-side experiments (including multivariate tests) in a production environment. And it integrates experiments with your normal development process.

## Prerequisites

We assume that you've already completed the last three tutorials in "Get Started":

* You have successfully created two [feature flags](https://www.featbit.co), `game runner` and `difficulty mode` in the tutorial [Create 2 flags for the demo](../create-two-feature-flags.md).
* You have basic experience with how to [interact with the "`Dino Game` " demo](../try-interacting-with-the-demo.md).
* You know how to [connect an SDK](../connect-an-sdk/) to your program or the "Dino Game" demo:
  * Download a demo code sample
  * Initialize SDK
  * Identify a user with customized properties.
  * Implement a feature flag to deliver, and control the feature

## Is DinoGame Demo easy to understand?

You see that we create a DinoGame for users who can get started as easy as possible. But we disagreed on the different versions of the initial process design.  We use AB groups to test the result, we make the results as statistically plausible as possible. We create to groups:

* One control group, "Relase Dino Game" to be the first step in the demo.
* One experimental group, "Difficulty mode" to be the first step in the demo.

We test which one is better to let the people complete the demo.

## Create same sample size for each mode

We let 10% users see "Difficulty mode" as the first step in Demo, 90% users see "Release Dino Game" as the first step (which is the initialized setting).


![](../../getting-started/assets/ab-testing/001.webp)

To keep each group has the same sample size, we need to set AB test that 1/9 users (10% in total users) in control group is considered in the test.

![](../../getting-started/assets/ab-testing/002.webp)

## Create metric when user get 500 points score

You need to define a metric for the test. You create a conversion metric here. If the user completes the entire process, we consider it a successful conversion.

![](../../getting-started/assets/ab-testing/003.webp)

## Create an experimentation for this AB test

Go back to the Overview sub-panel and click the **Add** button

![](../../getting-started/assets/ab-testing/004.webp)

In the **Experiment** drawer, select the feature flag you created above, choose **demo completed** as metric, choose **release dino game** as baseline. Click on the **Save** button.

![](../../getting-started/assets/ab-testing/005.webp)

## Add AB test code in the project

You need to use FeatBit SDK to add code below in DinoGame:

* Add ab test feature flag to split two versions.

![](../../getting-started/assets/ab-testing/006.webp)

* Add a metric event for tracking with fbClient.sendCustomEvent() function.

![](../../getting-started/assets/ab-testing/007.webp)

## Run your experimentation

In the experiment list, click on button **Check result** of experimentation **demo process**.

![](../../getting-started/assets/ab-testing/008.webp)

You'll be directed to the feature flag **Experimentation** tab. Click on the start button in the Experiment. It starts to run!

![](../../getting-started/assets/ab-testing/009.webp)

## View Testing Result & Report

As time changes, we can see the experiment report in the "Experimentation" sub-tab over time. In case of insufficient data, or when the control differences are not significant, we receive the hint in the figure below.

![](../../getting-started/assets/ab-testing/010.webp)

When the data are sufficient and the difference is significant (e.g. p-value less than 0.05), we will receive an indication of which result is superior, as shown in the figure below "Release Dino Game" wins.

![](../../getting-started/assets/ab-testing/011.webp)

