---
title: POI de téléchargement en masse
seo-title: POI de téléchargement en masse
description: Cette section fournit des informations sur la manière de télécharger en masse vos points d’intérêt.
seo-description: Cette section fournit des informations sur la manière de télécharger en masse vos points d’intérêt.
translation-type: tm+mt
source-git-commit: 3a9653dcc7f5d18b717c4bb59424b8cad7104dd7

---


# Téléchargement en masse des points d’intérêt {#bulk-upload-pois}

Un ensemble de scripts Python a été créé afin de simplifier l’importation par lots des points d’intérêt à partir d’un fichier .csv dans une base de données POI à l’aide des API de service Web. Ces scripts peuvent être téléchargés à partir de ce repo [git](https://github.com/adobe/places-scripts)open source.

Avant d’exécuter ces scripts, pour vous assurer que vous avez accès aux API des services Web, voir *Conditions préalables à l’accès* des utilisateurs dans la présentation [de l’intégration des E/S](/help/web-service-api/adobe-i-o-integration.md)Adobe.

Voici quelques informations sur les scripts :

>[!TIP]
>
>Ces informations sont également incluses dans un fichier Lisez-moi dans le [référentiel](https://github.com/adobe/places-scripts)git.

## Fichier CSV

Un exemple de fichier .csv `places_sample.csv`fait partie de ce package et comprend les en-têtes requis et une ligne d’exemples de données. Ces en-têtes sont tous en minuscules et correspondent aux clés de métadonnées réservées utilisées dans la base de données Places. Lorsque vous ajoutez des en-têtes, les colonnes supplémentaires sont ajoutées à la base de données du point d’accès dans une section de métadonnées distincte pour chaque point d’accès sous forme de paires clé/valeur.

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

   Valeur comprise entre 10 et 2000.

### Valeurs de colonne

Les valeurs des colonnes suivantes sont utilisées dans l’interface utilisateur du service d’emplacement :

* color, qui est utilisée comme couleur de la broche qui représente l’emplacement de l’interface utilisateur du service d’emplacement.
   * Les valeurs valides sont "", #3E76D0, #AA99E8, #DC2ABA, #FC685B, #FC962E, #F6C436, #BECE5D, #61B56B et #3DC8DE.
   * Si la valeur n’est pas renseignée, l’interface utilisateur du service d’emplacement utilise le bleu comme couleur par défaut.

      Les valeurs correspondent respectivement au bleu, au violet, au fuschia, à l’orange, au jaune, au vert clair, au vert foncé et au bleu clair.

* qui est utilisée comme icône sur l’épingle représentant l’emplacement de la zone cliquable sur le mappage de l’interface utilisateur du service d’emplacement.
   * Les valeurs valides sont "", anchor, beaker, bell, browse, book, brush, building, building, calculateur, appareil photo, shoppingCart, clock, box, flashlight, continue, bid, ruban, éducation, marteau, coeur, maison, clé, boîte aux lettres, mâle, promotion, argent, jeu, cadeau, lancement, étoile, ampoule, pin, cible, théière, thumbDown, umbUp, mallette, trophée, femelle et clé à molette.
   * Si la valeur n’est pas renseignée, l’interface utilisateur utilise étoile comme icône par défaut.

* Les colonnes qui ne sont pas mentionnées peuvent rester vides.

## Exécution du script

1. Téléchargez les fichiers dans le répertoire approprié.
1. Dans un éditeur de texte, ouvrez le `config.py` fichier et procédez comme suit :

   a. Modifiez les valeurs de variable suivantes en tant que chaînes :

   * `csv_file_path`

      Chemin d’accès à votre `.csv` fichier.

   * `access_code`

      Il s’agit du code d’accès obtenu à partir de l’appel à Adobe IMS.

   * `org_id`

      ID d’organisation Experience Cloud dans lequel les points d’intérêt doivent être importés.

   * `api_key`

      Il s’agit de la clé de l’API REST Places qui a été obtenue à partir de votre intégration des emplacements d’E/S Adobe.
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



