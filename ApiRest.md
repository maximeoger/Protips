# Qu'est ce qu'une API

##### Definition

Le terme 'API' est un acronyme signifiant 'Application Programming Interface'. Ce therme générique désigne une façon de lancer des requêtes structurées pour recevoir des réponses structurées.

'REST' est un acronyme pour 'Representational State Transfer' il désigne un type d'architecture pour structurer une API.

Le rôle de REST dans une API :

* assurer la création d'un lien client / serveur (le plus souvent via le protocole HTTP)

* Traiter les objets comme des ressources pouvant être créées, modifiées ou détruites

REST peut être utilisé par n'importe quel langage de programmation.

Pour simplifier, on peut dire que l'API est un messager et REST permet d'utiliser le protocole HTTP.

##### RESTful

On dit qu'une API est RESTful si elle répond bien a toutes les contraintes imposées par REST c'est à dire la possibilité de faire des requêtes de type GET, POST, PUT, DELETE.

Une autre particularité de l'architecture REST est que la partie client et la partie serveur communiquent sans que la partie client ne connaisse la structure et le contenu des ressources stockées sur le serveur. La seule chose que les deux parties (client/serveur) connaissent c'est le média utilisé pour communiquer (JSON, XML etc.. ).

verbes HTTP les plus utilisés :

* `GET` : renvoie les données d'une certaines ressource (dans le corps de la réponse)
* `POST` : envoie des données depuis le client vers le serveur pour créer une ressource
* `PUT` : modifie les données d'une ressource existante
* `DELETE` : supprime une ressource existante

autres verbes HTTP :

* `HEAD` : renvoie les information de l'entête de la réponse HTTP lors de la requête (comme pour GET, mais sans le corps de réponse)
* `OPTIONS` : Renvoie les méthodes HTTP supportées par le serveur
* `PATCH` : Applique des changements vers une ressource partielle


##### Endpoints

Un 'Endpoint' est une URL représentant la requête HTTP.

exemples de requêtes dans l'api Json: placeholder

`GET 'https://jsonplaceholder.typicode.com/users' `
renvoie la liste des utilisateurs au format JSON

`GET 'https://jsonplaceholder.typicode.com/users/1' `
renvoie les données de l'utilisateur enregistré sur le serveur avec l'id=1

`POST 'https://jsonplaceholder.typicode.com/posts/?userId=1&name=johnDoe'`
créé une nouvelle ressource avec les valeurs en paramètre de la requête.
