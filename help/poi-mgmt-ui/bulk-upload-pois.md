---
title: Points ciblés de chargement en masse
description: Cette section fournit des informations sur la manière de charger vos points ciblés en masse.
exl-id: 72704bfc-5837-4439-bdb2-e77ddf935639
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 0%

---

# Chargement en masse de POI {#bulk-upload-pois}

Le **Importation de points ciblés** dans le service Places peut être utilisé pour charger en masse de nouveaux points ciblés à l’aide d’un fichier CSV. Un exemple de modèle de feuille de calcul est fourni pour indiquer quelles colonnes de données sont requises et comment ajouter des métadonnées personnalisées facultatives.

![Écran d’importation en bloc](/help/assets/Bulk-import.png)

Consultez cette vidéo montrant le processus d’importation en bloc et de modification en masse :

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Importation et modification en bloc de points ciblés du service Places](https://www.youtube.com/watch?v=75qVtirsXhg)

## Scripts d’API Python

Un ensemble de scripts Python a été créé pour simplifier l’importation par lots des points ciblés à partir d’un fichier .csv dans une base de données de point ciblé à l’aide des API de service Web. Ces scripts peuvent être téléchargés à partir de ce code open source. [référentiel git](https://github.com/adobe/places-scripts).

Avant d’exécuter ces scripts, pour accéder aux API de service Web, voir *Conditions préalables pour l’accès utilisateur* in [Présentation de l’intégration et conditions préalables](/help/web-service-api/adobe-i-o-integration.md).

Voici quelques informations sur les scripts :

>[!TIP]
>
>Ces informations sont également incluses dans un fichier Lisez-moi dans la variable [référentiel git](https://github.com/adobe/places-scripts).

## fichier CSV

Un exemple de fichier .csv, `places_sample.csv`, fait partie de ce package et inclut les en-têtes requis et une ligne d’exemples de données. Ces en-têtes sont tous en minuscules et correspondent aux clés de métadonnées réservées utilisées dans la base de données Places. Les colonnes que vous ajoutez au fichier .csv seront ajoutées à la base de données du point ciblé dans une section de métadonnées distincte pour chaque point ciblé sous la forme de paires clé/valeur, et la valeur d’en-tête est utilisée comme clé.

Voici une liste des colonnes et des valeurs que vous devez utiliser :

* `lib_id`

   Identifiant de bibliothèque valide obtenu à partir de la base de données du point ciblé.

* `type`

   Le point est actuellement la seule valeur valide.

* `longitude`

   Valeur comprise entre -180 et 180.

* `latitude`

   Valeur comprise entre -85 et 85.

* `radius`

   Valeur comprise entre 10 et 20,000.

### Valeurs de colonne

Les valeurs des colonnes suivantes sont utilisées dans l’interface utilisateur du service Places :

* color, qui sert de couleur de la épingle qui représente l’emplacement du point ciblé dans la carte de l’interface utilisateur de Places Service.
   * Les valeurs valides sont &quot;&quot;, #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B et #3DC8DE, et &quot;&quot;.
   * Si la valeur n’est pas renseignée, l’interface utilisateur du service Places utilise le bleu comme couleur par défaut.

      Les valeurs correspondent respectivement au bleu (#3E76D0), au violet (#AA99E8), au fuschia (#DC2ABA), à l&#39;orange (#FC685B), à l&#39;orange clair (#FC962E), au jaune (#F6C436), au vert clair (#BECE5D), au vert (#61B56B) et au bleu clair (#3DC8DE).

* Icône, utilisée comme icône sur l’épingle qui représente l’emplacement du point ciblé sur la carte de l’interface utilisateur du service Places.

   * Les valeurs valides sont les suivantes : &quot;&quot;, magasin, lit d’hôtel, voiture, avion, train, navire, stade, stade, amusementpark, ancre, beaker, cloche, offre, livre, boîte, mallette, navigateur, brosse, bâtiment, calculatrice, caméra, horloge, éducation, lampe de poche, suivre, jeu, femme, homme, cadeau, marteau, coeur, maison, lancement, ampoule, lampadaire, boîte, argent, argent, promouvoir, ruban, shoppingCart, étoile, cible, théière, thumbDown, thumbUp, piège, trophée, clé à molette.

      Les valeurs des icônes sont répertoriées dans l’ordre dans lequel elles apparaissent dans l’illustration suivante :

      ![icônes dans l’interface utilisateur](/help/assets/UI_icons.png)

   * Si la valeur n’est pas renseignée, l’interface utilisateur utilise l’étoile comme icône par défaut.

* Les colonnes qui ne sont pas mentionnées peuvent être laissées vides.

## Exécution du script

1. Téléchargez des fichiers à partir du [référentiel git](https://github.com/adobe/places-scripts) dans votre répertoire local.
1. Dans un éditeur de texte, ouvrez le `config.py` et effectuez les tâches suivantes :

   a. Modifiez les valeurs de variable suivantes en tant que chaînes :

   * `csv_file_path`

      Il s’agit du chemin d’accès à votre `.csv`  fichier .

   * `access_code`

      Il s’agit de votre code d’accès obtenu à partir de l’appel à Adobe IMS. Pour plus d’informations sur l’obtention de ce code d’accès, voir *Conditions préalables pour l’accès utilisateur* in [Présentation de l’intégration et conditions préalables](/help/web-service-api/adobe-i-o-integration.md).

   * `org_id`

      orgID Experience Cloud dans lequel les points ciblés doivent être importés. Pour plus d’informations sur l’obtention de l’ID d’organisation, voir *Conditions préalables pour l’accès utilisateur* in [Présentation de l’intégration et conditions préalables](/help/web-service-api/adobe-i-o-integration.md).

   * `api_key`

      Il s’agit de votre clé API REST Places obtenue de votre intégration Places Adobe I/O. Pour plus d’informations sur l’obtention de la clé API, voir *Conditions préalables pour l’accès utilisateur* in [Présentation de l’intégration et conditions préalables](/help/web-service-api/adobe-i-o-integration.md).
   b. Enregistrez vos modifications.

1. Dans une fenêtre de terminal, accédez à la `…/places-scripts/import/` répertoire .
1. Entrée `python ./places_import.py` et appuyez sur la touche **[!UICONTROL enter]** (**[!UICONTROL return]**).


## Vérifications CSV de préimportation

Le script effectue initialement les vérifications suivantes sur le fichier .csv :

* Si `.csv` a été spécifié.
* Indique si le chemin d’accès au fichier est valide.
* Si les en-têtes de métadonnées réservés sont inclus.

   Les en-têtes de métadonnées réservés sont lib_id, nom, description, type, longitude, latitude, rayon, pays, état, ville, rue, catégorie, icône et couleur.

   >[!TIP]
   >
   >Les en-têtes sont en minuscules et peuvent être répertoriés dans n’importe quel ordre.

* Vérifie les valeurs des colonnes spécifiées dans la section Fichier CSV.

Si des erreurs sont détectées, le script les imprime et est abandonné. Si aucune erreur n’est trouvée, le script tente d’importer les points ciblés par lots de 1 000. Si le lot est importé avec succès, le script signale un code d’état de 200. Si l’importation du lot échoue, des erreurs sont signalées.

## Tests unitaires

Les tests unitaires se trouvent dans la variable `tests.py` doit être exécuté avant chaque requête de tirage et doit être transmis. Des tests supplémentaires doivent être ajoutés avec un nouveau code. Pour exécuter les tests, accédez au `…/places-scripts/import/` et saisissez `python ./places_import.py` dans le terminal.
