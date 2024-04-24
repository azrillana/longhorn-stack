# Setup Longhorn on Kubernetes with Kubectl

Prerequisite : 

Before deploy longhorn to kubernetes, must ensure that **open-iscsi** & **nfsv4 client** has been installed on each worker node

To install longhorn on kubernetes, follow these steps:

1. Change this parameter and adjust to your nodes count on longhorn/deploy.yaml file:
    ```
    parameters:
      numberOfReplicas: "2"
    ```

2. Deploy longhorn with kubectl:
    ```
    kubectl apply -f longhorn/deploy.yaml
    ```

# Test with basic nginx application

1. Create a persistent volume claim for the application:
    ```
    kubectl apply -f test-app/pvc.yaml
    ```
    *Note : Make sure the **storageClassName** to **longhorn***

2. Deploy the basic nginx application:
    ```
    kubectl apply -f test-app/deploy.yaml
    ```