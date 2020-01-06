# cookiecutter-kubernetes-deployment

A cookiecutter template for creating kubernetes deployment with CPU based autoscaling. 
Default values deploy a simple flask based IMDB clone. 

## How to Run

```bash
$ pip3 install cookiecutter --user
$ cookiecutter https://github.com/arjun921/cookiecutter-kubernetes-deployment.git
release_name [fmdb]: my-release-name
release_version [1.0.0]:
release_namespace [default]:
docker_image [arjun921/fmdb:latest]:
container_port [5000]:
expose_endpoint [example.com]: mycustomdomain.com
expose_path [/]:
expose_port [80]:
min_replicas [1]:
max_replicas [5]:
max_cpu_percentage [70]:
max_cpu [1024m]:
max_memory [512Mi]:
min_cpu [100m]:
min_memory [128Mi]:
$ kubectl cluster-info # ensure you are connected to your kubernetes cluster
$ kubectl apply -f my-release-name/
```

The above mentioned steps can deploy any containerized flask app with Autoscaling enabled.

### Parameters

The default paramters deploy an IMDB clone written with a flask backend.

- `release_name` - What the deployment should be named?
- `release_version` - Deployment app version
- `release_namespace` - Kubernetes Namespace for deployment
- `docker_image` - Docker image to deploy with tag
- `container_port` - The port at which your container exposes the service
- `expose_endpoint` - `domainname.com`
- `expose_path` - Path to the app. Could be something like `/v1/api/open/` or default `/`
- `expose_port` - Which port to expose the endpoint at. Will correspond to `mydomain.com:20415`
- `min_replicas` - Minimum number of pods to deploy. **Should be more than 1 for the service to be up**
- `max_replicas` - Maximum number of pods that the autoscaler can spin up
- `max_cpu_percentage` - CPU Percentage in Integer, Min: 0 - Max: 100. The HPA kicks in if CPU utilization crosses the threshold. 
- `max_cpu` - Maximum allowed CPU in Millicores a pod is allowed to consume
- `max_memory` - Maximum allowed Memory in megabytes a pod is allowed to consume
- `min_cpu` - Minimum CPU in Millicores required by the pod without which the pod will not run
- `min_memory` - Minimum Memory in megabytes required by the pod

