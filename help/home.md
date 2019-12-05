---
title: Adobe Experience Platform Location Service
seo-title: Adobe Experience Platform Location Service
description: 'Le service d’emplacement est un contexte important pour comprendre l’engagement des utilisateurs mobiles. En utilisant ce contexte, les développeurs d’applications mobiles peuvent améliorer la conception de l’application et en faire une expérience plus personnalisée et plus attrayante. '
seo-description: 'Le service d’emplacement est un contexte important pour comprendre l’engagement des utilisateurs mobiles. En utilisant ce contexte, les développeurs d’applications mobiles peuvent améliorer la conception de l’application et en faire une expérience plus personnalisée et plus attrayante. '
translation-type: tm+mt
source-git-commit: ecb059400d9203884faab6fd2f627251eeaeea38

---


# Présentation du service d’emplacement d’Adobe Experience Platform {#home}

!["Adobe Experience Platform Location Service"](/help/assets/LocationHeader.png)

L’emplacement est un contexte important pour comprendre et interagir avec les utilisateurs mobiles. En utilisant ce contexte, les développeurs d’applications mobiles peuvent améliorer la conception de l’application et en faire une expérience plus personnalisée et plus attrayante.

Le service d’emplacement d’Adobe Experience Platform (Location Service) est un service de géolocalisation qui permet aux applications mobiles connaissant l’emplacement de comprendre le contexte de l’emplacement en utilisant des interfaces SDK riches et faciles à utiliser, accompagnées d’une base de données flexible de points d’intérêt (POI).

Le service d’emplacement vous permet d’effectuer les opérations suivantes :

* Créez et gérez une base de données des points d’intérêt pouvant être exploitée avec d’autres solutions Adobe Experience Cloud.
* Associez des métadonnées personnalisées aux points d’intérêt pour les rendre plus riches et plus significatives en spécifiant des attributs supplémentaires.
* Visualisez les points d’intérêt sur une carte pour comprendre facilement le contexte spatial et ajouter/modifier des attributs de métadonnées.
* Configurez le SDK dans Adobe Experience Platform Launch pour définir vos règles déclenchées par l’emplacement et vos conditions basées sur les métadonnées.
* Réduisez le code que vous devez écrire pour surveiller l’emplacement d’un périphérique et utilisez l’extension Places pour déclencher automatiquement les règles spécifiques à l’emplacement.

Cela vous permettra d'agir à partir des signaux d'emplacement en temps réel, quand et où cela importe. Le contexte approprié offre une expérience d’engagement mobile plus enrichissante.

Voici quelques-unes des méthodes d’utilisation de Places :

* Envoyez une notification en temps réel quand quelqu'un entre dans un point d'intérêt, *"Hé...bienvenue au stade."*
* Analysez le trafic de pied de vos propres magasins par rapport à celui de vos concurrents.
* Segmentez une audience en fonction du comportement hors ligne en utilisant des profils d’audience avec contexte d’emplacement.
* Ciblez un utilisateur avec une expérience en magasin, le cas échéant.

## Composants du service d’emplacement

Le service d’emplacement comprend les composants suivants :

* **Service Web**

   Vous pouvez créer et gérer des points d’intérêt à l’aide des API REST Places. Pour plus d’informations sur les API REST, voir [Gestion des bibliothèques](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) et [Gestion des API](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **Interface de gestion des API**

   Visualisez les points d’intérêt sur une carte pour comprendre le contexte spatial et ajouter/modifier les points d’intérêt et leurs métadonnées personnalisées.

* **Extension Places**

   L’interface API mobile multiplateforme pour intégrer le contexte d’emplacement dans vos applications mobiles. Pour plus d’informations sur les SDK, voir [Extension](/help/places-ext-aep-sdks/places-extension/places-extension.md)Places.

* **Règles de lancement**

   Règles de lancement géointelligentes qui vous permettent de déclencher des actions avec des événements d’entrée et de sortie. Les règles vous permettent également d’utiliser des attributs géographiques dans des conditions pour personnaliser l’expérience.

* **Extension du moniteur des lieux**

   SDK mobile multiplateforme pouvant être intégré dans votre application mobile pour surveiller automatiquement les modifications d’emplacement de l’utilisateur et déclencher des règles de lieux. Pour plus d’informations, voir [Extension](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md)du moniteur des lieux.

## Terminologie

Voici quelques termes courants utilisés dans cette documentation :

* Un **point d’intérêt (POI)** est un lieu géographique qui intéresse votre organisation.

   Vous pouvez définir des points d’intérêt avec des attributs tels que le nom, le rayon, l’adresse, la catégorie et les balises de métadonnées.

* Une **géofence** est un type de point d'intérêt.

   Ce type d’IPE est une limite géographique virtuelle définie par les coordonnées de latitude et de longitude.

* Une **balise** est un type de point d’intérêt.

   Ce type d'interface est un périphérique physique qui représente un emplacement en émettant un signal Bluetooth à faible puissance. La prise en charge des balises sera disponible dans une prochaine version.

* Une **bibliothèque** est une collection de POI permettant l’association plus simple de règles à un ensemble de POI plutôt qu’à un POI unique.

* Une **extension** est l’extension Experience Platform Launch requise pour intégrer le SDK Places dans vos applications mobiles.

   Extension utilisée avec les autres SDK mobiles pour ajouter un contexte d’emplacement à vos expériences.

* Une **organisation** est l’entité Adobe qui identifie votre société dans Adobe Experience Cloud.

   En règle générale, une organisation est le nom de votre société. Cependant, une entreprise peut avoir plusieurs organisations. L’administrateur de l’organisation peut configurer des groupes et des utilisateurs et configurer la fonctionnalité de connexion unique.

* L’**orgID** est l’identifiant représentant votre organisation dans Adobe Experience Platform.

   Pour plus d’informations, voir [Recherche de votre orgID](https://forums.adobe.com/thread/2339895).

* The **Experience Cloud ID** service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud.

   For more information, see [Overview](https://docs.adobe.com/content/help/en/id-service/using/intro/overview.html).
