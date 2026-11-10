# Portfolio2---L-enqu-te-t-l-phonique-qui-souscrit-un-d-p-t-terme

Ce projet de data visualisation et d'analyse de données étudie le comportement des clients d'une banque afin d'identifier les facteurs clés qui influencent la souscription à un dépôt à terme. Il couvre l'intégralité du pipeline de données : de l'extraction et du nettoyage rigoureux via **SQL**, jusqu'à la création d'un tableau de bord interactif sous **Tableau Public**.


##  1. Objectifs du Projet
* **Identifier la cible principale :** Comprendre quel type de profil client (métier, âge, prêts en cours) souscrit le plus aux offres de dépôt à terme.
* **Analyser l'évolution temporelle :** Étudier les variations du taux de souscription et du volume de contacts mois par mois.
* **Croiser les dimensions clés :** Mettre en évidence l'impact des campagnes, de la situation professionnelle, des tranches d'âges et des crédits en cours sur la décision des clients.


##  2. Outils et Technologies Utilisés
* **SQL :** Manipulation, nettoyage, gestion des valeurs manquantes, transformation des variables et requêtes d'agrégation analytiques.
* **Tableau Public :** Création des visualisations graphiques avancées (double axe, barres et lignes) et assemblage du tableau de bord interactif.
* **GitHub :** Versioning, archivage du code SQL et documentation complète du projet.



##  3. Étape par Étape : Préparation, Nettoyage et Requêtes SQL

L'intégralité du traitement des données a été réalisée en amont grâce à des requêtes et scripts SQL structurés de la manière suivante :

### A. Ouverture des données et création d'une vue initiale
* Importation de la table de données brute des clients de la banque (base de données trouvée sur Kaggle :Bank Marketing Campaign || Opening a Term Deposit de Janio Bachmann.
* Création d'une vue de travail de base pour centraliser les données et faciliter les requêtes successives.

### B. Nettoyage des données et transformation des variables
* **Gestion des valeurs manquantes et des valeurs aberrantes :** Identification des lignes incomplètes et traitement de ces dernières.
* **Traitement des "unknown" :** Remplacement systématique des valeurs `unknown` par la mention explicite **« non renseigné »** pour éviter les biais d'interprétation.
* **Binarisation des variables (True/False) :** Transformation des réponses textuelles en valeurs numériques binaires (**1** et **0**) afin de faciliter les calculs statistiques et les taux de conversion.
* **Segmentation par tranches d'âge :** Création d'intervalles d'âges homogènes pour regrouper les clients par catégories (ex: *Moins de 30 ans*, *30-49 ans*, *50 ans et plus*).
* **Assemblage final :** Création d'une vue SQL propre et consolidée (`banque_propre.csv`) servant de socle unique pour l'exportation et l'analyse.

### C. Les 5 Questions Analytiques Clés traitées en SQL
Cinq requêtes SQL spécifiques ont été développées pour répondre aux problématiques métier :
1. **Le calcul global du taux de souscription :** Évaluation de la proportion globale de clients ayant souscrit un dépôt à terme.
2. **Le taux en fonction du métier :** Analyse comparative pour identifier quelles catégories professionnelles convertissent le mieux.
3. **Le taux en fonction de la tranche d'âge :** Mise en évidence de l'appétence au placement selon l'âge du client.
4. **Le taux en fonction du mois de l'année :** Suivi de la saisonnalité et de l'efficacité des campagnes de prospection mensuelles.
5. **L'influence des prêts (prêt immobilier ou autre crédit) :** Étude de l'impact de la présence d'un crédit en cours sur la décision de souscrire un nouveau dépôt à terme.



##  4. Exportation et Visualisations sur Tableau Public

Une fois le jeu de données `banque_propre.csv` exporté, les visualisations suivantes ont été conçues sur Tableau Public :

* **Taux de souscription par mois (Graphique à double axe) :** 
  * Combinaison d'un **diagramme en barres** (pour représenter le volume brut des contacts/appels par mois) et d'une **courbe** (pour suivre précisément l'évolution du taux de souscription en pourcentage au premier plan).
* **Taux par métier (Diagramme en barres horizontales) :** 
  * Classement des professions pour identifier immédiatement les segments les plus performants (mettant en avant des pics notables chez les retraités et les étudiants).
* **Taux par tranche d'âge (Graphique comparatif) :** 
  * Visualisation de la répartition de la conversion selon l'âge, confirmant l'attrait particulier des tranches d'âges extrêmes pour ce type de produit sécurisé.

Voici le lien vers le dashboard de tableau : https://public.tableau.com/authoring/Portfolio2-Enqutesurlesrsultatsdunecampagnetlphonique/Dashboard2#1

##  5. Conception du Tableau de Dashboard
* **Agencement ergonomique :** Organisation des graphiques en format paysage pour optimiser l'espace visuel sans saturer l'écran.
* **Mise en valeur du message clé :** Intégration d'un titre fort orienté métier (*« Qui sont ces 47% de clients qui souscrivent à un dépôt à terme ? »*) pour guider immédiatement la lecture et l'analyse de l'utilisateur.


##  6. Conclusion Générale et Recommandations Métier

### Conclusion générale
L'analyse croisée démontre que la réussite des campagnes de dépôt à terme repose sur deux piliers : un volume de prospects massif chez les jeunes (moins de 30 ans) et un taux de conversion unitaire exceptionnel chez les seniors. De plus, l'efficacité des campagnes varie fortement selon une saisonnalité mensuelle très marquée.

### Recommandations Métier (Chiffres à l'appui)

1. **Stratégie d'acquisition par tranche d'âge :**
   * **Le volume (Moins de 30 ans) :** Conserver la part majoritaire des efforts sur les moins de 30 ans. Bien que leur taux soit de 59,8 %, le volume brut de clients convertis (environ 2 600 personnes) dépasse en quantité absolue les autres segments, ce qui en fait le socle indispensable du portefeuille.
   * **La performance (Seniors / 50 ans et plus) :** Maintenir un ciblage prioritaire sur les seniors, dont le taux de souscription atteint 52 % sur un bassin de 2 600 personnes, générant un volume de conversion extrêmement fort et un retour sur investissement unitaire optimal.

2. **Saisonnalité des campagnes d'appels :**
   * **Les mois forts à privilégier :** Concentrer les efforts de phoning et de prospection commerciale en **mars, mai, août et octobre**. Ce sont ces mois précis qui affichent les pics de taux de souscription les plus élevés de l'année (dépassant par endroit les 80 % à 90 % de réussite selon le profil).
   * **Les mois à éviter :** Réduire drastiquement ou automatiser les campagnes durant les mois creux de l'année (où les taux chutent brutalement autour de 40 %), afin d'éviter le gaspillage d'efforts commerciaux sur des périodes non propices.

3. **Personnalisation selon l'historique de crédit :**
   * Ajuster le discours commercial en tenant compte de l'existence ou non d'un prêt immobilier en cours, variable qui influence directement la capacité et l'envie du client de placer son épargne sur un dépôt à terme.
