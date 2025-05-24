# initContainers

initContainers is a feature provided by K8s pods to run setup scripts before the actual containers start

You can execute multiple initContainers in the same Pod, but keep in mind they will run one after another, **not** in parallel.

initContainers can have their own Docker images, so you can offload some configuration to them and keeping your main images as small as possible, increasing the security of your cluster.

Keep in mind that a pod will **not** be launched if one of the initContainers will stop. They are not to be seen as something optional or something that could fail.
