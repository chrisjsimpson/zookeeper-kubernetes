
## Locally

If you run on a single node (e.g. locally; **don't** do this in production) with replicas > 1 then your deployment will fail. Why? Because your zookeeper pods won't be able to bind to their listen port (2181) because it'll already be in use. 

To fudge this locally, you may use `zookeeper-no-anti-afinity-no-fault-tolerance.yaml` which turns of affinity rules and reduces replicas down to 1.

Do not use in production. Provides no fault tolerance:
```
  kubectl apply -f zookeeper-no-anti-afinity-no-fault-tolerance.yaml
```

Based on src: https://github.com/kubernetes/contrib/tree/master/statefulsets/zookeeper 
