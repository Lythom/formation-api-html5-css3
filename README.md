# API HTML&nbsp;5 et CSS&nbsp;3

---

## Samuel BOUCHET

Freelance - JavaScript developer and architect

[@Lythom](https://twitter.com/Lythom)

<img src="photo.png" style="width: 200px;height: auto;" />

---

## Le plan
  * le web version html&nbsp;5
  * structure des pages html&nbsp;5
  * webforms2
  * multimedia et graphisme
  * communications
  * webworkers
  * fichiers et ressources locales
  * device api
  * css3
  * responsive design

---

## LE WEB VERSION HTML&nbsp;5

___

### Définition et limites de HTML&nbsp;5

* Successeur de HTML&nbsp;4
* Ensemble de fonctionnalité
* Chaque fonctionnalité => support navigateur différent
* Concerne surtout l'API JavaScript
* Concerne aussi l'accessibilité et l'interactivité

___

### Support des navigateurs 

<a href="https://caniuse.com/" target="_blank">https://caniuse.com/</a>

___

### Compatibilité : Modernizr

Détecte le support d'une fonctionnalité par le navigateur

https://modernizr.com/

Note: 
* Modernizer
    * Au moment d'afficher la page chez l'utilisateur, répond à la question : Le navigateur supporte t'il la fonctionnalité X ?
    * Pivot de l'amélioration progressive (progressive enhancement)
    * Plus fin que la détection de user-agent navigateur
___
### Compatibilité : Polyfills

Ajoute en JavaScript une fonctionnalité native qu'un navigateur n'implémente pas

```html
Rechercher: 
<nom_fonctionalité> polyfill <navigateur_cible>
```

___
### Compatibilité : BabelJS

Permet de faire fonctionner une version récente de javascript (ES6) sur un navigateur qui ne le supporte.

https://babeljs.io/
___

### Impact sur les architectures Web

- &plus; de fonctionnalités
- Donc des applications web + riches
- Donc des architectures + complèxes

Quelques mots clés :
* Bibliothèque (<i lang="en">Library</i>)&nbsp;: A utiliser en l'état
* Framework&nbsp;: Impose une manière de faire
* Boilerplate&nbsp;: Squelette d'application pré construit
* Generators&nbsp;: initialise une appli sur mesure

Note: Architecture logiciel n'est pas l'objet de la formation, on va rester sur les fonctionnalités individuelles et garder l'architecture la plus simple possible.

___

### HTML&nbsp;5 pour les mobiles

<a href="https://caniuse.com/" target="_blank">https://caniuse.com/</a>

Les smartphones se sont développés au moment de HTML&nbsp;5&nbsp;: Très bon support globalement

Popularité des applications webview (ex: cordova)

Popularité des Progressive Web Applications (PWA)

Note: 
* le principe d'une application webview est d'encapsuler une page web dans une application mobile.
* PWA uniquement sous Android pour le moment (bientôt Microsoft) et qui permet d'installer une application web offline.

---

## STRUCTURE DES PAGES HTML&nbsp;5
  
clic droit -> afficher la source

* Doctype `<!doctype html>`
* Balises sémantiques `<section></section>`
* Microformats 
```html
<li itemtype="http://microformats.org/profile/hcard" itemscope>
    <div itemprop="fn">Tony Stark</div>
</li>
``` 

note: 
* pas de comparatif avec avant car peu d'intérêt de voir ce qu'on ne pouvait pas faire.
* Doctype pour indiquer au navigateur qu'on est en html5
* Balises sémantiques et microformats pour permettre une meilleur accessibilités (outils de retranscription vocaux ou brail, robots, référencement)

---

## WEBFORMS2 

___

### Nouveaux champs de saisie 

```html
<input name="myinput" type="choisir_ci-dessous" />
```

<div>
<small>
<ul style="float:left; width: 45%;">
<li>Hidden state (type=hidden)</li>
<li>Text (type=text) state and Search state (type=search)</li>
<li>Telephone state (type=tel)</li>
<li>URL state (type=url)</li>
<li>E-mail state (type=email)</li>
<li>Password state (type=password)</li>
<li>Date state (type=date)</li>
<li>Month state (type=month)</li>
<li>Week state (type=week)</li>
<li>Time state (type=time)</li>
</ul>
<ul style="float:left; width: 45%;">
<li>Local Date and Time state (type=datetime-local)</li>
<li>Number state (type=number)</li>
<li>Range state (type=range)</li>
<li>Color state (type=color)</li>
<li>Checkbox state (type=checkbox)</li>
<li>Radio Button state (type=radio)</li>
<li>File Upload state (type=file)</li>
<li>Submit Button state (type=submit)</li>
<li>Image Button state (type=image)</li>
<li>Reset Button state (type=reset)</li>
<li>Button state (type=button)</li>
</ul>
</small>
</div>

Note: intéressant de choisir précisément celui au plus près de la donnée pour faciliter l'utilisation: accessibilité, facilité.
___

### Sliders

https://caniuse.com/#search=sliders (94.5%)



### datalist

https://caniuse.com/#search=datalist (72.29%)
=> https://github.com/mfranzke/datalist-polyfill

List de suggestion de valeurs pour assister la saisie.
Autocompletion sans JavaScript.
Inidicateur visuels

Note: Polyfill à tester ! Fonctionnalité encore mal couverte : mettre en place le cas d'utilisation et tester sur toutes les cibles. 
Alternativement choisir une solution en JavaScript qui fournira un service équivalent.

### placeholder 

https://caniuse.com/#search=placeholder (97.7%)
___

### Expressions régulières 

___

### Validation automatique 

___

### Validation dans le code 

---

## MULTIMEDIA ET GRAPHISME 

___

### Audi et vidéo 

___

### Canvas 

___

### SVG 

___

### WebGL 

---

## COMMUNICATIONS 

___

### XHR2 

___

### CORS 

___

### JSON 

___

### Messaging 

___

### WebSocket 

---

## WEBWORKERS 

___

### Modèle mono-thread 

___

### Worker API 

___

### Synchronisation 

___

### Shared 

___

### Workers 

---

## FICHIERS ET RESSOURCES LOCALES 

___

### Local

___

### Storage 

___

### Session

___

### Storage 

___

### Application

___

### Cache 

___

### IndexDB 

___

### File API 

---

## DEVICE API  

___

### Géolocalisation  

___

### Orientation 

___

### Batterie 

___

### Caméra et micro 

___

### WebRTC

---

## CSS3 

___

### Fonts Sélecteurs CSS3 

___

### Bordures 

___

### Couleurs et opadte 

___

### Transitions et transformations 

___

### Animations 

---

## RESPONSIVE DESIGN 

___

### Vision OneWeb 

___

### Responsive Web Design 

___

### Progressive Enhancement 

___

### Media Query
