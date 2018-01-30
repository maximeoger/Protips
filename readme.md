# Documentation

## Convention BEM

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
## Pseudos attributs

Les pseudos attributs `::before` et `::after` permettent de créer des neuds HTML et CSS.
Ils sont éssentiellements utilisés pour ajouter des ornements, des décorations ... On
peut bien entendu faire des animations avec, les positionner par rapport à leur parent (relative / absolute).
** Ils doivent obligatoirement avoir un `content: '';`**

## Centrer en 3 lignes de CSS (verticalement)

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
## REM, EM, %, VW Sizing

### %

### EM

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

### REM

* Le REM est basé sur la taille de la racine (soit la balise html) qui par défaut à une valeur de 16px. Afin d'éviter tout calcul, il est nécessaire de l'écraser en donnant une base de 10px soit 62.5px.
* Le REM est intéressant à utiliser si les média-queries employées sont en rem également. Cela vous permettra de garder des proportions égales lorsequ'on va redimensionner la page.
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

## liens utiles :

* [caniuse](http://caniuse.com)
