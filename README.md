# Conseil et methodes d'intégration pour but de créer des pages html facilement applicable à drupal

** ce document constitu un guideline. Il est amener à évoluer selon les nouvelles recommendations et outils d'intégrations

## Etat des lieux

2 approches sont utilisés pour la création d'un thème drupal 

### A. approche classique basé sur une intégration simple html/css/js puis passage à drupal en vue de l'incorporer au theme

#### Avantages : 
- avoir un rendu présentable avant la phase de développement
- liberté d'utilisation de balise et de classe css
- facilité de débugage
- code propre et optimal
- limitation des interventions en cas d'evolutions ou de modification du besoin
- developpement js plus souple
- possibilté de versionnage et de log
- phase de maintenance réduite
- phase de SEO en amant 
- réduire la charge de travail du graphiste en déclinants des pages en se basant sur une charte graphique déjà créé

#### Inconvenients : 
- phase de developpement plus importante
- besoin de developpeurs lors de l'implémentation des intégrations
- fixer le rendu des hooks aux donnés qu'on veut afficher 
- un va et vient important entre dev et intégrateur
- perte de souplesse d'utilisation du BO de drupal 
- travail en plus pour l'intégrateur/développeur

### B. approche back office basé sur ce que drupal génère comme rendu pour ses différents composants

#### Avantages :
- une rapidité de developpement 
- restitition propre des données en se basant sur un thème générique installé au préalable
- limiter l'intervention des developpeurs sur la partie thème
- va et vient réduit entre dev et intégrateur

#### Inconvenients : 
- code html qui n'est pas optimisé (génération de balises et tags innutile)
- phase de maintenance plus importante
- debugage des intégration plus compliqué
- impossible de versionner les intégrations
- se limiter à l'environnement drupal (on ne peux plus utiliser les intégrations sur d'autres plateformes)
- phase de test plus importante et en fin du projet
- phase de SEO en aval


## Approche à adopter

En se basant sur l'existant, on se rend compte qu'il n'existe pas d'approche parfaite d'où la nécessité de trouver une solution qui réunit les deux methodes pour tirer le meilleurs parti d'elles.
On va donc utiliser un process d'intégration qui se base sur ces points:

###A Réunion début de projet 
Des réunions seront envisagé avec les devs et chef de projets technique pour donner une lecture technique du projet.
A la fin de ces réunion, on dégagera la strcuture du site (vues, bloc, région, menu...) et on le communiquera à l'intégrateur chargé du découpage des maquette.
Le theme du site sera fixé lors de cette réunion selon les contraintes technique du projet (responsive ou pas).

###B Début d'intégration
L'intégrateur se basera sur le theme installé pour customiser tout les composant graphique  du site (boutons, pagination, lien, titre.... ) via le module "style guide".
Il pourra ainsi récupérer des fichiers LESS ou CSS qu'il va utiliser dans des intégrations statiques

###C intégration statique
Une fois les composants drupal customisé, l'intégrateur attaquera les gabarit et layout des pages indépendament de drupal. Ce ci dit, il n'aura pas toute la liberté pour créer ses balise et class css.

Nous fixons des règles d'integration comme suit :

- L'intégrateur aura toute la liberté de créer les balise/css du gabarit du site. Ces balise seront transporté dans les fichiers html.tpl et pages.tpl
- l'intégrateur se basera sur les elements dégagés lors de la réunion de debut de projet. Ainsi il pourra récupérer et appliquer le code d'un bloc ou d'un vue ...

exemple :

```
<div class="block nom-class-specifique">
   <h2 class="block-title">Titre du bloc</h2>
   <div class="block-content content">
    <p>ce ci est un contenu de test</p>
   </div>
</div> <!-- /.block -->
```
- l'intégrateur appliquera une classe spécifique au bloc et l'utilisara de façon générique dans tout le site et à tout les element du bloc 

exemple :

```
.nom-class-specifique h2 {
    font-size: 2em;
}
.nom-class-specifique .content {
    font-size: 1em;
}
```
- on utilisera LESS comme préprocesseur css
- on se basera sur le guideline css suivant : https://github.com/ymzoughi/cssguidelines
- il sera interdit d'utiliser les id dans la css afin de pouvoir les réutiliser dans d'autres blocs
- il sera interdit de référencer les classes css par rapport au body ou html du site sauf exeption (.front, .no-front,.ie8, lt-ie9...)
- préférer des plugins jquery ustilisé sur d'anciens projets drupal
- le developpeur se chargera d'ajouter les noms des classes spécifiques au différents bloc et régions du site
