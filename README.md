GitOps Project Overview:

The project involves creating a simple application running an Nginx web server.
Two environments are used: preprod and prod.
Preprod environment uses a Hostpath type PV with "Welcome to preproduction" data.
Prod environment uses a Hostpath type PV with "Welcome to production" data.

GitOps Procedure:

Create Git repositories for each environment.
PersistentVolumes (PV) need to be created beforehand by the storage administrator.
Each environment requires:
Deployment running the Nginx application.
PersistentVolumeClaim (PVC) connecting to environment storage.
NodePort service for deployment access.
Ingress resource for service access by name.


GitOps Operator Tasks:

Create or update resources if files are updated in the Git repository.
Test preproduction application to ensure it provides the correct webpage.
If tests pass, copy preprod YAML files to the prod Git repository, replacing "preprod" with "prod".
Commit changes to the Git repository.
Deploy files using kubectl apply for the CD procedure.
Use Blue/Green or Canary migration for exposing the application.

