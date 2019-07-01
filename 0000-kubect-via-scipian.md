- Feature Name: kubectl_via_scipian
- Start Date: 2019-07-01
- RFC PR: [scipian/rfcs#0000](https://github.com/scipian/rfcs/pull/0000)
- Community Issue: [scipian/community#0000](https://github.com/scipian/community/issues/0000)

# Summary
[summary]: #summary

Enable users to interact with their kubernetes clusters via Scipian. Commands desired are:

```
- kubectl create -f .
- kubectl apply -f .
- kubectl get <resource>
- kubectl describe <resource> 
- kubectl logs <resource>
- kubectl scale --replicas=<num> <resource>
```

# Motivation
[motivation]: #motivation

Enable kubectl access to a scipian created cluster via scipian tools to provide an additional level of authentication and security to changing a scipian managed kubernetes application.

# Guide-level explanation
[guide-level-explanation]: #guide-level-explanation

To use kubectl on your scipian created cluster simply provide scipian the cluster identifier and kubectl command.

`scipian <scipian_env_id> kubectl <command to interact with cluster>`

If Scipian is unable to authenticate your credentials or find the environment referenced an error will be returned. 

```
- Invalid environment referenced.
- Invalid authentication for provided environment.
```

Otherwise the success or failure message will come directly from the kubectl command provided.

# Reference-level explanation
[reference-level-explanation]: #reference-level-explanation

When a kubernetes cluster is created through scipian it stores the kubeconfig needed to access the cluster.

New tooling will allow a user to indicate which environment he/she would like to work with and the config is then sourced to support applying the command the developer wishes.

# Drawbacks
[drawbacks]: #drawbacks

No immediate drawbacks of adding this feature have been identified.

# Rationale and alternatives
[rationale-and-alternatives]: #rationale-and-alternatives

One alternative is bundling the kubernetes manifests in a zip and providing the bundle to scipian to initiate cluster changes.
However, providing direct access to the kubectl control plane provides additional visibility and the ability to make smaller changes (eg scaling replicas) without applying entire manifests again.

# Prior art
[prior-art]: #prior-art

(( Unsure if any other pipeline delivery tools provide access to toolsets via their controls. ))

# Unresolved questions
[unresolved-questions]: #unresolved-questions

- Are there better ways to enable cody deploy and visibility into resources?
- Should we simply be using scipian tools to ssh into a box and use kubectl commands from there? (Would that satisfy most no touch requirements?)

# Future possibilities
[future-possibilities]: #future-possibilities

In the future extending the functionality of managing kubernetes applications with tool sets such as Helm could be desirable.
Features like history and rollback would be fantastic. Eventually even the ability to trigger a chain of deployments on a sequential series of environments given the sucess of each would be optimal.