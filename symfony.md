# Symfony

symfony possède deux controlleurs frontaux : __/web/app.php__ pour les visiteurs de l'application (environement de production) et __/web/app_dev.php__ (environement de developpement) pour les développeurs. Symfony prends en compte le DX (Developer Experience) au même titre que l'UX


###### structure du projet :

* __/app__ : contient tout ce qui compose l'application sauf le code source
* __/bin__ : contient les commandes nécessaires au développement de l'application
* __/src__ : contient le code source de l'application
* __/tests__ : contient les tests unitaires nécessaires a certaines fonctionnalités
* __/var__ : contient une trace de ce que va écrire symfony (logs, cache, etc)
* __/vendor__ : contient les dépendances installées via composer (Twig, Doctrine, etc)
* __/web__ : contient les fichiers publiques (assets/images, css, js etc)

###### termes techniques :

* __Route__ : configuration qui définie l'url d'une page  
* __Controller__ : fonction ou methode qui génère le contenu d'une page

###### Créer un projet symfony

```
$ composer create-project symfony/website-skeleton [project-name]
```
commande composer pour utiliser la commande `bin/console` dans symfony

```
$ composer require server
```

Créer une entité : possibilité de remplacer bin/console par un alias.
une entité peut etre une table. Si la table existe déjà, on peut modifier et rajouter des colones

```
$ bin/console make:entity
```

Créer une migration  ( si erreur, modifier vendor/.env )

```
$ bin/console make:migration
```

Créer la base de données

```
$ bin/console doctrine:database:create
```

Update le schema

```
$ bin/console doctrine:schema:update --force
```
executer la migration

```
$ bin/console doctrine:migration:migrate
```

lancer un serveur

```
$ bin/console server:run
```

créer un crud

```
$ bin/console make:crud [nom-table-à-traiter]
```


créer les fonctionnalités admin

```
$ composer req admin
```

##### paramètres de routes

chaque route peut contenir un paramètre qui sera transformé en argument pour le controlleur :

```yml
# src/OC/PlatformBundle/Resources/config/routing.yml

oc_platform_view:
    path:      /advert/{id}
    defaults:
        _controller: OCPlatformBundle:Advert:view
    requirements:
        id: \d+
```

ici le paramètre {id} de la route '/advert/{id}' sera transormé en argument '$id' dans le controller AdvertController :

##### paramètres hors routes

En plus des paramètres de routes, on peut récupérer des paramètres "à l'ancienne" ( définis à la main ) via l'objet Request.

```php
use Symfony\Component\HttpFoundation\Request;

public function viewAction($id, Request $request)
    {
        // On récupère notre paramètre 'tag' correspondant au nom du paramètre appellé dans l'url
        $tag = $request->query->get('tag');
        return New Response( "Affichage de l'annonce : " . $id. " avec le tag : ". $tag);
    }

```

##### Le controller


* Doit Obligatoirement retourner un objet `Response`.
* Construit cette réponse avec les données qu'il reçoit en entrée : Paramètres de route et l'objet `Request`
* Se sert de tout ce dont il a besoin pour construire la réponse : la base de données, les vues, les différents services, etc.


#### twig

* ` { instruction } ` affiche une donnée
* ` {% instruction %} ` bloc d'instruction contenant du code
* ` {# truc #} ` bloc de commentaire
* ` {{ pseudo|upper }}` affiche la variable pseudo avec un filtre upper (uppercase)
* `{{ news.texte|striptags|title }}` affiche la variable news encombinant les filtres striptags et title (enlève les balises html et met les premières lettres en majuscule)
* `{{ nom ~ " " ~ prenom }}` concaténer un nom et un prénom
* `Date : {{ date|date('d/m/Y') }}` utiliser un filtre avec des arguments



[Documentation officielle ](https://twig.symfony.com/doc/2.x/filters/index.html)

#### Les relations :

* __ManyToOne__
* __OneToMany__
* __ManyToMany__
* __OneToOne__
