# Step-by-Step Guide: How to Use Feature Flags to Increase Deployment Frequency

Deployment frequency is one of the most important metric that DORA (DevOps Research and Assessment) uses to measure the software delivery performance. Many feature flag service providers tell you that feature flag can largely increase the deployment frequency. But how? Here, I will give you a step-by-step guide on how to use feature flags to increase deployment frequency.


**Prerequisites**: 
1. Readers need to have a practical understanding of continuous integration and continuous deployment (CI/CD).
2. Readers need to have a basic understanding of feature flags.

## Step 1, why we need to deploy frequently.

It's all about "Money". The more frequently you deploy, the earlier you can deliver value to the customer. The earlier you deliver value to the customer, the earlier you can get feedback from the customer. The earlier you get feedback from the customer, the earlier you can adjust your product to meet the customer's needs. The earlier you adjust your product to meet the customer's needs, the more money you can make.

## Step 2, understanding what prevent us from deploying frequently.

1. Fear of deployment risk. The more frequently you deploy, the more failed delivery may happen. Each failure bring you more fear, the less frequently you deploy.

Why failure bring us more fear? 

- Bug may impact the customer experience, cause customer churn then revenue loss.
- Rollback, fix and re-deploy will cost more time and make the team exhausted.

2. Big story or big feature. The bigger the story or feature, the more time it takes to develop and test, and the less frequently you can deploy.

Why we keep the story or feature big?

- We want to make the feature perfect before we deploy it.
- The sub-feature of the big feature is not independent, it can't serve the customer independently.

## Step 3, understand the what did we do wrong to prevent failure and reduce fear.

What we did to prevent failure and reduce fear?

1. Make the features we will deploy to be tested as much as possible.
2. Fix a deployment date (every two weeks, every month, even more).
3. Only merge the well tested feature branches to the main, and keep others in the feature branch.
4. Or don't even start the feature which won't be deployed in the next deployment date.

What was wrong with the above practices?

- For points 1 and 2, nothing wrong, but we can do better. 
- For points 3, it may cause long-lived feature branches, and increase the code conflict risk, review cost, and test cost. Especially the performance of testing will largely impact the delivery performance.
- For point 4, hmm... you may lose the opportunity to deliver value to the customer earlier, loss the competitive advantage, **then go broke**. 

## Step 4, what was wrong with the excuse of big story?

1. Let customer tell you whether the feature is perfect or not is a much better way than you think it's perfect.
2. 

## Step 5, if you can't deploy frequently as what your competitors do, you will be out of the game.

The delivery value gap is not too big for each deployment, but it's a huge gap if you accumulate it for a long time, then you will be out of the game.







