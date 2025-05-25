# 📦 initContainers

initContainers is a feature provided by K8s pods to run setup scripts before the actual containers start.

You can execute multiple initContainers in the same Pod, but keep in mind they will run one after another, **not** in parallel.

initContainers can have their own Docker images, so you can offload some configuration to them and keeping your main images as small as possible, increasing the security of your cluster.

Keep in mind that a pod will **not** be launched if one of the initContainers will stop. They are not to be seen as something optional or something that could fail.

### 🚀 Run the setup:

1. Create the pod:
```bash
kubectl apply -f initContainer.yml
```

2. Watch the logs:
```bash
kubectl get pods -w
```

3. See the logs for a specific container:
```bash
kubectl logs pods/nginx-with-init-container -c nginx-container
```

4. See all logs for all containers in a pod:
```bash
kubectl logs pods/nginx-with-init-container
```

5. See logs for past 2 hours in a certain container:
```bash
kubectl logs --since=2h pods/nginx-with-init-container -c nginx-container
```

6. See only the last 30 logs of a container:
```bash
kubectl logs --tail=30 pods/nginx-with-init-container -c nginx-container
```

🌎 There are many more ways to see logs, the command is pretty flexible. You can try for yourself.

### ❗️ Also, here is a useful resource I found on pod creation:
![Image](https://github.com/user-attachments/assets/4dbf61c4-892e-4187-8d44-208a0e216510)
