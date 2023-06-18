# BI Solution for Telecom Customer Churn

### Technologies utilisées : SQL server management studio, SQL Server Integration Services, Microsoft Visual Studio, Power BI

### 1- Domaine :
Télécommunication.
### 2- Contexte fonctionnel :
Toute entreprise de télécommunication souhaite maximiser le nombre de clients. Pour atteindre cet objectif, il est important non seulement d'essayer d'en attirer de nouveaux, mais aussi de conserver ceux qui existent déjà. Fidéliser un client coûtera moins cher à l'entreprise que d'en attirer un nouveau. De plus, un nouveau client peut être faiblement intéressé par les services aux entreprises et il sera difficile de travailler avec lui, alors que les anciens clients disposent déjà des données nécessaires sur l'interaction avec le service.
#### Besoin d’analyse :
Le besoin de cette étude est de :
• Comprendre les raisons de résiliations des clients pour améliorer la qualité des offres et le service clientèle.
• Analyser, de décrire et de prédire les données liées au désabonnement des clients afin de faire des tableaux de bord analytiques et prévisions à l'avenir pour faciliter la tâche de prise de décision pour la compagnie de télécommunication.
### 3- Jeu de données utilisés :
« IBM Teclo_Churn », Un ensemble de six fichiers Excel qui contiennent les informations sur une société de télécommunication fictive Telco qui a fourni des services de téléphonie résidentielle et Internet à 7043 clients en Californie au troisième trimestre de l’année 2020. Des informations sur les clients désabonnés, restés et ceux qui viennent de s’abonner. D’autres informations démographiques et géographiques importantes sont incluses pour chaque client, le type de contrat, les services choisis, le statut de désabonnement…etc
Et aussi d’autres fichiers, un qui s’agit d’une calendrier de 2020 et l’autre qui contient des données sur tous les Zip Code de Californie.
- Telco_customer_churn_demographics.xlsx
- Telco_customer_churn_location.xlsx
- Telco_customer_churn_location.xlsx
- Telco_customer_churn_population.xlsx
- Telco_customer_churn_services.xlsx
- Telco_customer_churn_status.xlsx
- DimDates.xlsx
- Zipcode.xlsx


## Indicateurs clé de performance – KPIs :
#### Description des axes de l’analyse :
![image](https://github.com/EL-MEHDI-git/Business-intelligence-project-report/assets/66147690/1cbd8bfa-2376-439b-93cb-1c02158575a9)

#### Matrice dimensionnelle d'analyse des indicateurs:

![image](https://github.com/EL-MEHDI-git/Business-intelligence-project-report/assets/66147690/ca4c9434-0859-4654-abbc-eadac285ac18)

## Modélisation du datawarehouse :
Dans cette partie du projet, nous mettrons en oeuvre l'entrepôt de données, en utilisant le schéma en étoile, qui est l'approche la plus utilisée pour développer des entrepôts de données, il se compose d'une table de faits faisant référence à un certain nombre de table de dimension.
Notre entrepôt de données va contenir un table de fait ‘’Churn’’, et quatre dimensions :
DimDates, DimCustomers, DimService et finalement DimLocalisation.
Les attributs de chaque table sont représentés sur le schéma ci-dessous :
![image](https://github.com/EL-MEHDI-git/Business-intelligence-project-report/assets/66147690/4071f52c-bdab-43dc-b9ec-f2df6b1a61ce)

### ETL :
Extract, Transform, Load est la procédure générale de copier des données d'un ou de plusieurs sources dans un système de destination qui représente les données différemment des source ou dans un contexte différent de la source. Dans ce projet, nous extrairons les données des fichiers plats ci-dessous, et chargez-les dans ‘’ChurnDW’’ Datawarehouse créé
sur SQL Server Management Studio (SSMS), nous devons remplir les quatre dimensions ainsi que la table des faits, pour ce faire nous utiliserons SQL Server Data Tools (SSDT).
#### • La dimension Client :
Pour remplir cette dimension, on va fusionner les fichiers plats par des jointures et par la suite effectuer une conversion de données pour les rendre compatible avec ceux définies sur la base de données sur Management Studio.
![image](https://github.com/EL-MEHDI-git/Business-intelligence-project-report/assets/66147690/dcea5908-b108-4a11-93b2-a8cf7b2a4cb2)
#### • La dimension Date:
![image](https://github.com/EL-MEHDI-git/Business-intelligence-project-report/assets/66147690/60983160-60ec-4897-afec-886409b943e4)

#### • La dimension Localisation:
![image](https://github.com/EL-MEHDI-git/Business-intelligence-project-report/assets/66147690/924c1212-f6bb-411e-adf5-5de9e2db06a5)

#### • La dimension Service:
![image](https://github.com/EL-MEHDI-git/Business-intelligence-project-report/assets/66147690/725f2538-23fa-4959-b20c-5f4fe4b030b6)

#### • Table de fait [ Churn ] :
##### Requête dans Source OLE DB :
![image](https://github.com/EL-MEHDI-git/Business-intelligence-project-report/assets/66147690/0b0c2fee-05e5-4547-8761-c7c9c63fbc79)

## Python : Visualisation et Analyse:
On exporte la table de fait réalisé sous la format CSV afin d’effectuer une analyse descriptive et prédictive qui vise à explorer et comprendre l’ensemble de données, les raisons de désabonnement et réaliser un modèle prédictif d’attrition des clients.
![image](https://github.com/EL-MEHDI-git/Business-intelligence-project-report/assets/66147690/bf5d2e3b-0e87-4eba-a094-0e7b66dbaae6)

#### • Analyse prédictive:
Dans la dernière partie du projet, nous mettrons en oeuvre des solutions prédictives pour la compagnies Telco afin d'explorer les modèles en analysant les faits actuels et historiques et faire des prédictions sur la situation des futurs clients.
Après le pré-traitement et la normalisation des données, on détermine la corrélation entre variables :
![image](https://github.com/EL-MEHDI-git/Business-intelligence-project-report/assets/66147690/dabcf909-5a28-476a-b257-0ee6f012d995)

On choisit les variables les plus corrélées avec la variable cible en utilisant le SelectKBest avec un test Chi-square.
![image](https://github.com/EL-MEHDI-git/Business-intelligence-project-report/assets/66147690/1d05c76a-1dd7-4928-9d0c-e201b5d2a3f0)

![image](https://github.com/EL-MEHDI-git/Business-intelligence-project-report/assets/66147690/eb0975a7-1950-488a-bcb5-ac9905fbca47)
En affichant le rapport de classification, on remarque que le modèle implémenté effectue de bonne prédiction et avait de bonne score au niveau de tous les métriques d’évaluation.

### Conclusion
La prise de décision est un rôle clé dans le succès de toute entreprise, ces décisions affectent directement l'entreprise, et donc une mauvaise décision par une source mal informée conduit à des résultats désastreux. Les décisions sont prises au niveau individuel jusqu'au niveau organisationnel. Cette solution BI que nous avons mise en place améliorera sûrement la décisions prises par les dirigeants de la compagnie Telco. Les systèmes de BI permettront en effet tous les gestionnaires de la compagnie Telco avec suffisamment d'informations et les rendre capables de la prise de décision.


## Analyse et Reporting:
![image](https://github.com/EL-MEHDI-git/Business-intelligence-project-report/assets/66147690/48806562-8027-4ea7-bf5e-938efd68236f)
![image](https://github.com/EL-MEHDI-git/Business-intelligence-project-report/assets/66147690/549ba2ea-f42c-4f59-b5fb-fe6be0b8fc77)


