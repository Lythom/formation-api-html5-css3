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

Note:
* Beaucoup de choses
* Objectif: bien tout comprendre mais pas forcément mémoriser. Ce support permettra de retrouver les infos.
---

## LE WEB VERSION HTML&nbsp;5

___

### Définition et limites de HTML&nbsp;5

* Successeur de HTML&nbsp;4
* Spécification d'un ensemble de fonctionnalité et de comportements attendus
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
🔎 <nom_fonctionalité> polyfill <navigateur_cible>
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

<div class="small">
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
</div>

Note: 
* intéressant de choisir précisément celui au plus près de la donnée pour faciliter l'utilisation: accessibilité, facilité.
* Référence : https://www.w3.org/TR/html5/sec-forms.html#sec-states-of-the-type-attribute
___

### Sliders

https://caniuse.com/#search=sliders (94.5%)

```html
<input type="range" min="0" max="100" step="10" name="range" />
```
<input type="range" min="0" max="100" step="10" name="range" />
___

### datalist

<small>
https://caniuse.com/#search=datalist (72.29%)<br />
&#x1F50E; `"datalist polyfill"` ou bibliothèque spécifique
</small>

<div class="small">
<ul>
    <li>Liste de suggestions pour assister la saisie</li>
    <li>Autocompletion sans JavaScript</li>
    <li>Inidicateur visuels</li>
</ul>
</div>

```html
<input type="range" list="rangelist" min="0" max="100" name="range" />
<datalist id="rangelist">
    <option value="20" label="low">
    <option value="50">
    <option value="80" label="high">
</datalist>
```
<input type="range" list="rangelist" min="0" max="100" name="range" />
<datalist id="rangelist">
    <option value="20" label="low">
    <option value="50">
    <option value="80" label="high">
</datalist>

Note: Polyfill à tester ! Fonctionnalité encore mal couverte : mettre en place le cas d'utilisation et tester sur toutes les cibles. 
Alternativement choisir une solution en JavaScript qui fournira un service équivalent.

___

### placeholder 

https://caniuse.com/#search=placeholder (97.7%)

```html
<input type="text" list="valuelist" name="val" placeholder="Saisir une valeur" />
<datalist id="valuelist">
    <option value="abc" label="low">
    <option value="bcd">
    <option value="cde" label="high">
</datalist>
```
<input type="text" list="valuelist" name="val" placeholder="Saisir une valeur" />
<datalist id="valuelist">
    <option value="abc" label="low">
    <option value="bcd">
    <option value="cde" label="high">
</datalist>
___

### Expressions régulières 

Exemple 1:

```js
const dateRegexp = /[0-9]{2}-[0-9]{2}-[0-9]{4}/gi
document.getElementById('regexpDate').innerHTML = 'test de dates:' + '<br/>'
document.getElementById('regexpDate').innerHTML += '20/10/1987'.match(dateRegexp) + '<br/>'
document.getElementById('regexpDate').innerHTML += '20-10-1987'.match(dateRegexp) + '<br/>'
```
<div>
    <button onclick="
const dateRegexp = /[0-9]{2}-[0-9]{2}-[0-9]{4}/gi
document.getElementById('regexpDate').innerHTML = 'test de dates:' + '<br/>'
document.getElementById('regexpDate').innerHTML += '20/10/1987'.match(dateRegexp) + '<br/>'
document.getElementById('regexpDate').innerHTML += '20-10-1987'.match(dateRegexp) + '<br/>'
    " >Tester</button>
    <div id="regexpDate">
          
    </div>
</div>
___

### Expressions régulières 

Exemple 2:

```js
const bulletLine = /\* (.*)/g
const text = 
`* une ligne
* une autre
* ça va changer !`;
document.getElementById('regexpText').innerHTML = text.replace(bulletLine, '- $1<br/>')
```
<div>
    <button onclick="
const bulletLine = /\* (.*)/g
const text = 
`* une ligne
* une autre
* ça va changer !`;
document.getElementById('regexpText').innerHTML = text.replace(bulletLine, '- $1<br/>')
    " >Tester</button>
    <div id="regexpText">
    </div>
</div>

___

### Expressions régulières 

Impossible de penser à tous les cas du premier coup : 

&#x1F50E; `regexp date_fr`

___

### Validation automatique 

Avec un pattern

```html
<form action="#" name="validate1" onsubmit="alert(document.validate1.val.value);return false;">
<input type="text" list="valuelist2" name="val" placeholder="Saisir une valeur"
       pattern="[A-Za-z]{3}" title="3 lettres minuscule ou majuscules"/>
<datalist id="valuelist2">
    <option value="dfg" label="low">
    <option value="fgh">
    <option value="ghj" label="high">
</datalist>
<input type="submit" />
</form>
```

<form action="#" name="validate1" onsubmit="alert(document.validate1.val.value);return false;">
<input type="text" list="valuelist2" name="val" pattern="[A-Za-z]{3}" title="3 lettres minuscule ou majuscules" placeholder="Saisir une valeur" />
<datalist id="valuelist2">
    <option value="dfg" label="low">
    <option value="fgh">
    <option value="ghj" label="high">
