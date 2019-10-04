
TP 1 Les notions fondamentales, une à une.
===
## Créer un premier component React

### Contexte

Les components ```React``` sont des ```fonctions``` ou des ```classes``` qui renvoient du HTML, sur lequel on pourra facilement greffer du javascript ( pour montrer une valeur qui vient d'une ```variable``` en ```javascript```, ou éxecuter une ```fonction javascript``` lors d'un événement )

Ainsi, les components renvoient soit directement du ```HTML``` ( via ```JSX```), soit d'autres components qui eux-même renvoient du ```HTML```

Dans le JSX, on appelle soit des éléments html, soit des components. 
Pour que React fasse la distinction, on appellera toujours un component avec une majuscule.

ex:

< button /> sera un élément HTML

< Button /> sera un component React que l'on aura appelé Button.

### Instructions :
-------


- créez un component Button et appelez le dans App
- -------



## gérer les props d'un component

Les props sont des ```propriétés``` du component, qui pourront lui permettre d'avoir une ou des ```valeurs``` et/ou un ou des ```comportements``` particuliers lorsque ce component sera appelé, pour qu'il réponde aux besoins spécifiques liés au contexte où l'on a besoin de lui.

ex: 

un component Button aura un props ```title``` dont la valeur sera 'Se connecter' s'il est utilisé dans la partie login, et 'Soumettre' dans le cas où fait partie d'un formulaire.

De même, les fonctions qu'il executera au click seront différentes ( appel vers le serveur pour s'authentifier dans le premier cas, appel au serveur pour envoyer les données du formulaire dans l'autre cas.)


### Instructions
-------
- faire une liste de 5 - 10 props pour : 
  - un menu
  - une liste
  - un bouton

- proposez à votre component de pouvoir gérer un props nommé ```title```, qu'il affichera comme texte du bouton.

- appelez deux fois votre component **Button** dans **App**, et assignez une **valeur différente** pour le **props title** pour chaque component, **hello** et **bonjour** par exemple
- -------


## gérer les event
React reprend une des façons d'éxecuter du code javascript lors d'un évènement, comme le click par exemple.

voir https://fr.reactjs.org/docs/handling-events.html pour faire :

