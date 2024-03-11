# Combining Feature Flags with Deployment Strategies to Optimize the Release Process - Part 2 - Making Features Consistent Across Environments

Your team may deploy frequently per day or per week without fixed scheduled deployment date and time. Your team may also deploy once per bi-weekly or monthly with a fixed date and time. 

Regardless of the frequency, your team may make mistake to deploy a feature to production environment without creating it before deployment. This mistake may cause a production issue. To avoid this mistake, you can use a feature flag examination gate during the pipeline.

1. Check if some feature flags missed in current cd pipeline. "Miss" means for example:
   a. The feature flag appears in the testing environment pipeline but not in the production environment pipeline.
   b. The configuration of feature flag is not consistent between the testing environment pipeline and the production environment pipeline.
   c. If you have release plan, try to compare with the plan and the feature flags in the pipeline.
2. Check if the new feature flag is disabled that won't expose new feature to public immediately after deployment. 
3. Check if all feature flags appear in the code are defined in the feature flag management system.
4. If last two steps didn't discover all potential risk, we propose also that when writing a new feature flag, define a default value. Normally we give it a default value of `false` to avoid the feature being enabled by mistake. Or other value that will not enable the new version or configuration of feature. 

In this article, we will discuss how to make features consistent across environments by using FeatBit.

## Check if some feature flags missed in current cd pipeline

1. Use FeatBit Rest APIs to get all feature flags in the two different environments.
2. Compare the feature flags in the two different environments. You can write a program or using an LLM directly.

### Create a API token in FeatBit