</datalist>
<input type="submit" />
</form>

Note: Pas de visuel pour indiquer le champ en erreur sur tous les navigateur. Utiliser les sélecteurs de style `:valid` et `:invalid`
___

### Validation automatique 

Avec un required

```html
<form action="#" name="validate2" onsubmit="alert(document.validate2.val.value);return false;">
<input type="text" list="valuelist3" name="val" placeholder="Saisir une valeur"
       required pattern="[A-Za-z]{3}" title="3 lettres minuscule ou majuscules"  />
<datalist id="valuelist3">
    <option value="jkl" label="low">
    <option value="klm">
    <option value="mpo" label="high">
</datalist>
<input type="submit" />
</form>
```

<form action="#" name="validate2" onsubmit="alert(document.validate2.val.value);return false;">
<input type="text" list="valuelist3" name="val" required pattern="[A-Za-z]{3}" title="3 lettres minuscule ou majuscules" placeholder="Saisir une valeur" />
<datalist id="valuelist3">
    <option value="jkl" label="low">
    <option value="klm">
    <option value="mpo" label="high">
</datalist>
<input type="submit" />
<button onclick="
function formIsValid(e) {
    const list = document.getElementById('valuelist3').options
    const value = document.validate2.val.value
    if (value === 'secret') return true
    for(var i = 0; i < list.length; i++) {
        if (list.item(i).value === value) return true
    }
    e.preventDefault();
    return false;
}
alert(formIsValid(event))
"/>Valider par le code (voir slide suivante)</button>
</form>

Note: Pas de changement visuel a priori, indication visuelle "required" (souvent asterisque + message) à faire en html.

___

### Validation dans le code  

Par exemple en forçant une valeur de la datalist

```html
<form … onsubmit="return formIsValid();">
```

```js
function formIsValid() {
  const value = document.validate2.val.value
  const list = document.getElementById('valuelist3').options
  if (value === 'secret') return true
  for(var i = 0; i < list.length; i++) {
      if (list.item(i).value === value) return true
  }
  return false;
}
```

Note: Chercher dans la doc de l'api pour connaitre la structure des données, ici : https://www.w3schools.com/jsref/coll_datalist_options.asp

---

## MULTIMEDIA ET GRAPHISME 

___

### Vidéo 

https://developer.mozilla.org/fr/docs/Web/HTML/Element/Video

```html
<video src="https://zippy.gfycat.com/WavyMeanDesertpupfish.webm" 
       height="150" loop controls
       poster="https://cdn.pixabay.com/photo/2017/11/11/23/31/curtain-2940999__340.png">
  Votre navigateur ne permet pas de lire les vidéos.
  Mais vous pouvez toujours <a href="https://zippy.gfycat.com/WavyMeanDesertpupfish.webm">la télécharger</a> !
</video>
```
<video src="https://zippy.gfycat.com/WavyMeanDesertpupfish.webm" 
       height="200" loop controls
       poster="https://cdn.pixabay.com/photo/2017/11/11/23/31/curtain-2940999__340.png">
  Votre navigateur ne permet pas de lire les vidéos.
  Mais vous pouvez toujours <a href="https://zippy.gfycat.com/WavyMeanDesertpupfish.webm">la télécharger</a> !
</video>

___

### Audio 

https://developer.mozilla.org/fr/docs/Web/HTML/Element/audio

```html
<audio src="http://developer.mozilla.org/@api/deki/files/2926/=AudioTest_(1).ogg" 
       autoplay>
  Votre navigateur ne supporte pas l'élément <code>audio</code>.
</audio>
```
___

### Canvas 

```html
<canvas id='canvas1' width='480' height='320'> Canvas not supported</canvas>
```
```js
const c = document.getElementById('canvas1');
const ctx = c.getContext('2d');
let x = 100, y = 160, i = 0;
ctx.fillStyle = 'lightgrey'; ctx.fillRect(0, 0, 480, 320);
// axis
ctx.beginPath();ctx.strokeStyle='red';
ctx.moveTo(0,y);ctx.lineTo(480,y);ctx.stroke();
ctx.moveTo(x,0);ctx.lineTo(x,320);ctx.stroke();
// draw function
ctx.beginPath();ctx.moveTo(x,y + Math.sin(0) * 100);
setInterval(function() {
    i++;
    ctx.lineTo(x + i, y + Math.sin(i/50) * 100);
    ctx.strokeStyle='black';ctx.stroke();
}, 1000/60)
```

<canvas id="canvas1" width="480" height="320" style="position: absolute; left: 60%;top: 50%;">
  Canvas not supported
</canvas>

<button onclick="
const c = document.getElementById('canvas1');
const ctx = c.getContext('2d');
let x = 100, y = 160, i = 0;
ctx.fillStyle = 'lightgrey'; ctx.fillRect(0, 0, 480, 320);
// axis
ctx.beginPath();ctx.strokeStyle='red';
ctx.moveTo(0,y);ctx.lineTo(480,y);ctx.stroke();
ctx.moveTo(x,0);ctx.lineTo(x,320);ctx.stroke();
// draw function
ctx.beginPath();ctx.moveTo(x,y + Math.sin(0) * 100);
setInterval(function() {
    i++;
    ctx.lineTo(x + i, y + Math.sin(i/50) * 100);
    ctx.strokeStyle='black';ctx.stroke();
}, 1000/60)
">Dessiner !</button>
___

