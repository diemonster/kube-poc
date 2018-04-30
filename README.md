## Intro

Instructions on installing Minikube and getting a simple guestbook app working w it

## Prereqs

Run Container Transform on an ECS Task Definition

- `docker run --rm -v $(pwd):/data/ micahhausler/container-transform  --input-type ecs --output-type kubernetes Guestbook.Dockerrun.aws.json > guestbook-deployment.yaml`

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
