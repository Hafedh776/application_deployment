# application_deployment
#Nous avons besoin d'héberger une application N-tiers classique.
#Cette dernière est constituée des images de containers suivantes :
#·Une partie front avec l'image my-registry.io/my-application/front:1.0
#·Une partie backend avec l'image my-registry.io/my-application/backend:1.0
#La base de données est hébergée à l'extérieur à l'adresse my-db-test.io. Il s'agit d'une base de données PostgreSQL. 
#Nous disposons d'un utilisateur myapplication avec comme mot de passe M3P@ssw0rd!
#L'exercice consiste à démarrer entièrement cette application à l'aide soit de Docker compose/swarm ou de Kubernetes 
#(à l'aide d'outils comme Kubectl ou Helm). Il faut que les informations d'accès à la base de données soient exposées dans 
#les variables d'environnements SPRING_POSTGRES_USERNAME, SPRING_POSTGRES_PASSWORD et SPRING_POSTGRES_URL
#
#Afin de réaliser l'exercice, il ne faut pas hésiter à remplacer le nom des images par des choses qui existent. 
#Merci d'aller au plus direct et de ne pas se compliquer la tâche : pas la peine par exemple de chercher à masquer les variables d'environnements.

# Appliquez les fichiers YAML
kubectl apply -f namespace.yaml
kubectl apply -f configmap.yaml
kubectl apply -f backend-deployment.yaml
kubectl apply -f frontend-deployment.yaml
kubectl apply -f ingress.yaml

kubectl get all -n my-application
kubectl describe ingress my-application-ingress -n my-application
