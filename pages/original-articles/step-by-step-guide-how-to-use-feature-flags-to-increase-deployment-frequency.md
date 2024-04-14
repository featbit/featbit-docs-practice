# Step-by-Step Guide: How to Use Feature Flags to Increase Deployment Frequency

Deployment frequency is one of the most important metric that DORA (DevOps Research and Assessment) uses to measure the software delivery performance. Many feature flag service providers tell you that feature flag can largely increase the deployment frequency. But how? Here, I will give you a step-by-step guide on how to use feature flags to increase deployment frequency.


**Prerequisites**: 
1. Readers need to have a practical understanding of continuous delivery.
2. Readers need to have a basic understanding of feature flags.

## Step 1, why we need to deploy frequently.

It's all about "Money". The more frequently you deploy, the earlier you can deliver value to the customer. The earlier you deliver value to the customer, the earlier you can get feedback from the customer. The earlier you get feedback from the customer, the earlier you can adjust your product to meet the customer's needs. The earlier you adjust your product to meet the customer's needs, the more money you can make.

The delivery value gap is not too big for each deployment, but it's a huge gap if you accumulate it for a long time. **If you can't deploy frequently as what your competitors do, you will be out of the game**. 

## Step 2, understanding what prevent us from high deployment frequency.

**Fear of deployment risk**. The more frequently you deploy, the more failed delivery may happen. Each failure bring you more fear, the less frequently you deploy. Why failure bring us more fear? 

- Bug may impact the customer experience, cause customer churn then revenue loss.
- Rollback, fix and re-deploy will cost more time and make the team exhausted.

**Big story or big feature**. Many teams can't separate the big story into small pieces. They think the big story is a whole, they can't deploy it until it's all done.

## Step 3, what we may did wrong and thought wrong.

**Case 1**, your team may fix a deployment date for each iteration. They merge some features into the main branch, then make as many tests as possible before the deployment day. During the testing time, no new features are allowed to merge (even no development is allowed). 

-------

Picture for bad practice

-------

They think that's the only way to keep the delivery safe. But you will still have bugs in the production. If there're still other development in progress, this method may leads those development to be long-lived feature branches. 

There's a better way to make the delivery safer and allow you to deploy more features in an iteration.

**Case 2**, why we have to separate the big story into small pieces? Because a big story may introduce a long-live feature branch, which leads a high risk of code conflict, review and test. If you have many of them, it will be a nightmare for the team.

You may think technically it's hard to separate the big story into small pieces, and merge them to the main code without impact the existing service. Feature flags can help you to solve this problem.

## Step 4, feature flag solve the problem.

The main software engineering conception to solve the problem is **decouple the feature release from the deployment**.

- Solve the problem of fear of deployment risk.
- Solve the problem of merge pieces of a big story to the main branch.
- Solve the problem of long-lived feature branch.

To be simple, imagine you have 3 environments, dev, uat and prod. 

- Each time a feature is finished can then be merged into the main branch. 
- Whenever a uat deployment request is submitted, you can immediately create a uat branch based on main.
- You test the features in uat environment. Enable the feature flag to test the new features.
  - If feature is ok, nothing to do. 
  - If feature has bug, report the bug, disable the feature flag, then do nothing else.
- Whenever a prod deployment request is submitted, you can immediately create a prod branch based on uat. Then run the deployment process.
- In the production, enable the feature flag to do TIP then progressive rollout the new feature.

P.S.: Above is an example, please adjust it to fit your own process.