### SVG 

```html
<svg width="480" height="320">
  <rect width="480" height="320" style="fill:lightgrey;" />
  <rect x="100" y="0" width="1" height="320" style="fill:red;" />
  <rect x="0" y="160" width="480" height="1" style="fill:red;" />
  <path id="svgpath" d="M 100 160 L 101 162 L 102 164 L 103 166 L 104 168 L 105 170 L 106 172 L 107 174 L 108 176 L 109 178 L 110 180 L 111 182 L 112 184 L 113 186 L 114 188 L 115 190 L 116 191 L 117 193 L 118 195 L 119 197 L 120 199 L 121 201 L 122 203 L 123 204 L 124 206 L 125 208 L 126 210 L 127 211 L 128 213 L 129 215 L 130 216 L 131 218 L 132 220 L 133 221 L 134 223 L 135 224 L 136 226 L 137 227 L 138 229 L 139 230 L 140 232 L 141 233 L 142 234 L 143 236 L 144 237 L 145 238 L 146 240 L 147 241 L 148 242 L 149 243 L 150 244 L 151 245 L 152 246 L 153 247 L 154 248 L 155 249 L 156 250 L 157 251 L 158 252 L 159 252 L 160 253 L 161 254 L 162 255 L 163 255 L 164 256 L 165 256 L 166 257 L 167 257 L 168 258 L 169 258 L 170 259 L 171 259 L 172 259 L 173 259 L 174 260 L 175 260 L 176 260 L 177 260 L 178 260 L 179 260 L 180 260 L 181 260 L 182 260 L 183 260 L 184 259 L 185 259 L 186 259 L 187 259 L 188 258 L 189 258 L 190 257 L 191 257 L 192 256 L 193 256 L 194 255 L 195 255 L 196 254 L 197 253 L 198 253 L 199 252 L 200 251 L 201 250 L 202 249 L 203 248 L 204 247 L 205 246 L 206 245 L 207 244 L 208 243 L 209 242 L 210 241 L 211 240 L 212 238 L 213 237 L 214 236 L 215 235 L 216 233 L 217 232 L 218 230 L 219 229 L 220 228 L 221 226 L 222 225 L 223 223 L 224 221 L 225 220 L 226 218 L 227 217 L 228 215 L 229 213 L 230 212 L 231 210 L 232 208 L 233 206 L 234 205 L 235 203 L 236 201 L 237 199 L 238 197 L 239 195 L 240 193 L 241 192 L 242 190 L 243 188 L 244 186 L 245 184 L 246 182 L 247 180 L 248 178 L 249 176 L 250 174 L 251 172 L 252 170 L 253 168 L 254 166 L 255 164 L 256 162 L 257 160 L 258 158 L 259 156 L 260 154 L 261 152 L 262 150 L 263 148 L 264 146 L 265 144 L 266 142 L 267 140 L 268 138 L 269 136 L 270 134 L 271 133 L 272 131 L 273 129 L 274 127 L 275 125 L 276 123 L 277 121 L 278 119 L 279 118 L 280 116 L 281 114 L 282 112 L 283 110 L 284 109 L 285 107 L 286 105 L 287 104 L 288 102 L 289 100 L 290 99 L 291 97 L 292 96 L 293 94 L 294 93 L 295 91 L 296 90 L 297 88 L 298 87 L 299 86 L 300 84 L 301 83 L 302 82 L 303 81 L 304 79 L 305 78 L 306 77 L 307 76 L 308 75 L 309 74 L 310 73 L 311 72 L 312 71 L 313 70 L 314 69 L 315 68 L 316 68 L 317 67 L 318 66 L 319 65 L 320 65 L 321 64 L 322 64 L 323 63 L 324 63 L 325 62 L 326 62 L 327 61 L 328 61 L 329 61 L 330 61 L 331 60 L 332 60 L 333 60 L 334 60 L 335 60 L 336 60 L 337 60 L 338 60 L 339 60 L 340 60 L 341 61 L 342 61 L 343 61 L 344 61 L 345 62 L 346 62 L 347 63 L 348 63 L 349 64 L 350 64 L 351 65 L 352 65 L 353 66 L 354 67 L 355 67 L 356 68 L 357 69 L 358 70 L 359 71 L 360 72 L 361 73 L 362 74 L 363 75 L 364 76 L 365 77 L 366 78 L 367 79 L 368 80 L 369 81 L 370 83 L 371 84 " stroke="black" stroke-width="3" fill="none" />
</svg>
```
```js
const path = document.getElementById('svgpath');
let x = 100, y = 160, i = 0;
path.setAttribute('d', /* … */);
setInterval(function() {
    i++;
    path.setAttribute('d', /* … */);
}, 1000/60)
```
<svg width="480" height="320" style="position: absolute; left: 60%;top: 50%;">
  <rect width="480" height="320" style="fill:lightgrey;" />
  <rect x="100" y="0" width="1" height="320" style="fill:red;" />
  <rect x="0" y="160" width="480" height="1" style="fill:red;" />
  <path id="svgpath" d="M 100 160 L 101 162 L 102 164 L 103 166 L 104 168 L 105 170 L 106 172 L 107 174 L 108 176 L 109 178 L 110 180 L 111 182 L 112 184 L 113 186 L 114 188 L 115 190 L 116 191 L 117 193 L 118 195 L 119 197 L 120 199 L 121 201 L 122 203 L 123 204 L 124 206 L 125 208 L 126 210 L 127 211 L 128 213 L 129 215 L 130 216 L 131 218 L 132 220 L 133 221 L 134 223 L 135 224 L 136 226 L 137 227 L 138 229 L 139 230 L 140 232 L 141 233 L 142 234 L 143 236 L 144 237 L 145 238 L 146 240 L 147 241 L 148 242 L 149 243 L 150 244 L 151 245 L 152 246 L 153 247 L 154 248 L 155 249 L 156 250 L 157 251 L 158 252 L 159 252 L 160 253 L 161 254 L 162 255 L 163 255 L 164 256 L 165 256 L 166 257 L 167 257 L 168 258 L 169 258 L 170 259 L 171 259 L 172 259 L 173 259 L 174 260 L 175 260 L 176 260 L 177 260 L 178 260 L 179 260 L 180 260 L 181 260 L 182 260 L 183 260 L 184 259 L 185 259 L 186 259 L 187 259 L 188 258 L 189 258 L 190 257 L 191 257 L 192 256 L 193 256 L 194 255 L 195 255 L 196 254 L 197 253 L 198 253 L 199 252 L 200 251 L 201 250 L 202 249 L 203 248 L 204 247 L 205 246 L 206 245 L 207 244 L 208 243 L 209 242 L 210 241 L 211 240 L 212 238 L 213 237 L 214 236 L 215 235 L 216 233 L 217 232 L 218 230 L 219 229 L 220 228 L 221 226 L 222 225 L 223 223 L 224 221 L 225 220 L 226 218 L 227 217 L 228 215 L 229 213 L 230 212 L 231 210 L 232 208 L 233 206 L 234 205 L 235 203 L 236 201 L 237 199 L 238 197 L 239 195 L 240 193 L 241 192 L 242 190 L 243 188 L 244 186 L 245 184 L 246 182 L 247 180 L 248 178 L 249 176 L 250 174 L 251 172 L 252 170 L 253 168 L 254 166 L 255 164 L 256 162 L 257 160 L 258 158 L 259 156 L 260 154 L 261 152 L 262 150 L 263 148 L 264 146 L 265 144 L 266 142 L 267 140 L 268 138 L 269 136 L 270 134 L 271 133 L 272 131 L 273 129 L 274 127 L 275 125 L 276 123 L 277 121 L 278 119 L 279 118 L 280 116 L 281 114 L 282 112 L 283 110 L 284 109 L 285 107 L 286 105 L 287 104 L 288 102 L 289 100 L 290 99 L 291 97 L 292 96 L 293 94 L 294 93 L 295 91 L 296 90 L 297 88 L 298 87 L 299 86 L 300 84 L 301 83 L 302 82 L 303 81 L 304 79 L 305 78 L 306 77 L 307 76 L 308 75 L 309 74 L 310 73 L 311 72 L 312 71 L 313 70 L 314 69 L 315 68 L 316 68 L 317 67 L 318 66 L 319 65 L 320 65 L 321 64 L 322 64 L 323 63 L 324 63 L 325 62 L 326 62 L 327 61 L 328 61 L 329 61 L 330 61 L 331 60 L 332 60 L 333 60 L 334 60 L 335 60 L 336 60 L 337 60 L 338 60 L 339 60 L 340 60 L 341 61 L 342 61 L 343 61 L 344 61 L 345 62 L 346 62 L 347 63 L 348 63 L 349 64 L 350 64 L 351 65 L 352 65 L 353 66 L 354 67 L 355 67 L 356 68 L 357 69 L 358 70 L 359 71 L 360 72 L 361 73 L 362 74 L 363 75 L 364 76 L 365 77 L 366 78 L 367 79 L 368 80 L 369 81 L 370 83 L 371 84 " stroke="black" stroke-width="3" fill="none" />
