## Intro

How to install Minikube and get a simple guestbook app working w it

## Instructions

Run Container Transform on an ECS Task Definition

- `docker run --rm -v $(pwd):/data/ micahhausler/container-transform  --input-type ecs --output-type kubernetes Guestbook.Dockerrun.aws.json > guestbook-deployment.yaml`
- replace `name` and `app` fields with a identifier (in this case, I used `guestbook`)

Install and run [Minikube](https://github.com/kubernetes/minikube) locally

- `brew cask install minikube`
- `minikube start`
- `minikube dashboard`

Create deployment

- `kubectl create -f guestbook-deployment.yaml`

Create a service and expose the deployment

- `kubectl expose deployment guestbook --type=LoadBalancer`
- `kubectl get services`

View the service

- `minikube service guestbook`

## More Info

Based largely off of [Hello Minikube](https://kubernetes.io/docs/tutorials/stateless-application/hello-minikube/).
