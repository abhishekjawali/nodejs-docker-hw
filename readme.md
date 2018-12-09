**NodeJS Hello World application with Docker and Kubernetes**

# Building and running Docker image

## Create the docker image
Excute the below command from the root directory to create the docker image.

```
$ docker build -t abhishekjv/nodejs-hw .
```
Note: With ``` -t ``` tag, I have specified the name of the image which also contains the name of my Docker hub ID. This is one of the best practice to follow when tagging images. 

## Run the image to verify its working
To run the application, execute the below command:
```
docker run -p 3000:3000 IMAGE-ID
```

## Push the image to docker hub
```
docker push abhishekjv/nodejs-hw
```

## Create a pod in Kubernetes
```
kubectl create -f pod-nodejs-docker-hw.yml
```

## To access the application on K8s
```
kubectl port-forward nodejs-docker-hw 8081:3000

curl http://localhost:8081
```

## To access the application on K8s via service
```
kubectl expose pod nodejs-docker-hw --type=NodePort --name nodejs-hw-service
kubectl describe service nodejs-hw-service
```
Look for the port number defined for NodePort.
