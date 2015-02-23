# Conseil et methodes d'intégration pour but de créer des pages html facilement applicable à drupal

** ce document constitu un guideline. Il est amener à évoluer selon les nouvelles recommendations et outils d'intégrations

## Etat des lieu

2 approches sont utilisés pour la création d'un thème drupal 

**** A. approche classique basé sur une intégration simple html/css/js puis passage à drupal en vue de l'incorporer au theme

== Avantages : 
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

== Inconvenients : 
- phase de developpement plus importante
- besoin de developpeurs lors de l'implémentation des intégrations
- fixer le rendu des hooks aux donnés qu'on veut afficher 
- un va et vient important entre dev et intégrateur
- perte de souplesse d'utilisation du BO de drupal 
- travail en plus pour l'intégrateur/développeur

**** A. approche back office basé sur ce que drupal génère comme rendu pour ses différents composants

== Avantages :
- une rapidité de developpement 
- restitition propre des données en se basant sur un thème générique installé au préalable
- limiter l'intervention des developpeurs sur la partie thème
- va et vient réduit entre dev et intégrateur

== Inconvenients : 
- code html qui n'est pas optimisé (génération de balises et tags innutile)
- phase de maintenance plus importante
- debugage des intégration plus compliqué
- impossible de versionner les intégrations
- se limiter à l'environnement drupal (on ne peux plus utiliser les intégrations sur d'autres plateformes)
- phase de test plus importante et en fin du projet
- phase de SEO en aval