</svg>

<button onclick="
const path = document.getElementById('svgpath');
let x = 100, y = 160, i = 0;
path.setAttribute('d', path.getAttribute('d') + 
    'M ' +
    x + ' ' +
    Math.round(y + Math.sin(i/50) * 100) + ' ');
setInterval(function() {
    i++;
    path.setAttribute('d', path.getAttribute('d')  +
    'L ' +
    (x + i) + ' ' +
    Math.round(y + Math.sin(i/50) * 100) + ' ');
}, 1000/60)
">Dessiner !</button>

___

### WebGL 


```html
<canvas id='canvas' width='480' height='320'> Canvas not supported</canvas>
```
```js
const c = document.getElementById('canvas2');
const gl = c.getContext('webgl');
// instructions opengl a partir d'ici
// c'est trop long pour une slide
```

<canvas id="canvas2" width="480" height="320" style="position: absolute; left: 60%;top: 50%;">
  Canvas not supported
</canvas>

<button onclick="

// instructions opengl a partir d'ici
function shaderProgram(gl, vs, fs) {
	var prog = gl.createProgram();
	var addshader = function(type, source) {
		var s = gl.createShader((type == 'vertex') ?
			gl.VERTEX_SHADER : gl.FRAGMENT_SHADER);
		gl.shaderSource(s, source);
		gl.compileShader(s);
		if (!gl.getShaderParameter(s, gl.COMPILE_STATUS)) {
			throw 'Could not compile '+type+
				' shader:\n\n'+gl.getShaderInfoLog(s);
		}
		gl.attachShader(prog, s);
	};
	addshader('vertex', vs);
	addshader('fragment', fs);
	gl.linkProgram(prog);
	if (!gl.getProgramParameter(prog, gl.LINK_STATUS)) {
		throw 'Could not link the shader program!';
	}
	return prog;
}

