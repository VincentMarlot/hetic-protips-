

# Documentation

## Convention BEM

* B -> Block
* E -> Element
* M -> Modifier

```html
<!-- mainList = block -->
<ul class="mainList mainList--xmas">
  <!-- __item = Element = block -->
  <li class="mainList__item">
    <!-- __itemLink = Element -->
    <a class="mainList__itemLink--isActive" href="/Home"></a>

  </li>

  <li class="mainList__item">
    <!-- __itemLink = Element -->
    <a class="mainList__itemLink" href="/about"></a>

  </li>

  <li class="mainList__item">
    <!-- __itemLink = Element -->
    <a class="mainList__itemLink" href="/Works"></a>

  </li>

</ul>

```

```css  

.mainList {
  display: flex;
  justify-content: space-between;
  @--xmas {
    background: green;
  }
  &__item {
    list-style: none;
  }
  &__itemLink {
    color:red;
    &--isActive {
      color: white;
    }

  }
}

```

Exemple en css rendu:

```css

.mainList {

}

.mainList--xmas {

}

.mainList__item {

}

.mainList__itemLink {

}

.mainList__itemLink--isActive {

}
```

## Pseudo attributs

les pseudo attributs `before` et `after` permettent de créer des noeuds HTML en CSS. Ils sont essentiellement utilisés
pour ajouter des ornements, des décorations ... On peut bien entendu faire des animations avec, les positionner par
rapport à leur parent (relative / absolute). **Ils doivent obligatoirement avoir un `content: ''`** afin de s'afficher.

```HTML
<section>
  <h1 class="cover__mainTitle">Presentation des pseudo-attributs</h1>  
</section>

```

```css
.cover {
  background: #FDFDFD;
  padding: 20px;
  &__mainTitle { 
    text-align: center;
    font-size: 24px;
    color: green;
    position: relative;
    &::before,
    &::after {
      position: absolute; 
      content:'';
      display: block;
      width: 50px;
      height: 50px;
      background: green;
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

## REM, EM, %, VM Sizing

### %

### EM

```CSS
.cover {
  font-size: 100%; /* 16 px = 100% */
  &__mainTilte {
    /* 1em = 16px (taille du parent) */
  }
}

### REM

* Le REM est basé sur la taille de la racine (soit la balise <html>) qui, par défaut a une valeur de 16 px. Afin
d'éviter tout calcul, il est nécessaire de l'écraser en donnant une base de 10px soit 62.5%.
* Le REM est intéressant à utiliser si les media-queries employées sont en rem également. Cela vous permettra de garder
des proportions égales lorqu'on va redimensionner la page.
* Ses proportions seront également gardées quand l'utilisateur zoomera dans votre page.  

```css

html {
  font-size: 62.5%;
}
```

### VW(idth) / VHj(eight)

* Unités relatives à la taille de votre écran (peu importe le device)
* Attention au VH et à son contenu. 100vh = 100 vh quoi qu'il arrive.
* Très utile pour les interfaces fluides.

## Liens utiles:

* [caniuse](https://caniuse.com/) : c'est compatible partout ou pas ?
