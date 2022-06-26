

How to create posts container:

    cd to posts directory
    run this command: docker build -t mojimich2015/posts:0.0.1 .

How to run only posts pod:

    cd to infra\k8s\
    run this command: kubectl apply -f posts.yml

How to see if posts pod is created and running:

    cd to infra\k8s
    run this command: kubectl get pods

Some useful commands for working with pods:

    docker ps => kubectl get pods
    docker exec -it [container id] [cmd] => kubectl exec -it [pod_name] [cmd]
    kubectl logs [pod_name]
    kubectl delete pod [pod_name]
    kubectl apply -f [config file name]
    kubectl describe pod [pod_name]

Some useful commands for working with deployments:

    kubectl get deployments
    kubectl describe deployment [depl name]
    kubectl apply -f [config file name]
    kubetl delete deployment [depl name]

Method 1 Deployment:

    Change the version inside the depl file
    then kubectl apply

Method 2 Deployment:
    
    Use latest tag for image of deployment
    Build image
    Push to container repository
    kubectl rollout restart deployment [depl_name]

Networking and services in kubernetes:

    Create yaml file for NodePort type service
    kubectl apply -f posts-serv.yaml
    kubectl get services
    kubectl describe service [service yaml file name] 
    Get the ip of cluster using "minikube ip"
    Or for localhost just use: localhost:nodePort/posts

Apply all Kubernetes files all at once inside a directory:

    kubectl apply -f .

Load balancer stuff (ingress-nginx):

    kubectl apply -f https://raw.githubusercontent.com/kubernetes/ingress-nginx/controller-v1.2.0/deploy/static/provider/cloud/deploy.yaml
    https://kubernetes.github.io/ingress-nginx/deploy/#docker-desktop
    https://kubernetes.github.io/ingress-nginx/deploy/#quick-start
    When applying ingress-srv you may get error, use this link: https://programmerah.com/solved-kubernetes-ingress-srv-error-failed-calling-webhook-validate-nginx-ingress-kubernetes-io-51118/
    kubectl get pods --namespace=ingress-nginx
    kubectl delete namespace ingress-nginx

### For Dev Puposes

    It was added skaffold from https://skaffold.dev
    to ease changes on local development
    It has been added skaffold.yaml file 
    The only thing to start project is running this command: "skaffold dev" inside your root project dir
    - If you get some errors the first time that you run skaffold dev, Just CTRL + C and then run the skaffold dev again
    
