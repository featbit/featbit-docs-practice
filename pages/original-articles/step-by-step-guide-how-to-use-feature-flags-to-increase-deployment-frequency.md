# Step-by-Step Guide: How to Use Feature Flags to Increase Deployment Frequency

Deployment frequency is one of the most important metric that DORA (DevOps Research and Assessment) uses to measure the software delivery performance. Many feature flag service providers tell you that feature flag can largely increase the deployment frequency. But how? Here, I will give you a step-by-step guide on how to use feature flags to increase deployment frequency.


**Prerequisites**: 
1. Readers need to have a practical understanding of continuous integration and continuous deployment (CI/CD). The feature flag practice in this article will be less effective without the mature CI/CD pipelines.
2. Readers need to have a basic understanding of feature flags.

每个功能都用 feature flag 控制。代码被合并到 main 分之后，了之后可以发布到 uat 环境。测试在被通知功能上线后，在uat打开开关进行测试。 当一个部署到生产环境的任务被提交后，uat上的内容可以直接部署至生产环境。只将测试好的逐步发布出去即可。


当一个功能既有web端，又有移动端，甚至后端也进行了修改时。用三个 feature flags 分别控制往往难于管理。可以使用一个 feature flag进行控制，用独立的规则对不同的设备进行灰度发布管控。并且可以使用 approval方法，在修改后让不同的团队审核通过，比如移动端团队的改动可以让web端审核通过。等当多个端整体完成新能力后，再集体清理 feature flag代码。

有一种理论是用 feature flag 拯救 long-lived feature branch 的困难，将代码尽可能的合并到主分支中，用 feature flag 控制。我本人是接受并且实践过这种做法的。但有些团队因为一些原因并支持这种做法，不希望将没有完成的功能合并到主分支。那么可以首先将 long-lived feature 尽可能切割成短 feature，正如scrum里面经常会讲一个story切分成多个小于13 points的小story一样。然后用 feature flag 去控制这个被切割后的功能。

此时，可以将这些小功能部署到UAT,SIT和PROD中。对于独立并不能完成整体业务的能力，UAT（甚至SIT）中仍然可以对其进行有效的测试，而在 PROD 中我们将其关闭即可。

这些大的、小的功能在最终全部可用前，被 feature flags 控制，不仅可以降低部署风险，减少代码分支管理困难，更灵活的和尽可能早的部署发布功能外，还可以将功能的管理变的更加的可追踪化。


