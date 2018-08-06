# Docker

wikipédia : Docker est un outil qui permet d'empaqueter une application et ses dépendances dans un conteneur virtuel, qui pourra être exécuté sur n'importe quel serveur linux.

Un conteneur est une boite qui à la manière d'une machine virtuelle va contenir une application (code source / dépendances / librairies / assets / etc) et qui sera complètement isolée du système d'exploitation. Ce qui lui donne l'avantage de pouvoir être executée sur n'importe quel système.

l'avantage de ce système de conteneurs est qu'il permet aux développeurs d'applications à fournir à l'administrateur système, l'application et toutes ses dépendances afin de lui éviter d'avoir à tout installer sur son serveur pour faire fonctionner l'application.

La différence entre un conteneur et une machine virtuelle est que le conteneur sera beaucoup moins lourd qu'une machine virtuelle et pourra donc plus facilement être envoyée sur un serveur.


###### Comment ça marche ?

* Docker Deamon : Tourne en tâche de fond sur un serveur et permet de faire fonctionner les conteneurs

* Docker Client : Système de commandes permettant d'interagir avec le Deamon et de gérer les conteneurs (lancer, stopper, supprimer etc)

* Boot2Docker : permet de faire fonctionner docker sur tous les systèmes


######

```
$ docker run <packageName>
```
Télécharge une image du paquet voulu
