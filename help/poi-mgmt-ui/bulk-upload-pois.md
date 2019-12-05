---
title: POI de téléchargement en masse
description: Cette section fournit des informations sur la manière de télécharger en masse vos points d’intérêt.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Téléchargement en masse des points d’intérêt {#bulk-upload-pois}

Un ensemble de scripts Python a été créé afin de simplifier l’importation par lots des points d’intérêt à partir d’un fichier .csv dans une base de données POI à l’aide des API de service Web. Ces scripts peuvent être téléchargés à partir de ce repo [git](https://github.com/adobe/places-scripts)open source.

Avant d’exécuter ces scripts, pour accéder aux API des services Web, voir *Conditions préalables à l’accès* des utilisateurs dans la section Présentation de l’ [intégration et conditions préalables](/help/web-service-api/adobe-i-o-integration.md).

Voici quelques informations sur les scripts :

>[!TIP]
>
>Ces informations sont également incluses dans un fichier Lisez-moi dans le [référentiel](https://github.com/adobe/places-scripts)git.

## Fichier CSV

Un exemple de fichier .csv `places_sample.csv`fait partie de ce package et comprend les en-têtes requis et une ligne d’exemples de données. Ces en-têtes sont tous en minuscules et correspondent aux clés de métadonnées réservées utilisées dans la base de données Places. Les colonnes que vous ajoutez au fichier .csv sont ajoutées à la base de données du point d’accès dans une section de métadonnées distincte pour chaque point d’accès sous forme de paires clé/valeur, et la valeur d’en-tête est utilisée comme clé.

Voici une liste des colonnes et des valeurs à utiliser :

* `lib_id`

   ID de bibliothèque valide obtenu à partir de la base de données d’API.

* `type`

   Le point est actuellement la seule valeur valide.

* `longitude`

   Valeur comprise entre -180 et 180.

* `latitude`

   Valeur comprise entre -85 et 85.

* `radius`

   Valeur comprise entre 10 et 20 000.

### Valeurs de colonne

Les valeurs des colonnes suivantes sont utilisées dans l’interface utilisateur du service d’emplacement :

* color, qui est utilisée comme couleur de la broche qui représente l’emplacement de l’interface utilisateur du service d’emplacement.
   * Les valeurs valides sont "", #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B, #3DC8DE et "".
   * Si la valeur n’est pas renseignée, l’interface utilisateur du service d’emplacement utilise le bleu comme couleur par défaut.

      Les valeurs correspondent au bleu (#3E76D0), au violet (#AA99E8), au fuschia (#DC2ABA), à l’orange (#FC685B), à l’orange clair (#FC962E), au jaune (#F6C436), au vert clair (#BECE5D), au vert (#61B 56B) et bleu clair (#3DC8DE), respectivement.

* qui est utilisée comme icône sur l’épingle représentant l’emplacement de la zone cliquable sur le mappage de l’interface utilisateur du service d’emplacement.

   * Les valeurs valides sont "", boutique, hotelbed, voiture, avion, train, navire, stade, parc d'attraction, ancrage, beaker, cloche, bid, boîte, mallette, fenêtre, navigation, brosse, bâtiment, calculatrice, appareil photo, horloge, éducation, lampe de poche, suivre, jeu, femelle, mâle, cadeau, marteau, coeur, maison, clé, lancement, ampoule, boîte aux lettres, épingle, promouvoir, ruban, panier, étoile, cible, théière, pouceBas, pouceHaut, piège, trophée, clé à molette.

      Les valeurs d’icône sont répertoriées dans l’ordre dans lequel elles apparaissent dans l’illustration suivante :

      ![icônes dans l’interface utilisateur](/help/assets/UI_icons.png)

   * Si la valeur n’est pas renseignée, l’interface utilisateur utilise étoile comme icône par défaut.

* Les colonnes qui ne sont pas mentionnées peuvent rester vides.

## Exécution du script

1. Téléchargez des fichiers depuis le référentiel [git](https://github.com/adobe/places-scripts) vers votre répertoire local.
1. Dans un éditeur de texte, ouvrez le `config.py` fichier et procédez comme suit :

   a. Modifiez les valeurs de variable suivantes en tant que chaînes :

   * `csv_file_path`

      Il s’agit du chemin d’accès à votre `.csv` fichier.

   * `access_code`

      Il s’agit du code d’accès obtenu à partir de l’appel à Adobe IMS. Pour plus d’informations sur la manière d’obtenir ce code d’accès, voir *Conditions requises pour l’accès* des utilisateurs dans Présentation de l’ [intégration et Conditions préalables](/help/web-service-api/adobe-i-o-integration.md).

   * `org_id`

      ID d’organisation Experience Cloud dans lequel les points d’intérêt doivent être importés. Pour plus d’informations sur la manière d’obtenir l’ID d’organisation, voir *Conditions requises pour l’accès* des utilisateurs dans Présentation de l’ [intégration et Conditions préalables](/help/web-service-api/adobe-i-o-integration.md).

   * `api_key`

      Il s’agit de votre clé d’API REST Places obtenue à partir de votre intégration des emplacements d’E/S Adobe. Pour plus d’informations sur la manière d’obtenir la clé d’API, voir *Conditions requises pour l’accès* des utilisateurs dans la présentation de l’ [intégration et les conditions préalables](/help/web-service-api/adobe-i-o-integration.md).
   b. Enregistrez vos modifications.

1. Dans une fenêtre de terminal, accédez au `…/places-scripts/import/` répertoire.
1. Saisissez `python ./places_import.py` et appuyez sur la **[!UICONTROL enter]** (**[!UICONTROL return]**) touche.


## Vérifications CSV préalables à l’importation

Le script effectue initialement les vérifications suivantes sur le fichier .csv :

* Indique si un `.csv` fichier a été spécifié.
* Indique si le chemin d’accès au fichier est valide.
* Précise si les en-têtes de métadonnées réservés sont inclus.

   Les en-têtes de métadonnées réservés sont lib_id, name, description, type, longitude, latitude, rayon, pays, état, ville, rue, catégorie, icône et couleur.

   >[!TIP]
   >
   >Les en-têtes sont tous en minuscules et peuvent être répertoriés dans n’importe quel ordre.

* Vérifie les valeurs des colonnes spécifiées dans la section du fichier CSV.

Si des erreurs sont détectées, le script imprime les erreurs et est abandonné. Si aucune erreur n’est détectée, le script tente d’importer les points d’intérêt par lots de 1 000. Si le lot est importé avec succès, le script signale un code d’état de 200. Si l’importation du lot échoue, des erreurs sont signalées.

## Tests unitaires

Les tests unitaires se trouvent dans le `tests.py` fichier, doivent être exécutés avant chaque demande d’extraction et doivent tous réussir. Des tests supplémentaires doivent être ajoutés avec un nouveau code. Pour exécuter les tests, accédez au `…/places-scripts/import/` répertoire, puis entrez `python ./places_import.py` dans le terminal.
