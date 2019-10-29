---
title: Utilisation de lieux avec Mobile Services pour la messagerie
seo-title: Utilisation de lieux avec Mobile Services pour la messagerie
description: Cette section explique comment utiliser Places avec Mobile Services pour la messagerie.
seo-description: Cette section explique comment utiliser Places avec Mobile Services pour la messagerie.
translation-type: tm+mt
source-git-commit: accfa6ba009ad3419481d9bd3b498143228099fc

---


# Adobe Mobile Services {#places-mobile-services}

Avant d’utiliser l’extension Mobile Services pour la messagerie, vérifiez les conditions préalables suivantes :

* Des points d’intérêt ont été créés dans le service d’emplacement. Si nécessaire, voir Documentation. (lien vers la création d’un point d’accès) Remarque : Le service d’emplacement comprend une nouvelle base de données de points d’intérêt améliorée pour votre entreprise qui existe en dehors de l’interface AMS héritée. Les points d’intérêt trouvés dans la navigation "Gérer les lieux" d’AMS ne fonctionneront que pour la version 4 du SDK.
   * Voici l’interface héritée de gestion des points d’accès aux emplacements dans AMS pour les anciennes versions du SDK :

      ![Interface utilisateur héritée](/help/assets/legacy-location-v4-ui.png)

   * Voici l’interface de gestion des points d’accès du service d’emplacement :

      ![Interface utilisateur de gestion des points d’accès du service Emplacement](/help/assets/places-ui.png)

* Le SDK ACP est correctement configuré avec les extensions Places et/ou Places Monitor. Cela signifie que les données sont disponibles en tant qu’événements et/ou conditions dans le moteur des règles de lancement pour votre application mobile. Consultez la documentation si nécessaire. (https://aep-sdks.gitbook.io/docs/beta/adobe-places)

* Familiarisez-vous avec la création et la publication de règles de lancement dans le SDK ACP dans votre application mobile. Consultez la documentation si nécessaire. (https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine)

* Les éléments de données de lancement sont créés à partir des données d’extension Places SDK qui seront utilisées dans les règles. Voir la documentation (https://aep-sdks.gitbook.io/docs/using-mobile-extensions/mobile-core/rules-engine#data-elements).

## Création de rapports

Avant d’utiliser les rapports, remplissez les conditions préalables suivantes :

* Envoi réussi des données du service d’emplacement dans la suite de rapports Adobe Analytics. Si nécessaire, consultez la documentation d’Adobe Analytics (lien vers les documents de Steve).
* Familier avec les rapports AMS. Veuillez consulter la documentation si nécessaire (https://docs.adobe.com/content/help/en/mobile-services/using/reports-ug/usage.html).

## Visualisation des rapports

Vous pouvez exécuter des rapports AMS à l’aide des données du service d’emplacement envoyées à Adobe Analytics. Par exemple, j’ai envoyé des événements lorsque des utilisateurs ont des entrées dans l’une de mes API. Dans ce rapport, j’ai ajouté un filtre de l’événement d’entrée d’API en plus de mon rapport utilisateur prêt à l’emploi :

![Visualisation des rapports](/help/assets/report-visualize.png)

Une plus grande flexibilité dans la visualisation des données du service d’emplacement est disponible dans les interfaces Adobe Analytics.

