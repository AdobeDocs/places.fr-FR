---
title: POI de téléchargement en masse
description: Cette section fournit des informations sur la manière de télécharger en masse vos points d’intérêt.
translation-type: tm+mt
source-git-commit: 462df20bb351795dc72009cc18d390cb45e262a8
workflow-type: tm+mt
source-wordcount: '861'
ht-degree: 0%

---


# Chargement en masse des points d’intérêt {#bulk-upload-pois}

Le bouton **Importer les points d’intérêt** du service Lieux peut être utilisé pour charger en masse les nouveaux points d’intérêt à l’aide d’un fichier CSV. Un exemple de modèle de feuille de calcul est fourni pour indiquer les colonnes de données requises et comment ajouter des métadonnées personnalisées facultatives.

![Écran d&#39;importation en masse](/help/assets/Bulk-import.png)

Cette vidéo présente le processus d&#39;importation en masse et de modification en masse :

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Importation et modification en masse des points d’intérêt de service](https://www.youtube.com/watch?v=75qVtirsXhg)

## Scripts d&#39;API Python

Un ensemble de scripts Python a été créé pour simplifier l&#39;importation par lots des points d&#39;intérêt à partir d&#39;un fichier .csv dans une base de données POI à l&#39;aide des API de service Web. Ces scripts peuvent être téléchargés à partir de ce [git repo](https://github.com/adobe/places-scripts) open source.

Avant d’exécuter ces scripts, pour accéder aux API de service Web, voir *Conditions préalables pour l’accès des utilisateurs* dans [Présentation de l’intégration et conditions préalables](/help/web-service-api/adobe-i-o-integration.md).

Voici quelques informations sur les scripts :

>[!TIP]
>
>Ces informations sont également incluses dans un fichier lisez-moi dans le [réf. git](https://github.com/adobe/places-scripts).

## Fichier CSV

Un exemple de fichier .csv, `places_sample.csv`, fait partie de ce package et comprend les en-têtes requis et une ligne d’exemples de données. Ces en-têtes sont tous en minuscules et correspondent aux clés de métadonnées réservées utilisées dans la base de données Places. Les colonnes que vous ajoutez au fichier .csv sont ajoutées à la base de données du point d’accès (POI) dans une section de métadonnées distincte pour chaque point d’accès (POI) en tant que paires clé/valeur et la valeur d’en-tête est utilisée comme clé.

Voici une liste des colonnes et des valeurs que vous devez utiliser :

* `lib_id`

   Identifiant de bibliothèque valide obtenu à partir de la base de données d’API.

* `type`

   Le point est actuellement la seule valeur valide.

* `longitude`

   Valeur comprise entre -180 et 180.

* `latitude`

   Valeur comprise entre -85 et 85.

* `radius`

   Valeur comprise entre 10 et 20 000.

### Valeurs de colonne

Les valeurs des colonnes suivantes sont utilisées dans l’interface utilisateur du service Lieux :

* color, qui est utilisée comme couleur de la broche qui représente l’emplacement du point d’accès dans la carte d’interface utilisateur du service Places.
   * Les valeurs valides sont &quot;&quot;, #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B, #3DC8DE et &quot;&quot;.
   * Si la valeur n’est pas renseignée, l’interface utilisateur du service des emplacements utilise le bleu comme couleur par défaut.

      Les valeurs correspondent au bleu (#3E76D0), au violet (#AA99E8), au fuschia (#DC2ABA), à l’orange (#FC685B), à l’orange clair (#FC962E), au jaune (#F6C436), au vert clair (#BECE5D), au vert (#61B1B). 56B), et bleu clair (#3DC8DE), respectivement.

* qui sert d’icône sur la broche représentant l’emplacement de la POI sur la carte d’interface utilisateur du service Places.

   * Les valeurs valides sont &quot;&quot;, boutique, hotelbed, voiture, avion, train, navire, stade, stade, parc d&#39;attraction, ancrage, beaker, bell, bid, livre, boîte, mallette, navigateur, brosse, bâtiment, calculatrice, caméra, horloge, éducation, lampe de poche, suivre, jeu, femme, homme, cadeau, marteau, coeur, maison, clé, lancement, ampoule, boîte aux lettres, épingle, promouvoir, ruban, shoppingCart, étoile, cible, théière, pouceDown, pouceUp, piège, trophée, clé à molette.

      Les valeurs d’icône sont répertoriées dans l’ordre dans lequel elles apparaissent dans l’illustration suivante :

      ![icônes dans l’interface utilisateur](/help/assets/UI_icons.png)

   * Si la valeur n’est pas renseignée, l’interface utilisateur utilise l’étoile comme icône par défaut.

* Les colonnes qui ne sont pas mentionnées peuvent rester vides.

## Exécution du script

1. Téléchargez des fichiers de [git repo](https://github.com/adobe/places-scripts) vers votre répertoire local.
1. Dans un éditeur de texte, ouvrez le fichier `config.py` et effectuez les tâches suivantes :

   a. Modifiez les valeurs de variable suivantes en tant que chaînes :

   * `csv_file_path`

      Il s&#39;agit du chemin d&#39;accès à votre fichier `.csv`.

   * `access_code`

      Il s&#39;agit de votre code d&#39;accès obtenu à partir de l&#39;appel à l&#39;Adobe IMS. Pour plus d&#39;informations sur la façon d&#39;obtenir ce code d&#39;accès, voir *Conditions préalables requises pour l&#39;accès utilisateur* dans [Présentation de l&#39;intégration et conditions préalables](/help/web-service-api/adobe-i-o-integration.md).

   * `org_id`

      orgID Experience Cloud dans lequel les points d’intérêt doivent être importés. Pour plus d’informations sur la manière d’obtenir l’ID d’organisation, voir *Conditions préalables pour l’accès utilisateur* dans [Présentation de l’intégration et conditions préalables](/help/web-service-api/adobe-i-o-integration.md).

   * `api_key`

      Il s’agit de votre clé d’API REST Places obtenue à partir de votre intégration Adobe I/O Places. Pour plus d&#39;informations sur la façon d&#39;obtenir la clé d&#39;API, voir *Conditions préalables requises pour l&#39;accès utilisateur* dans [Présentation de l&#39;intégration et conditions préalables](/help/web-service-api/adobe-i-o-integration.md).
   b. Enregistrez vos modifications.

1. Dans une fenêtre de terminal, accédez au répertoire `…/places-scripts/import/`.
1. Saisissez `python ./places_import.py` et appuyez sur la touche **[!UICONTROL enter]** (**[!UICONTROL return]**).


## Vérifications CSV préalables à l’importation

Le script effectue initialement les vérifications suivantes sur le fichier .csv :

* Indique si un fichier `.csv` a été spécifié.
* Indique si le chemin d’accès au fichier est valide.
* Précise si les en-têtes de métadonnées réservés sont inclus.

   Les en-têtes de métadonnées réservés sont lib_id, name, description, type, longitude, latitude, rayon, pays, état, ville, rue, catégorie, icône et couleur.

   >[!TIP]
   >
   >Les en-têtes sont tous en minuscules et peuvent être répertoriés dans n’importe quel ordre.

* Vérifie les valeurs des colonnes spécifiées dans la section de fichier CSV.

Si des erreurs sont détectées, le script imprime les erreurs et est abandonné. Si aucune erreur n’est détectée, le script tente d’importer les points d’intérêt par lots de 1 000. Si le lot est importé avec succès, le script signale un code d’état de 200. Si l’importation du lot échoue, des erreurs sont signalées.

## Tests unitaires

Les tests unitaires se trouvent dans le fichier `tests.py`, doivent être exécutés avant chaque demande d&#39;extraction et doivent tous réussir. Des tests supplémentaires doivent être ajoutés avec un nouveau code. Pour exécuter les tests, accédez au répertoire `…/places-scripts/import/`, puis saisissez `python ./places_import.py` dans le terminal.
