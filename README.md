# MongoDB and Mongo Express Deployment on Kubernetes Cluster

This README provides an overview of the YAML files used to deploy and configure a MongoDB database and a Mongo Express web interface on a Kubernetes cluster. The YAML files include:

   - mongo_configmap.yml
   - mongo_deploy.yml
   - mongo_express_deploy.yaml
   - mongo_secret.yml

![diagram](https://github.com/tunckasik/MongoDB-MongoExpress-Kubernetes/blob/main/app-diagram-mongodb-k8s.png)

The deployment is designed to run on a Kubernetes cluster using **'kubectl'**.

## Prerequisites
Before deploying these YAML files, you must have the following:

  - A Kubernetes cluster
  - kubectl CLI installed
  - A working knowledge of Kubernetes concepts such as Deployments, Services, ConfigMaps, and Secrets
  - Access to the YAML files in this repository
  
> Note: You can also provision AKS/EKS on Azure or AWS cloud account, and you can use their CLIs.

## Deployment

1. To deploy the MongoDB and Mongo Express resources, follow these steps:

1. Clone the repository containing the YAML files to your local machine.

1. Open a terminal window and navigate to the directory containing the YAML files.

1. First you must run the following command to create the ConfigMap:

    ```
    kubectl apply -f mongo_configmap.yml
    ```

     This ConfigMap is used to store the configuration data for the MongoDB database.

1. Run the following command to create the Secret:

    ```
    kubectl apply -f mongo_secret.yml
    ```

     This Secret is used to store the MongoDB database credentials.

1. Run the following command to create the MongoDB Deployment:

    ```
    kubectl apply -f mongo_deploy.yml
    ```

    This Deployment creates the MongoDB database and makes it available to other resources in the Kubernetes cluster.

1. Run the following command to create the Mongo Express Deployment:

    ```
    kubectl apply -f mongo_express_deploy.yaml
    ```
    This Deployment creates a web interface for the MongoDB database, allowing you to view and manage its data.

## Accessing the Mongo Express Web Interface
To access the Mongo Express web interface, follow these steps:

1. Get the IP address of the Mongo Express Service by running the following command:

    ```
    kubectl get services mongo-express
    ```

1. Open a web browser and navigate to the IP address obtained in step 1, followed by port 8081. For example:

    ```
    http://<IP_ADDRESS>:8081/
    ```
1. You should see the Mongo Express and you now be logged in to the Mongo Express web interface and able to view and manage the data in the MongoDB database.

  ![screenshot](https://github.com/tunckasik/MongoDB-MongoExpress-Kubernetes/blob/main/Deployment_SS.png)