function attributeSetFloats(gl, prog, attr_name, rsize, arr) {
	gl.bindBuffer(gl.ARRAY_BUFFER, gl.createBuffer());
	gl.bufferData(gl.ARRAY_BUFFER, new Float32Array(arr),
		gl.STATIC_DRAW);
	var attr = gl.getAttribLocation(prog, attr_name);
	gl.enableVertexAttribArray(attr);
	gl.vertexAttribPointer(attr, rsize, gl.FLOAT, false, 0, 0);
}

function init() {
	try {
        const c = document.getElementById('canvas2');
        const gl = c.getContext('webgl');
        
        var prog = shaderProgram(gl,
            'attribute vec3 pos;'+
            'void main() {'+
            '	gl_Position = vec4(pos, 2.0);'+
            '}',
            'void main() {'+
            '	gl_FragColor = vec4(0.5, 0.5, 1.0, 1.0);'+
            '}'
        );
        gl.useProgram(prog);
    
        attributeSetFloats(gl, prog, 'pos', 3, [
            -1, 0, 0,
            0, 1, 0,
            0, -1, 0,
            1, 0, 0
        ]);
        
        gl.drawArrays(gl.TRIANGLE_STRIP, 0, 4);
    } catch (e) {
        alert('Error: '+e);
    }
}
setTimeout(init, 100);

">Dessiner !</button>

Note: Canvas avancé pour utiliser la puissance de la carte graphique.

---

## COMMUNICATIONS 

___

### Réseau

Architecture client / serveur

HTTP = protocole de transfert

format du message HTTP = headers + payload

headers = request [ + response ] + métadonnées

___

### JSON 

<div class="small">
Format d'échange privilégié sur le web aujourd'hui

compatible avec l'objet JavaScript

Autres formats similaires : xml, yaml, formats binaires
</div>

```json
{ 
  "menu": "Fichier", 
  "commandes": [ 
      {
          "titre": "Nouveau", 
          "action":"CreateDoc"
      }, 
      {
          "titre": "Ouvrir", 
          "action": "OpenDoc"
      }
   ] 
} 
```    

Note:
___

### XHR2 

Ne pas utiliser XHR2 !

