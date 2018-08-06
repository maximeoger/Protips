# Protips

dernière mise à jour : 20/06/2018

# css :art:


### Convention BEM

* B -> Block
* E -> Element
* M -> Modifier

```html
<!-- mainList = Block -->
<ul class="mainList mainList--xmas">
    <!-- __item = Element -->       
    <li class="mainList__item">
        <!-- __itemLink = Element -->   
        <a class="mainList__itemLink" href = "/home">Home</a>
    </li>
    <!-- __item = Element -->       
    <li class="mainList__item">
        <!-- __itemLink = Element -->   
        <a class="mainList__itemLink mainList__itemLink--isActive" href = "/about">About</a>
    </li>
    <!-- __item = Element -->       
    <li class="mainList__item">
        <!-- __itemLink = Element -->   
        <a class="mainList__itemLink" href = "/works">Works</a>
    </li>
</ul>
```

*en scss*
```css
.mainList {
  display: flex;
  justify-content: space-between;

  &--xmas{
    background: green;
  }
  &__item {
    list-style: none;
  }
  &__itemLink {
    color: red;

    &--isActive{
      color: white;
    }
  }
}
```


*en css*
```css
.mainList {

}
.mainList--xmas {

}
.mainList__itemLink {

}
.mainList__itemLink--isActive {

}
```
### Pseudos attributs

Les pseudos attributs `::before` et `::after` permettent de créer des neuds HTML et CSS.
Ils sont éssentiellements utilisés pour ajouter des ornements, des décorations ... On
peut bien entendu faire des animations avec, les positionner par rapport à leur parent (relative / absolute).
** Ils doivent obligatoirement avoir un `content: '';`**

### Centrer en 3 lignes de CSS (verticalement)

``` HTML
<section class="cover">
  <h1 class="mainTitle">Présentation des pseudo-attributs</h1>
</section>
```
```CSS
.cover {
  background: #FDFDFD;
  padding: 20px;

  &__mainTitle{
    text-align: center;
    font-size: 24px;
    color: green;
    position: relative;

    &::before,
    &::after {
      content: '';
      width: 50px;
      height: 50px;
      display: block;
      background: red;
      top: 0;
    }
    &::before {
      left: 0;
    }
    &::after {
      right: 0;
    }
  }
}
```
### REM, EM, %, VW Sizing

#### %

#### EM

* Le EM est relatif à sont parent direct et non pas à sa racine comme le REM.

```css
.cover {
  font-size: 100%;

  &__mainTitle {

    /* 1em = 16px / .8em != 16px */
    font-size: .8em;
  }
}
```

#### REM

* Le REM est basé sur la taille de la racine (soit la balise html) qui par défaut à une valeur de 16px. Afin d'éviter tout calcul, il est nécessaire de l'écraser en donnant une base de 10px soit 62.5px.
* Le REM est intéressant à utiliser si les Media-Queries employées sont en rem également. Cela vous permettra de garder des proportions égales lorsqu'on va redimensionner la page.
* Ses proportions seront également gardées quand l'utilisateur zoomera dans votre page.

```css

  html{
    /* 62.5% === 10px */
    font-size: 62.5%;
  }
  .mainTitle{
    /* 1.6 rem === 16px */
    font-size: 1.6rem;
    /* 32rem === 320px */
    width: 32rem;
  }

```

### VW(idth) / VH(eight)

* Unités relatives à la taille de votre écran (peu importe le device)
* Attention au VH et à son contenu. 100vh === 100vh quoi qu'il arrive.
* VW : très utile pour les interfaces fluides.

## Npm

Npm sert à gérer des dépendances dans un projet

ex: Pour installer Gulp de manière globale : `npm install -g gulp`
Pour initialiser Gulp sur son dossier de projet :
* `npm init`
* `npm install gulp --save-dev`

# JavaScript

###### this

`this` est un mot clé servant à identifier la relation avec la fonction qui l'a défini au départ. Sa valeur est déterminée à partir de la fonction qui l'appelle.





### ES2015

###### fonctions fléchées
En plus d'offir une synthaxe plus simple, elles ne prennent pas leurs valeurs pour `this`, `arguments`, `super` ou `new.target` donc plutôt pas mal pour définir des fonctions simples. Il ne faut pas l'utiliser pour définir des méthodes de classes.

```javaScript
let animals = ['chien', 'chat', 'girafe', 'zebre'];

// dans une variable
let faisUnTruc = () => {
  console.log('truc');
}

// fonction fléchée anonyme
animals.forEach( animal => console.log(animal) );

```

###### programmation orientée objet en JavaScript

* mots clés

### React

React est basée sur le concept de la programmation orientée objet avec javaScript. l'application sera organisée en composants indépendants les uns des autres (dans la plupart des cas) ce qui permet une meilleure maintenabilité du code. Chaque composant sera défini dans une `class` qui hérite des propriétés de la classe `React.Component`. Par convention, on va chercher à séparer nos composants dans des fichiers distincts. Afin que la classe puisse hériter des propritétés de `React.Component` il faut importer React via une règle d'importation :

```javascript
import React from "react";
```

###### Structure du fichier


###### props

Les props agissent comme des "attributs" pour les composants react
* ex : pour un composant ` <header tagline /> ` la props est le mot clé `tagline`
* pour voir les props d'un composant, aller dans l'onglet React de chrome (requier React dev tools)
* une props doit être passée avec des accolades `{props}`
* Les props doivent rester en lecture seule : lorsque l'on déclare une fonction ou une classe, celle çi ne doit jamais modifier ses propres props (on les appelles les fonctions "pures" cad qu'elles retournent les mêmes valeurs en sorties qu'en entrée) un composant réact doit agir comme une fonction pure

###### Composants

Pour créer un composant, il faut créer une classe qui prends le nom du composant voulu, par convention, on nomme les classes avec la première lettre en majuscule.

```javascript
import React from "react";

class Header extends React.Component {
  render(){
    return(
        <header className="top">
          <h1>
            catch
            <span className="ofhe">
              <span className="of">of</span>
              <span className="the">the</span>
            </span>
            day
          </h1>
          <h3 className="tagline">
            <span>{this.props.tagline}</span>
          </h3>
        </header>
    )
  }
}

export default Header;
```

### PHP

##### Programmation Orientée Objet

###### les classes

une classe est une définition d'un concept un peut comme un moule qui va contenir des attributs et des méthodes

```PHP
class Person
{
  private $name;
  private $weight;

  function __construct(string $name)
  {
    this->name = $name;
  }

  function setWeight(int $weight)
  {
    this->weight = $weight;
  }

  function getWeight()
  {
    return this->weight;
  }
}

$toto = new Person("toto");
toto->setWeight("78");
// -> 78

```
###### méthodes magiques

* `__toString()` transforme une donné en string



## liens utiles :

* [doc symfony](https://symfony.com/doc/current/index.html)
* [caniuse](http://caniuse.com)
* [frontend developer job interview questions](https://github.com/h5bp/Front-end-Developer-Interview-Questions)
* [css next](http://cssnext.io/)
