---
title: Chargement en masse de POI
description: Cette section fournit des informations sur la manière de charger en bloc vos points d’intérêt.
exl-id: 72704bfc-5837-4439-bdb2-e77ddf935639
TQID: https://experienceleague.adobe.com/FVZzn3FwSAFgnRBjkiFwHG8Zl2I-I4fPrqax-zGNclk
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
  - id: f002a92a-b99f-47a4-90c8-65e0e415bc7a
feature_v2:
  - id: bef6f891-2e8a-425e-8f99-7ddf22070daa
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 854
ht-degree: 0%

---

# Chargement en masse des points d’intérêt {#bulk-upload-pois}

Le bouton **Importer des POI** du service Places permet de charger en masse de nouveaux POI à l’aide d’un fichier CSV. Un exemple de modèle de feuille de calcul est fourni pour indiquer les colonnes de données requises et comment ajouter des métadonnées personnalisées facultatives.

![Écran Importer en bloc](/help/assets/Bulk-import.png)

Regardez cette vidéo présentant le processus d’importation et de modification en bloc :

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Importation et modification en bloc des points d’intérêt du service Places](https://www.youtube.com/watch?v=75qVtirsXhg)

## Scripts d&#39;API Python

Un ensemble de scripts Python a été créé pour simplifier l’importation par lots de POI d’un fichier .csv dans une base de données de POI à l’aide des API de service web. Ces scripts peuvent être téléchargés à partir de ce référentiel open source [git](https://github.com/adobe/places-scripts).

Avant d’exécuter ces scripts, pour accéder aux API de service web, consultez *Conditions préalables pour l’accès utilisateur* dans [Présentation de l’intégration et conditions préalables](/help/web-service-api/adobe-i-o-integration.md).

Voici quelques informations sur les scripts :

>[!TIP]
>
>Ces informations sont également incluses dans un fichier Lisez-moi dans le [référentiel git](https://github.com/adobe/places-scripts).

## Fichier CSV

Un exemple de fichier .csv, `places_sample.csv`, fait partie de ce package et comprend les en-têtes requis et une ligne de données d’exemple. Ces en-têtes sont tous en minuscules et correspondent aux clés de métadonnées réservées utilisées dans la base de données Places. Les colonnes que vous ajoutez au fichier .csv sont ajoutées à la base de données de POI dans une section de métadonnées distincte pour chaque POI en tant que paires clé/valeur, et la valeur de l’en-tête est utilisée comme clé.

Voici une liste des colonnes et des valeurs que vous devez utiliser :

* `lib_id`

  Identifiant de bibliothèque valide obtenu à partir de la base de données du point d’intérêt.

* `type`

  Point est actuellement la seule valeur valide.

* `longitude`

  Valeur comprise entre -180 et 180.

* `latitude`

  Valeur comprise entre -85 et 85.

* `radius`

  Valeur comprise entre 10 et 20 000.

### Valeurs de colonne

Les valeurs des colonnes suivantes sont utilisées dans l’interface utilisateur de Places Service :

* la couleur, qui est utilisée comme couleur de l’épingle qui représente l’emplacement du point d’intérêt dans la carte de l’interface utilisateur de Places Service.
   * Les valeurs valides sont les suivantes : «  », #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B et #3DC8DE, et «  ».
   * Si la valeur n’est pas renseignée, l’interface utilisateur du service Places utilise le bleu comme couleur par défaut.

     Les valeurs correspondent respectivement au bleu (#3E76D0), au violet (#AA99E8), au fuschia (#DC2ABA), à l&#39;orange (#FC685B), à l&#39;orange clair (#FC962E), au jaune (#F6C436), au vert clair (#BECE5D), au vert (#61B56B) et au bleu clair (#3DC8DE).

* icône, utilisée comme icône sur l’épingle représentant l’emplacement du point d’intérêt sur la carte de l’interface utilisateur de Places Service.

   * Les valeurs valides sont les suivantes : «  », shop, hotelbed, car, airplane, train, bateau, stade, parc d&#39;attractions, ancre, bécher, cloche, enchère, livre, boîte, porte-documents, parcourir, brosse, bâtiment, calculatrice, caméra, horloge, éducation, lampe de poche, suivre, jeu, femme, masculin, cadeau, marteau, cœur, accueil, clé, lancement, ampoule, boîte aux lettres, argent, épingle, promouvoir, ruban, panier, étoile, cible, théière, pouceDown, pouceDown, piège, trophée, clé, clé à clé, clé à main, clé à main, clé à main.

     Les valeurs des icônes sont répertoriées dans l’ordre dans lequel elles apparaissent dans l’illustration suivante :

     ![icônes de l’interface utilisateur](/help/assets/UI_icons.png)

   * Si cette valeur n’est pas renseignée, l’interface utilisateur utilise étoile comme icône par défaut.

* Les colonnes qui ne sont pas mentionnées peuvent être laissées vides.

## Exécution du script

1. Téléchargez les fichiers du [référentiel git](https://github.com/adobe/places-scripts) dans votre répertoire local.
1. Dans un éditeur de texte, ouvrez le fichier `config.py` et effectuez les tâches suivantes :

   a. Modifiez les valeurs de variable suivantes en tant que chaînes :

   * `csv_file_path`

     Il s’agit du chemin d’accès au fichier `.csv`.

   * `access_code`

     Il s’agit de votre code d’accès obtenu à partir de l’appel à Adobe IMS. Pour plus d’informations sur la manière d’obtenir ce code d’accès, consultez *Conditions préalables pour l’accès utilisateur* dans [Présentation de l’intégration et conditions préalables](/help/web-service-api/adobe-i-o-integration.md).

   * `org_id`

     OrgID Experience Cloud dans lequel les points d’intérêt doivent être importés. Pour plus d’informations sur l’obtention de l’ID d’organisation, voir *Conditions préalables pour l’accès utilisateur* dans [Présentation de l’intégration et conditions préalables](/help/web-service-api/adobe-i-o-integration.md).

   * `api_key`

     Il s’agit de la clé API REST Places obtenue à partir de votre intégration Adobe I/O Places. Pour plus d’informations sur l’obtention de la clé API, voir *Conditions préalables pour l’accès utilisateur* dans [Présentation de l’intégration et conditions préalables](/help/web-service-api/adobe-i-o-integration.md).

   b. Enregistrez vos modifications.

1. Dans une fenêtre de terminal, accédez au répertoire `…/places-scripts/import/` .
1. Saisissez `python ./places_import.py` et appuyez sur la touche **[!UICONTROL entrée]** (**[!UICONTROL retour]**).


## Contrôles CSV de pré-importation

Le script effectue initialement les vérifications suivantes sur le fichier .csv :

* Indique si un fichier `.csv` a été spécifié.
* Indique si le chemin d’accès au fichier est valide.
* Indique si les en-têtes de métadonnées réservés sont inclus.

  Les en-têtes de métadonnées réservés sont lib_id, name, description, type, longitude, latitude, radius, country, state, city, street, category, icon et color.

  >[!TIP]
  >
  >Les en-têtes sont tous en minuscules et peuvent être répertoriés dans n’importe quel ordre.

* Vérifie les valeurs des colonnes spécifiées dans la section du fichier CSV.

Si des erreurs sont détectées, le script les imprime et est abandonné. Si aucune erreur n’est trouvée, le script tente d’importer les POI par lots de 1 000. Si l’importation du lot réussit, le script indique un code d’état de 200. Si l’importation du lot échoue, des erreurs sont signalées.

## Tests unitaires

Les tests unitaires se trouvent dans le fichier `tests.py`, doivent être exécutés avant chaque demande d’extraction et doivent tous réussir. Des tests supplémentaires doivent être ajoutés avec le nouveau code. Pour exécuter les tests, accédez au répertoire `…/places-scripts/import/` et saisissez `python ./places_import.py` dans le terminal.
