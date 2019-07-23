- Feature Name: kubectl_via_scipian
- Start Date: 2019-07-01
- RFC PR: [scipian/rfcs#0000](https://github.com/scipian/rfcs/pull/0000)
- Community Issue: [scipian/community#0000](https://github.com/scipian/community/issues/0000)

# Summary
[summary]: #summary

Enable cluster observability for scipian users.

# Motivation
[motivation]: #motivation

Enable control plane access to a scipian created resource via scipian tools to provide an additional level of authentication and security to changing a scipian managed application.

# Guide-level explanation
[guide-level-explanation]: #guide-level-explanation

To interact with your scipian created cluster simply provide scipian the cluster identifier and desired command.

`scipian <scipian_env_id> get <resource>`
`scipian <scipian_env_id> describe <resource>`
`scipian <scipian_env_id> logs <resource>`

If Scipian is unable to find the environment referenced or authenticate your credentials an error will be returned. 

```
- Invalid environment referenced.
- Invalid authentication for provided environment.
```

Otherwise the success or failure message returned will come directly from the cluster.

# Reference-level explanation
[reference-level-explanation]: #reference-level-explanation

When a cluster is created through scipian it stores the configuration needed to access the cluster.

This feature request will allow a user to interact with the his/her scipian created cluster. When a developer interacts with scipian an environment id will be referenced. Scipian then loads the config associated with that id and proceeds with applying the developer provided command.

# Drawbacks
[drawbacks]: #drawbacks

No immediate drawbacks of adding this feature have been identified.

# Rationale and alternatives
[rationale-and-alternatives]: #rationale-and-alternatives

# Prior art
[prior-art]: #prior-art

Kubernetes Cluster Federation (KubeFed for short) allows you to coordinate the configuration of multiple Kubernetes clusters from a single set of APIs in a hosting cluster. KubeFed aims to provide mechanisms for expressing which clusters should have their configuration managed and what that configuration should be. The mechanisms that KubeFed provides are intentionally low-level, and intended to be foundational for more complex multicluster use cases such as deploying multi-geo applications and disaster recovery.

# Unresolved questions
[unresolved-questions]: #unresolved-questions

- Should we use a push model instead? (e.g. Push logs to a scipian dashboard)
- How should an individual user provide scipian credentials?
- How should does scipian determine whether a user can manage a cluster?

# Future possibilities
[future-possibilities]: #future-possibilities

In the future extending the functionality of managing clusters with tool sets such as Helm could be desirable.
Features like history and rollback would be fantastic. Eventually even the ability to trigger a chain of deployments on a sequential series of environments given the success of each would be optimal.