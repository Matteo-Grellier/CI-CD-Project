# Projet : CI-CD

## Lancer le projet
Pour lancer le projet il faut d'abord créer un cluster minikube :
`minikube start -p ci-cd`

Il suffit de lancer la commande suivante sur tout les fichiers de ce repository [repository](https://github.com/Matteo-Grellier/microapp-deploy) :
`kubectl apply -f "le fichier"`.

Il faut aussi lancer argo-cd en suivant ce [tutoriel](https://argo-cd.readthedocs.io/en/stable/getting_started/).
![image](https://github.com/Matteo-Grellier/CI-CD-Project/assets/46086160/0584cc63-a1f6-4606-a646-8f63587e527b)

Les services devraient être lancer. Pour y accéder il faut faire cette série de commandes :
- Tout d'abord récupérer les pods sur lesquelles ils sont lancés et ensuite faire:
- `kubectl port-forward <order-service-pod> 3002:3002`
- `kubectl port-forward <front-end-service> 3000:3000`

En allant ensuite sur `http://localhost:3000` on peut voir que l'on accède au front et si l'on clique sur get orders, le message "Hello depuis le service Order" apparait bien ce qui signifie que le service front et order communiques.

## Github action
A noter qu'il y a un github action qui build et déploie une nouvelle image des services sur docker-hub à chaque push sur une branche de version. Une version latest est mis à jour ainsi qu'un tag est ajouter avec la nouvel version de l'image.
![image](https://github.com/Matteo-Grellier/CI-CD-Project/assets/46086160/82df189d-400c-49ba-9567-a7fd16865f29)

## Les problèmes restants
De cette manière les services front et order communique mais pas le service user. J'ai commencé à mettre en place un service Ingress mais je n'ai pas réussi à l'intégrer.
