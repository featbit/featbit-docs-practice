# Identity and Access Management (IAM)

FeatBit IAM gives you precise access control to everything in FeatBit, including feature flags, projects, environments, metrics, and teams, so you can enforce access policies that meet your exact workflow needs.With custom roles, you can:

* Lock your production environment down to a small set of trusted users
* Allow team members to control feature flags on projects or environments that are designated for their team only (Work in progress)
* Allow different permissions at the flag level, such as between experiment flags and operational flags (Work in progress)
* Create private projects that only the team members you select can view.

Our IAM system is inspired by [AWS Identity and Access Management (IAM)](https://aws.amazon.com/iam/). If you're familiar with IAM, there are some similarities.Each team member must have at least one policy.

You can assign team members a built-in policy or one or more custom policies to give them the exact permissions they need.

A team member's initial policy is set when you add a new member to FeatBit.

The one exception to this is the first team member, the default user. His policy is granted Owner permissions automatically, because they are required to configure your team entirely and add more team members.

You can read our topics below to understand how to set permission for a specific team member or a group of members.

* [Teams](teams.md)
* [Groups](groups.md)
* [Policies](policies.md)