https://developer.mozilla.org/fr/docs/Web/API/Fetch_API     
&plus; polyfills si besoin (https://github.com/github/fetch)

```js
fetch('/users.json')
  .then(function(response) {
    return response.json()
  }).then(function(json) {
    console.log('parsed json', json)
  }).catch(function(ex) {
    console.log('parsing failed', ex)
  })
```

Note: Les Polyfills s'appuiront sur xhr2 de façon transparent pour vous.

___

### fetch typical use

```js
function checkStatus(response) {
  if (response.status >= 200 && response.status < 300) {
    return response
  } else {
    var error = new Error(response.statusText)
    error.response = response
    throw error
  }
}
function parseJSON(response) {
  return response.json()
}
fetch('/users')
  .then(checkStatus)
  .then(parseJSON)
  .then(function(data) {
    console.log('request succeeded with JSON response', data)
  }).catch(function(error) {
    console.log('request failed', error)
  })
```

___

### CORS (Cross-Origin Resource Sharing )

Système de sécurité implémenté par les navigateurs

Empêche par défaut les requêtes cross-sites    
(En anglais *cross-domain*)

Se configure au niveau du serveur web, les informations sont transmises à travers les headers http

```text
Access-Control-Allow-Origin: http://foo.example
Access-Control-Allow-Methods: POST, GET, OPTIONS
Access-Control-Allow-Headers: X-PINGOTHER
Access-Control-Max-Age: 1728000
```

https://developer.mozilla.org/fr/docs/HTTP/Access_control_CORS

Note: Laissez les développeurs expérimentés vous expliquer.

___

### Messaging 

https://html.spec.whatwg.org/multipage/web-messaging.html#crossDocumentMessages

Note: Je n'en ai jamais eu l'usage, permet de transmettre des messages entre plus pages de domaines différents. Plus souvent fetch + politique CORS sont utilisés pour communiquer.
___

### WebSocket 

Ouverture d'un socket réseau direct entre un serveur et un client. socket = adresse IP + port

Nécessite un serveur websocket dédié, application différente du serveur http

Utiliser des bibliothèques plutôt que l'API native, https://socket.io/

WebRTC est une autre API qui met l'accent sur les performances du streaming, plus complexe

Note: la plupart du temps le même serveur fait à la fois HTTP et Websocket, parfois même au sein du même programme serveur, mais il s'agit bien de 2 mécaniques complètement différentes pour communiquer entre client et serveur.

---

## WEBWORKERS 

___

### Modèle mono-thread 

* JavaScript est mono-threadé
* L'asynchrone est simplement décalé dans la file d'exécution
* Le système d'événements permet à l'environnement (navigateur, système d'exploitation) de notifier d'une changement
* Système d'événement est la force des performances de JavaScript
___

### Workers 

Agents qui exécutent du code Asynchrone

___

### Shared 

* type spécifique de worker qui peut être accédé à partir de plusieurs contextes de navigation, tels que plusieurs fenêtres, iframes ou même workers
* Utile pour synchroniser des données par exemple
* https://developer.mozilla.org/fr/docs/Web/API/SharedWorker

---

## FICHIERS ET RESSOURCES LOCALES 

___

### LocalStorage et SessionStorage

* https://caniuse.com/#search=web%20storage (95.31%)
* Stocker des données dans le navigateur
* localStorage persiste, peut être vidé manuellement
* sessionStorage vidé à la fin de la session

```js
localStorage.setItem("username", "John");
alert( "username = " + localStorage.getItem("username"));
```

~ 10Mo de capacité

___

### <strike>ApplicationCache</strike> Service Workers 

https://caniuse.com/#search=Service%20Workers (73.67%)
https://developer.mozilla.org/fr/docs/Web/API/Service_Worker_API/Using_Service_Workers <!-- .element: class="small" -->

* Stocke des fichiers en cache
* Permet de rendre l'entièreté de votre site disponible une fois déconnecté du réseau

Note: Les Services Workers ne sont pas trivial à utiliser mais pas non plus excessivement complèxes. Avancer étape par étape.

Capacité dépends des navigateur et du disque dur de l'utilisateur, en théorie beaucoup (> 100 Mo partagés)
___

### IndexedDB 

https://caniuse.com/#search=indexedDB (93.98%)

Stocker des données dans une base de données objets sur le navigateur du client

https://developer.mozilla.org/fr/docs/Web/API/API_IndexedDB

Capacité dépends des navigateur et du disque dur de l'utilisateur, en théorie beaucoup (> 100 Mo partagés)

___

### File API 

https://caniuse.com/#search=file%20API (94.62%)

Manipuler des fichiers sélectionnés par l'utilisateur côté client

https://developer.mozilla.org/fr/docs/Web/API/File/Using_files_from_web_applications <!-- .element: class="small" -->

Plusieurs cas d'utilisation (téléchargement, affichage des images, modification avec envoi)

---

## DEVICE API  

___

### Géolocalisation  

https://caniuse.com/#search=Geolocation (95.01%)

Connaitre la position de l'utilisateur

```js
if ("geolocation" in navigator) {
  /* géolocalisation possible */
  navigator.geolocation.getCurrentPosition(function(position) {
    do_something(position.coords.latitude, position.coords.longitude);
  })
} else {
  alert("Le service de géolocalisation n'est pas disponible sur votre ordinateur.");
}
```

___

### Orientation 


https://caniuse.com/#search=Orientation (91.8%)

Connaitre l'orientation du téléphone

<div>
    <div class="small" style="display: inline-block;">
        <pre>
        window.addEventListener('deviceorientation', handleOrientation);
        function handleOrientation(event) {
          // true pour un référentiel terrestre
          // false pour un référentiel arbitraire
          const absolute = event.absolute;
          // inclinaison autour de l"axe Z
          const alpha    = event.alpha;
          // inclinaison autour de l"axe X
          const beta     = event.beta;
          // inclinaison autour de l"axe Y
          const gamma    = event.gamma;
        }
        </pre>
    </div>
    <div class="small" style="display: inline-block;width: 29%;vertical-align: top;">
        <img src="https://developer.mozilla.org/@api/deki/files/5694/=axes.png"/>
    </div>
    <div class="small">Source: https://developer.mozilla.org/en-US/docs/Web/Guide/Events/Orientation_and_motion_data_explained</div>
</div>

___

### Batterie 

https://caniuse.com/#search=battery (69.15%)<!-- .element: class="small" -->

Connaitre l'état de charge du périphérique. Support en baisse pour confidentialité. <!-- .element: class="small" -->

```js
const battery = navigator.battery || navigator.mozBattery || navigator.webkitBattery;

function updateBatteryStatus() {
  console.log("Batterie chargée à : " + battery.level * 100 + " %");
  if (battery.charging) { console.log("Chargement de la batterie"); }
}
battery.addEventListener("chargingchange", updateBatteryStatus);
battery.addEventListener("levelchange", updateBatteryStatus);
updateBatteryStatus();
```
<div class="small">Source: https://developer.mozilla.org/fr/docs/Web/API/Battery_status_API</div>
___

### Caméra et micro 

https://caniuse.com/#search=getUserMedia (84.56%)

Obtenir un flux de données du micro ou de la webcam.

Nombreux changement d'API, utilisation d'un Shim ou d'un polyfill recommandé. <!-- .element: class="small" -->
```html
🔎 Shim getUserMedia
```

---

## CSS3 

___

### Fonts 
Problématique très complèxe <!-- .element: class="small" -->

#### Sans webfont

* Dépendant du système => http://fontfamily.io/
* Utiliser une font stack
```html
🔎 css font stack
```
* Peu de choix, pas de fantaisie
___

### Fonts 
Problématique très complèxe <!-- .element: class="small" -->

#### avec webfont

* Problèmatique de performance
  * FOUT (Flash Of Unstyled Text)<!-- .element: class="small" -->
  * FOIT (Flash Of Invisible Text)<!-- .element: class="small" -->
  * FOFT (Flash Of Faux Text)<!-- .element: class="small" -->
  * https://www.zachleat.com/web/comprehensive-webfonts<!-- .element: class="smaller" -->
  * https://www.zachleat.com/web/recipes/<!-- .element: class="smaller" -->
* Problèmatiques de fidélité du rendu
  * https://blog.clever-age.com/fr/2012/08/29/optimiser-le-rendu-de-font-face/ <!-- .element: class="smaller" -->

Note:
Si possible confier le sujet à un web developer expérimenté. Sinon suivre une méthode éprouvée.
___

### Fonts

Approche naïve

```css
@font-face {
    font-family: 'League Gothic';
    src: url('league-gothic.eot');
    src: url('league-gothic.eot?#iefix') format('embedded-opentype'),
         url('league-gothic.woff') format('woff'),
         url('league-gothic.ttf') format('truetype');
}
```
<span style="font-family: 'League Gothic'">Je suis en League Gothic !</span>
```htlm
<span style="font-family: 'League Gothic'">Je suis en League Gothic !</span>
```
___

### Sélecteurs CSS&nbsp;3 

https://caniuse.com/#search=CSS3%20selectors (98.16%)

sélecteurs CSS utilisés également dans les biblitohèque de requêtage du DOM

```html
🔎 css selecteur <motif>
```

https://developer.mozilla.org/fr/docs/Web/CSS/S%C3%A9lecteurs_CSS<!-- .element: class="small" -->

___

### Sélecteurs CSS&nbsp;3

<div class="small">
<ul style="float:left; width: 45%;">
<li>[foo^="bar"] (attribute start with)</li>
<li>[foo$="bar"] (attribute end with)</li>
<li>[foo*="bar"] (attribute contains)</li>
<li>:root (racine du document)</li>
<li>:nth-child()</li>
<li>:nth-last-child()</li>
<li><type>:nth-of-type()</li>
<li><type>:nth-last-of-type()</li>
<li>:last-child</li>
<li>:first-of-type</li>
<li>:last-of-type</li>
</ul>
<ul style="float:left; width: 45%;">
<li>:only-child</li>
<li>:only-of-type</li>
<li>:empty</li>
<li>:target</li>
<li>:enabled</li>
<li>:disabled</li>
<li>:checked</li>
<li>:not()</li>
<li>~</li>
</ul>
</div>

___

### Sélecteurs CSS&nbsp;3

<div class="small">
* Préférez les sélecteurs de class (`.nomDeClasse`)
* Évitez les sélecteurs d'identifiant (`#toujoursUniqueSaufParfois`)
* Évitez les sélecteurs de type (`span, div, a, button`)
* Évitez les sélecteurs universels ou d'attributs seuls
  * OUI (dans un context fermé)
    * `.monElement > *`, `input.avecStyleSpecial[type=range]`
  * NON (dans un context trop large)
    * `div > *`, `[type=range]`
</div>
Note:
Sélecteurs de styles à utiliser pour les styles globaux uniquement (reset, choix de design à grande échelle)



___

### Bordures 

```css
 .shadowBox {
       width: 200px;
       color: #444444;
       background-color: #ddd; /* Fallback for older browsers */
       background-image: linear-gradient(#E5E5E5, #CFCFCF);
       box-shadow: -1px 2px 5px 1px rgba(0, 0, 0, 0.7) /* inset */; 
       margin: 2rem;
       padding: 1rem;
    }
```
<style>
    .shadowBox {
       display: inline-block;
       width: 200px;
       color: #444444;
       background-color: #ddd;
       background-image: linear-gradient(#E5E5E5, #CFCFCF);
       box-shadow: -1px 2px 5px 1px rgba(0, 0, 0, 0.7);
       margin: 2rem !important;
       padding: 1rem !important;
    }
    .shadowBox2 {
       display: inline-block;
       width: 200px;
       color: #444444;
       background-color: #ddd;
       background-image: linear-gradient(#E5E5E5, #CFCFCF);
       box-shadow: -1px 2px 5px 1px rgba(0, 0, 0, 0.7) inset; 
       margin: 2rem !important;
       padding: 1rem !important;
    }
</style>
<div>
    <div class="shadowBox">Boite avec ombrage</div>
    <div class="shadowBox2">Boite avec ombrage 2</div>
</div>

___

### Couleurs et opacité 

espace de couleur sRGB sur le web (sRGB color space)

```css
.shadowBoxLeft {
    background-color: rgba(255, 0, 0, 0.5);
}
.shadowBoxRight {
    background-image: linear-gradient(#0000FF, rgba(0, 0, 255, 0));
    /* #0000FFFF = rgba(0, 0, 255, 1) 
                 = rgb(0, 0, 255) 
                 = hsla(240, 100%, 50%, 1) 
                 = hsl(240, 100%, 50%) */
}
```
    
<style>
    .shadowBox3 {
       display: inline-block;
       width: 200px;
       color: #444444;
       background-color: rgba(255, 0, 0, 0.5);
       box-shadow: -1px 2px 5px 1px rgba(0, 0, 0, 0.7);
       margin: 2rem !important;
       padding: 1rem !important;
    }
    .shadowBox4 {
       display: inline-block;
       width: 200px;
       color: #444444;
       background-color: rgba(0, 0, 255, 0.3);
       background-image: linear-gradient(rgba(0, 0, 255, 1), rgba(0, 0, 255, 0));
       box-shadow: -1px 2px 5px 1px rgba(0, 0, 0, 0.7) inset; 
       margin-left: -5rem !important;
       padding: 1rem !important;
    }
</style>
<div>
    <div class="shadowBox3">Boite avec ombrage</div>
    <div class="shadowBox4">Boite avec ombrage 2</div>
</div>

___

### Transitions et transformations 

```css
.spinButton {
    transition: transform 0.5s ease-in;
}
.spinButton:active {
    transform: rotate(270deg);
}
.spinButton.easeout {
    transition: transform 0.5s ease-out;
}
```

<style>
.spinButton {
    transition: transform 0.5s ease-in;
    height: 96px;
    width: 96px;
}
.spinButton:active {
    transform: rotate(270deg);
}
.spinButton.easeout {
    transition: transform 0.5s ease-out;
}
</style>

<button class="spinButton">Click me ! Ease-in</button>
<button class="spinButton easeout">Click me ! Ease-out</button>

```html
<button class="spinButton">Click me ! Ease-in</button>
<button class="spinButton easeout">Click me ! Ease-out</button>
```

Note: 
mots clés: css transition et css transform;
performance de `transform` (`scale, opacitity, rotate`) meilleures que de modifier width et height en JavaScript.
___

### Animations 

```css
@keyframes alwaysSpinButtonAnimation {
    from {transform: rotate(0deg);}
    50% {transform: rotate(90deg);}
    to {transform: rotate(360deg);}
}

.alwaysSpinButton {
    animation-name: alwaysSpinButtonAnimation;
    animation-duration: 1s;
    animation-iteration-count: 10;
    animation-timing-function: linear;
}
```

<style>
@keyframes alwaysSpinButtonAnimation {
    from {transform: rotate(0deg);}
    50% {transform: rotate(90deg);}
    to {transform: rotate(360deg);}
}

.alwaysSpinButton {
    height: 96px;
    width: 96px;
    animation-name: alwaysSpinButtonAnimation;
    animation-duration: 1s;
    animation-iteration-count: 10;
    animation-timing-function: linear;
}
</style>

<button class="alwaysSpinButton">Click me !</button>

```html
<button class="spinButton">Click me !</button>
<button class="spinButton easeout">Click me !</button>
```

Note: 
mots clés: css animation keyframes;

---

## RESPONSIVE DESIGN 

___

### Responsive Web Design (RWD)

Contenu qui s'adapte à l'espace d'affichage disponible

* Grille fluide (float, display: inline-block, flexbox, CSS grid)
* Media queries (`@media screen and (min-width: 1024px) {`)
    * Avec breakpoints
    * Sur mesure
* Element queries (nécessite JavaScript)
* images et video adaptives
* SVG et vectoriel

<!-- .element: class="small" -->

https://developer.mozilla.org/fr/Apps/app_layout/responsive_design_building_blocks

___

### Progressive Enhancement 

* Utiliser les fonctionnalités les répandues en premier
* Utiliser modernizr pour ajouter des fonctionnalités si possible
* Avoir un fallback CSS pour les propriétés mal supportées

---

Retrouver les slides sur https://github.com/Lythom/formation-api-html5-css3

<div class="smaller">
    <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/"><img alt="Licence Creative Commons" style="border-width:0" src="https://i.creativecommons.org/l/by-nc-sa/4.0/88x31.png" /></a><br /><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">Formation aux API HTML5 et CSS3</span> de <a xmlns:cc="http://creativecommons.org/ns#" href="https://github.com/Lythom/formation-api-html5-css3/" property="cc:attributionName" rel="cc:attributionURL">Samuel Bouchet</a> est mis à disposition selon les termes de la <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/4.0/">licence Creative Commons Attribution - Pas d’Utilisation Commerciale - Partage dans les Mêmes Conditions 4.0 International</a>.
</div>