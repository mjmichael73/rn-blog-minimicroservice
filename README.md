

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