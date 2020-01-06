# cookiecutter-kubernetes-deployment

A deployment template for creating kubernetes deployment with CPU based autoscaling.

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

The above mentioned steps can deploy any containerized flask app with Autoscaling enabled by default. The default values deploy an IMDB clone written with flask backend
