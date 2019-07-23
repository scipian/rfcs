- Feature Name: `terraform_state_migration`
- Start Date: 2019-07-03
- RFC PR: [scipian/rfcs#0000](https://github.com/scipian/rfcs/pull/0000)
- Community Issue: [scipian/community#6](https://github.com/scipian/community/issues/6)

# Summary
[summary]: #summary

Migrating Terraform state from an on-boarding customer's AWS account to Scipian's
managed backend is an important feature for users who are currently using Stack.
This feature will allow them to seamlessly move over to the Scipian platform
in a way that does not disrupt their current infrastructure.

# Motivation
[motivation]: #motivation

There is currently no process for an on-boarding customer to migrate their
Terraform state to Scipian. Having a smooth self-service process is important
to encouraging users to use Scipian.

# Guide-level explanation
[guide-level-explanation]: #guide-level-explanation

After a new customer has been on-boarded, they will have the option to migrate
their existing Terraform state to Scipian's backend. The process is simple:

1. User will create a Kubernetes secret with their AWS credentials for the 
AWS acocunt they will be pulling their Terraform state from. As part of the
onboarding process, appropriate IAM rules will be set up allowing the 
on-boarding customer CRUD privileges from their account to a namespaced path 
in Scipian's S3 bucket backend.
2. User will then run a Kubernetes Job, based on a yaml template provided by
the Scipian team. This job will run a special Docker image which will pull
the Terraform state from the user's existing S3 bucket, and push it to Scipian's
S3 backend.

# Reference-level explanation
[reference-level-explanation]: #reference-level-explanation

- As mentioned above, the migrator is a special Docker image that is
run as a Kubernetes job. It will rely on certain ENV's to be avaiable, with
information about S3 bucket, Workspace name, Namespace, etc.
- The special Docker image is a Go app, that utilizes the AWS SDK to pull from
and push to S3 buckets.
- The on-boarding customer will supply the following as ENV's defined in the
Job yaml spec:
    - S3_BUCKET: the S3 bucket where the on-boarding customer's Terraform state
    resides
    - S3_KEY: the key to the above Terraform state
    - Namespace: the Namespace created in Scipian from the on-boarding customer
    - Workspace: the name of the Workspace of the on-boarding customer's
    Terraform
    - AWS_ACCESS_KEY_ID: the access key to the on-boarding customer's
    AWS account where the state will be pulled from
    - AWS_SECRET_ACCESS_KEY: secret access key to the above account

# Drawbacks
[drawbacks]: #drawbacks

No drawbacks have been identified with this feature.

# Rationale and alternatives
[rationale-and-alternatives]: #rationale-and-alternatives

This is an MVP level feature, allowing users to migrate state seamlessly if
needed. A simple alternative manually move state, but that becomes labor
intensive.

As this feature is iterated on, it would likely become part of the self-service
customer onboarding, which likely would include a UI. Some of this would then
be abstracted away from the on-boarding customer. The internals will likely
stay the same (i.e. a kubernetes job running a special Docker image to migrate
state), however an onboarding customer wouldn't need to kick this off manually.

# Prior art
[prior-art]: #prior-art

Terraform Enterprise offers some level of state migration, however the current
use case for Scipian does not support Terraform Enterprise, and is therefore
outside of the scope of this RFC.

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
