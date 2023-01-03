# springboot-mysql-kubernetes
Step1: Start the minikube by using following command
      > minikube start
Step2: In order to sync both minikube and docker we can use the below command
  > eval $(minikube docker-env)

Step3: Create Spring Boot project and add the db-deployment.yaml file
 Inside the db-deployment.yaml file we need to configure the 
    kind : PersistentVolumeClaim
    kind : Deployment
    kind : Service
  - Here type : None

Step4: In order to execute the db-deployment.yaml file we use the below command
   > kubectl apply -f db-deployment.yaml
     This command will create PersistentVolumentClaim , Deployment, Service objects

Step5:   Use the below commands to cross check the status of objects

    > kubectl get deployements
    > kubectl get pods
    > kubeclt get services
 we can also chekc the logs by using command : kubectl logs object


Step6: In order to execute the mysql image we use the below command
   >kubectl exec -t mysql-34343-gmfcr /bin/bash
  # mysql -h mysql -u root -p


Step7: Now create the image for spring boot application
>docker build -it springboot-crud-k8s:1.0 .

Step8: Create the app-deployment.yaml file
   Inside the app-deployment.yaml file we need to configure the 
          kind : Deployment
          kind : Service

  - Here type: NodePort


Step9: Now execute the app-deployement.yaml file
 > kubectl apply -f app-deployement.yaml
 > kubectl get deployements
 > kubectl get pods
 > kubectl get svc
 > kubectl logs springboot-crud
 > minikube ip

step10: Now open the browser and test it.

step11: We can also open the dashboard
 >minikube dashboard


