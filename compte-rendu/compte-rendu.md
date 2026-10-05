# Compte-rendu — TP Vue.js : Créer un quiz en images

## 1. Présentation du projet

Dans ce travail pratique, j’ai réalisé une application web de quiz en images avec **Vue.js 3**.

L’objectif est de créer un quiz simple et interactif permettant à l’utilisateur de répondre à plusieurs questions, de suivre sa progression et d’obtenir son score final.

Le quiz contient **5 questions**, chaque question étant associée à une image et à **3 propositions de réponse**.

---

## 2. Technologies utilisées

Pour réaliser ce projet, j’ai utilisé :

* **Vue.js 3**
* **JavaScript**
* **HTML**
* **CSS**
* **Vite**
* **Visual Studio Code**
* **Git et GitHub**

Le projet utilise Vue.js pour gérer l’affichage, les réponses, le score et la progression du quiz.

---

## 3. Structure du projet

Le projet est organisé principalement comme suit :

```text
Vue-Quizz/
│
├── public/
│   └── images/
│       ├── carre.jpg
│       ├── cercle.jpg
│       ├── etoile.jpg
│       ├── rectangle.jpg
│       └── triangle.jpg
│
├── src/
│   └── App.vue
│
├── compte-rendu/
│   └── compte-rendu.md
│
├── package.json
└── README.md
```

Les images utilisées dans le quiz sont stockées localement dans le dossier `public/images`.

---

## 4. Fonctionnement de l’application

Au lancement de l’application, la première question est affichée avec :

* le titre du quiz ;
* le score actuel ;
* la progression ;
* l’image de la question ;
* la question ;
* trois boutons de réponse.

L’utilisateur doit choisir une réponse avant de pouvoir passer à la question suivante.

Lorsqu’une réponse est sélectionnée, elle est immédiatement vérifiée.

Si la réponse est correcte, le score augmente de **1 point**.

Si la réponse est incorrecte, le score reste inchangé.

Dans les deux cas, la progression augmente car la question a été répondue.

---

## 5. Gestion du score et de la progression

Le score est calculé sur un total de **5 points**.

La progression indique le nombre de questions déjà répondues.

Par exemple :

```text
0/5
1/5
2/5
3/5
4/5
5/5
```

La progression ne dépend donc pas du nombre de bonnes réponses, mais du nombre de questions auxquelles l’utilisateur a répondu.

Après avoir répondu à une question, les trois boutons sont désactivés afin d’éviter plusieurs réponses pour la même question.

---

## 6. Passage entre les questions

Après avoir répondu, l’utilisateur peut cliquer sur le bouton **« Question suivante »**.

Pour la dernière question, le bouton permet d’afficher le résultat final.

Après les cinq questions, l’application affiche :

* le score obtenu sur 5 ;
* un message correspondant au résultat ;
* le bouton **« Rejouer »**.

Le bouton « Rejouer » permet de recommencer le quiz depuis la première question avec un score et une progression remis à zéro.

---

## 7. Gestion des données dans Vue.js

Les questions sont stockées dans un tableau JavaScript.

Chaque question contient notamment :

* le texte de la question ;
* le chemin de l’image ;
* les trois choix ;
* la bonne réponse ;
* une description de l’image.

L’application utilise également plusieurs variables pour gérer l’état du quiz, notamment :

* `indexQuestion`
* `score`
* `reponseChoisie`
* `termine`

Des méthodes permettent ensuite de gérer les réponses, le passage à la question suivante et le redémarrage du quiz.

---

## 8. Interface et affichage

L’interface a été réalisée avec HTML et CSS.

Les images sont affichées sans être déformées grâce à l’utilisation de `object-fit: contain`.

L’application utilise également des textes alternatifs avec l’attribut `alt` afin d'améliorer l’accessibilité des images.

Le style a été adapté pour permettre une utilisation plus confortable sur différents écrans, notamment sur mobile.

---

## 9. Tests réalisés

Plusieurs tests ont été effectués pour vérifier le fonctionnement de l’application :

* lancement d’une nouvelle partie ;
* sélection d’une bonne réponse ;
* sélection d’une mauvaise réponse ;
* vérification de l’augmentation du score ;
* vérification de la progression ;
* vérification du blocage des boutons après une réponse ;
* passage à la question suivante ;
* test avec toutes les bonnes réponses ;
* test avec toutes les mauvaises réponses ;
* test avec des réponses mélangées ;
* affichage du résultat final ;
* utilisation du bouton « Rejouer ».

Les fonctionnalités principales du quiz ont été testées avec succès.

---

## 10. Versionnement avec GitHub

Le projet a également été versionné avec **Git** et publié sur **GitHub**.

Le dépôt du projet est :

`https://github.com/talbi-elyes-1/Vue-Quizz`

Cette étape permet de conserver le projet en ligne et de faciliter sa consultation et son partage.

---

## 11. Conclusion

Ce travail pratique m’a permis de mettre en pratique plusieurs notions de Vue.js 3, notamment la gestion des données, les conditions, les boucles, les événements et la mise à jour dynamique de l’interface.

J’ai également appris à organiser un projet Vue.js, à utiliser des ressources locales comme les images et à versionner le projet avec Git et GitHub.

Le quiz final permet de répondre aux cinq questions, de suivre la progression, de calculer le score et de recommencer une partie.
