# Create files needed for rest of example.
echo -n 'admin' > ./username.txt
echo -n '1f2d1e2e67df' > ./password.txt

kubectl create secret generic db-user-pass --from-file=./username.txt --from-file=./password.txt

You can check that the secret was created like this:

kubectl get secrets

kubectl describe secrets/db-user-pass


Define container environment variables using Secret data

Define a container environment variable with data from a single Secret
Define an environment variable as a key-value pair in a Secret:
   kubectl create secret generic backend-user --from-literal=backend-username='backend-admin'
Assign the backend-username value defined in the Secret to the SECRET_USERNAME environment variable in the Pod specification.

kubectl create -f pod-single-secret-env-variable.yaml


Define container environment variables with data from multiple Secrets
As with the previous example, create the Secrets first.
     kubectl create secret generic backend-user --from-literal=backend-username='backend-admin' 
  
	 kubectl create secret generic db-user --from-literal=db-username='db-admin' 

kubectl create -f pod-multiple-secret-env-variable.yaml 


Configure all key-value pairs in a Secret as container environment variables
Note: This functionality is available in Kubernetes v1.6 and later.
Create a Secret containing multiple key-value pairs
   kubectl create secret generic test-secret --from-literal=username='my-app' --from-literal=password='39528$vdg7Jb'
Use envFrom to define all of the Secret’s data as container environment variables. The key from the Secret becomes the environment variable name in the Pod.

kubectl create -f pod-secret-envFrom.yaml
