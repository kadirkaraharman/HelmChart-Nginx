## Nginx Helm CHart, HPA for Nginx, Load Pod

### This repository contains nginx deployment, hpa for nginx deployment and load pods for overload the nginx and try out the hpa.

If you are using minikube you should enable metric addons for hpa otherwise hpa can't get cpu or mem metrics from pods.

### Pre Requirements

**k8s cluster or minikube**

**Helm installed**

**Metric addons enable if you are using the minikube**
```
minikube addons enable metrics-server
```

### Installation
* **Clone the repository**
* **Configure the values.yaml**
* **Go into values directory**
* **Deploy with helm**
```
helm install {{name-for-deployment}} {{values.yaml location}}
helm install nginx .
```

### U can check the hpa, in my case it will take a 1-2 minute to hpa reach the metric on nginx, im using minikube.

Check the hpa
```
kubectl get hpa 
```

Check the pods 
```
kubectl get pods
```

You can check the load pods, if they working right or what happens, you should see the welcome to nginx html template over and over
```
kubectl logs -n default load-generator
```

## TroubleShooting
* **If load pods can't reach the nginx configure service**
* **Make sure service name is nginx and namesapce is default**
* **You can check the hpa logs, i figured the hpa needs metric addons for minikube**

### Thats it. HPA Configured Nginx Deployment With Helm Chart. ;) 