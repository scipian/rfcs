- Feature Name: `scipian_customer_onboarding`
- Start Date: 2019-06-21
- RFC PR: [scipian/rfcs#0000](https://github.com/scipian/rfcs/pull/3)
- Community Issue: [scipian/community#6](https://github.com/scipian/community/issues/6)

# Summary
[summary]: #summary

Scipian customer onboarding will allow a seamless process for customers to
onboard to the Scipian platform. At a high level, this includes creation of
namespaces, RBAC rules, and distributing the authentication CLI.

# Motivation
[motivation]: #motivation

There is currently no process for a new customer to be onboarded to Scipian. 
Having a smooth process in place will be paramount to onboarding multiple 
customers who want to use Scipian. Having a low barrier of entry will encourage
teams to use Scipian.

# Guide-level explanation
[guide-level-explanation]: #guide-level-explanation

Scipian builds on and uses many Kubernetes primitives. Some of these include 
namespaces and RBAC rules. This allows multiple teams to use Scipian, while 
keeping each team's data and interactions with Scipian separated from eachother.

For onboarding a new team to the Scipian platform, the following is created:

- **Namspace**. A new namespace in the Scipian cluster will be created for a
given team, under a unique name tied to a specific project or application.
- **Role**. This will define a role in Scipian as to what operations are allowed 
in the cluster for anyone asigned to that role. It will be tied to the created 
namespace, and only allow the least privileges required to create Workspaces and 
Runs in Scipian.
- **RoleBinding**. This will bind the created role to a set of users associated 
with the onboarding team.

Below is the flow when onboarding a new customer to Scipian:

- New customer requests to be onboarded to Scipian
- Customer provides list of users, (the email associated with the IDP Scipian 
uses) of all the members who will need to use Scipian
- A Scipian admin will create the Namespace and RBAC roles for the onboarding 
team
- Onboarding team members will use the Scipian Authentication CLI to set up 
their kubeconfigs for interfacing Scipian.

# Reference-level explanation
[reference-level-explanation]: #reference-level-explanation

- RBAC rules and Namespace will be created manually by a Scipian admin using
yaml and `kubectl`. This could be automated later via an onboarding UI, but that
is beyond the scope of this RFC.
- The Scipian authentication CLI will need to be downloaded/installed by an
on-boarding customer.

# Drawbacks
[drawbacks]: #drawbacks

This is a necessary feature of Scipian, and currently no drawbacks have been
identified by adding this feature.

# Rationale and alternatives
[rationale-and-alternatives]: #rationale-and-alternatives

The onboarding outlined in this RFC will be an MVP level feature. Later, this
functionality could be extended to include a self service UI, which would
automate RBAC rules and Namespace creation, thereby removing the requirement for 
a Scipian admin's direct involvement every time a new customer wishes to onboard 
to Scipian.

# Prior art
[prior-art]: #prior-art

Because Scipian extends Kubernetes and utilizes many of Kubernetes' primitives,
the approach outlined in this RFC will use typical Kubernetes cluster
administration flows to accomplish these tasks, even though it will require
manual action from a Scipian admin. Namely, these resources will be created to
onboard a customer by a Scipian admin using `kubectl` and yaml. Using the 
primitives already built into Kubernetes allows us to stay unified with 
Kubernetes, build this solution quickly, and iterate to improve this onboarding 
process over time.

# Unresolved questions
[unresolved-questions]: #unresolved-questions

The following are open questions the Scipian dev community should answer before
work commences:

- Somewhat tied to this process is the question of how best to distribute the 
Scipian Authentication CLI to onboarding teams?
- What areas do we need to consider to align us for future iterations and
improvements to automate this process?

# Future possibilities
[future-possibilities]: #future-possibilities

As mentioned in this RFC, this is an MVP level solution to onboarding. This
process should be automated and include a self service UI in the future, as
the manual action requried by a Scipian admin will not scale. However, this MVP
should be done in a way where future iteration can begin at any time, but the
proposed implementation should support the current needs for the forseable 
future.