- proposez à votre component **Button** de gérer un **nouveau props** nommé **onButtonClick**, qui executera cette fonction si on clique sur le bouton ( grâce à l'attribut **onClick** )
- donnez deux fonctions différentes à executer aux deux Buttons que vous avez déjà écrit précédemment ( ça peut être un alert et un console log par exemple )


## gérer le state :

### Contexte
Le **state** permet notamment de **stocker** un changement de valeurs qui appartiennent à un **component**, c'est notamment nécessaire / un moyen naturel lorsqu'on peut **modifier des valeurs depuis l'UI**, le cas d'excellence étant un **formulaire** et la gestion des valeurs de ses **inputs**, **checkbox** etc

### Instructions 
-------

- deux inputs différents
- un radio
- un checkbox
-------


## gérer la persistance, découvrir le localStorage
- en utilisant le **localStorage**, arrangez-vous pour que votre formulaire **conserve** ses valeurs après avoir **rafraîchi** la page


TP COLOR : utiliser les notions fondamentales ensemble
===
## gérer les props et le state, et les event

- commencez par créer 4 div de 4 couleurs dfférentes
- en faire une 5eme qui prend la couleur choisie quand on clique sur une des 4 div colorées
- votre 5ème div devra garder la dernière couleur choisie lors du **refresh**
- 
:warning: les divs de couleur devront être un component :warning:


TP LIFECYCLE
====

## Ressources 
- [cours OpenClassrooms](https://openclassrooms.com/fr/courses/4664381-realisez-une-application-web-avec-react-js/4664881-apprivoisez-le-cycle-de-vie-des-composants)
- [Documentation de React (fr)](https://fr.reactjs.org/docs/react-component.html#reference)


## Contexte 

Quand une application React est initialisée, le **constructor** de chaque component sont appelés une première fois, et un premier **render** est lancé pour convertir le jsx en html

A chaque fois qu'un component reçoit une **nouvelle valeur** pour un **props**, ou **met à jour son state**, on dit qu'il s'**update**.

Quand un component est détruit ( changement de page par exemple ), on dit qu'il est démonté ( unmounted).

React prévoit différentes méthodes **accessibles uniquement aux component sous forme de classes** pour agir sur es évènements.

Les 5 methodes principales sont : 
- ```constructor``` : à l'initialisation du component
- ```componentDidMount``` : lorsque le component est injecté dans le dom réel.
- ```componentDidUpdate``` : lorsque le component s'update
- ```componentWillUnmount``` : dernière méthode éxecutée avant que le component soit démonté.
- ```render``` : s'occupe de convertir la portion de jsx du component en html ( avec les valeurs de props et/ou state à l'instant T du render )



## Instructions
-----



TP ROUTING
===

## Contexte

Dans une SPA ( single page app), le **routing est géré côté front**, comme en réalité il n'y a qu'une seule page HTML ( index.html).
Le routing sert donc à pouvoir afficher des **components associés à la route choisie** ( ex : /home proposera au component Home de s'afficher, quand /contact chargera Contact, sans rafraichir et ça c'est cool. 
Vous décidez de l'url et du component à lui associé. Ici les noms choisis sont arbitraires, c'est surtout une bonne pratique de garder une cohérence entre le nom de route et le component, ```/toto``` associé à ```<MaVoiture/>``` marchera mais ne sera pas franchement explicite..)

Il n'y a pas de relation directe entre les routes coté front et les routes coté back. Les appels ajax que vous déclencherez s'occuperont de faire ce lien.

Typiquement, la route /profile ( coté front)  chargera le component Profile qui fera peut-être un appel ajax vers /me ( coté serveur ) pour récupérer les infos relatives à mon profil, quand la page /movies qui chargera le component Movies qui appellera en ajax /users/MON_ID/movies




##  Instructions
-------
- ommencez par vous faire la main sur [React-training](https://reacttraining.com/react-router/web/guides/quick-start)
- créer deux routes statiques
- pouvoir naviguer de l'une à l'autre
- dans le component associé à la première route :
  -  ajouter un input, qui permet de setter une value
  - ajouter un bouton qui renvoie vers une route type todos/:value 
- créer la route qui intercepte cette url, le component associé doit afficher la valeur ajoutée dynamiquement dans la route ( ce qui était dans l'input ex : sur /todos/45, le component devra afficher : hey j'ai récupéré 45 commme valeur !)
- au rechargement de l'url, cette valeur doit être toujours affichée ( en la récupérant depuis l'url, via les props disponibles créés par le component Route )
- -----

TP 5
===

##  todo CRUD basé sur le json api 
on aura besoin de deux routes :
- un qui correspond à une page qui :
  - affiche la liste des titres des todos, 
  - affiche un **input** pour créer un nouveau todo ( en appuyant sur le bouton créé, qu'on mettra à coté de l'input)
  -   quand on clique sur un todo item on est envoyé vers une seconde page avec l'id en param ( ex : ```/todos/45```)
- la seconde page est celle du todoItem:
  - le todo item est récupéré **via un nouvel appel ajax**
  - on affiche le titre du todo item dans cette nouvelle page, **via un input**.
  - un bouton **save** sera implanté à coté de l'input, **au click**, il lance un appel ajax pour enregistrer le changement de titre ( vous devrez donc contrôler l'input avec **value** + **onChange** ).
  - au retour de l'**appel ajax**, on effectue une **redirection** vers la page de la liste des todos
  - on ajoute un bouton pour le supprimer : un **appel ajax** pour supprimer l'item en **BDD**, et une **redirection** une fois le job fait
       
