---
title: Présentation d’Adobe Places
seo-title: Présentation d’Adobe Places
description: 'Adobe Places est un contexte important pour comprendre l’engagement des utilisateurs mobiles. En utilisant ce contexte, les développeurs d’applications mobiles peuvent améliorer la conception de l’application et en faire une expérience plus personnalisée et plus attrayante. '
seo-description: 'Les lieux sont un contexte important pour comprendre l’engagement des utilisateurs mobiles. En utilisant ce contexte, les développeurs d’applications mobiles peuvent améliorer la conception de l’application et en faire une expérience plus personnalisée et plus attrayante. '
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Aperçu {#home}

Adobe Places est un contexte important pour comprendre l’engagement des utilisateurs mobiles. En utilisant ce contexte, les développeurs d’applications mobiles peuvent améliorer la conception de l’application et en faire une expérience plus personnalisée et plus attrayante. Places est un service de géolocalisation qui permet aux développeurs d’applications mobiles de comprendre le contexte de l’emplacement en utilisant des interfaces SDK riches et faciles à utiliser, accompagnées d’une base de données flexible de points d’intérêt (POI).

Les emplacements vous permettent d’effectuer les opérations suivantes :

* Créez et gérez une base de données des points d’intérêt qui peut être exploitée avec d’autres solutions Adobe Experience Cloud.
* Associez des métadonnées personnalisées aux points d’intérêt pour les rendre plus riches et plus significatives en spécifiant des attributs supplémentaires.
* Visualisez les points d’intérêt sur une carte pour comprendre facilement le contexte spatial et ajouter/modifier des attributs de métadonnées.
* Configurez le SDK dans Adobe Experience Platform Launch pour définir vos règles déclenchées par l’emplacement et vos conditions basées sur les métadonnées.
* Réduisez le code que vous devez écrire sur l’emplacement du périphérique du moniteur et utilisez le moniteur d’emplacement d’Adobe pour déclencher automatiquement les règles spécifiques à l’emplacement.

Cela vous permettra d'agir à partir des signaux d'emplacement en temps réel, quand et où cela importe. Le contexte approprié offre une expérience d’engagement mobile plus enrichissante.

Voici quelques-unes des méthodes d’utilisation de Places :

* Envoyez une notification en temps réel quand quelqu'un entre dans un point d'intérêt, *"Hé...bienvenue au stade."*
* Analysez le trafic de pied de vos propres magasins par rapport à celui de vos concurrents.
* Segmentez une audience en fonction du comportement hors ligne en utilisant des profils d’audience avec contexte d’emplacement.
* Ciblez un utilisateur avec une expérience en magasin, le cas échéant.

## Place les composants

Les lieux comprennent les composants suivants :

* **Place le service Web**

   Vous pouvez créer et gérer des points d’intérêt à l’aide des API REST. Pour plus d’informations sur les API REST, voir [Places Web Services](/help/places-rest-apis/api-usage/api-usage.md).

* **Interface utilisateur Places**

   Visualisez les points d’intérêt sur une carte pour comprendre le contexte spatial et ajouter/modifier les points d’intérêt et leurs métadonnées personnalisées.

* **Places SDK**

   L’interface API mobile multiplateforme pour intégrer le contexte d’emplacement dans vos applications mobiles. Pour plus d’informations sur les SDK, voir [Extension](/help/configure-places-in-the-sdk/places-extension/places-extension.md)Places.

* **Règles de lieux**

   Règles de lancement géointelligentes qui vous permettent de déclencher des actions avec des événements d’entrée et de sortie. Les règles vous permettent également d’utiliser des attributs géographiques dans des conditions pour personnaliser l’expérience.

* **Moniteur des lieux**

   SDK mobile multiplateforme pouvant être intégré dans votre application mobile pour surveiller automatiquement les modifications d’emplacement de l’utilisateur et déclencher des règles de lieux. Pour plus d’informations, voir [Extension](/help/configure-places-in-the-sdk/places-monitor-extension/places-monitor-extension.md)du moniteur des lieux.

## Terminologie

Voici quelques termes courants utilisés dans cette documentation :

* Un **point d’intérêt (POI)** est un lieu géographique qui intéresse votre organisation.

   Vous pouvez définir des points d’intérêt avec des attributs tels que le nom, le rayon, l’adresse, la catégorie et les balises de métadonnées.

* Une **géofence** est un type de point d'intérêt.

   Ce type d’IPE est une limite géographique virtuelle définie par les coordonnées de latitude et de longitude.

* Une **balise** est un type de point d’intérêt.

   Ce type d'interface est un périphérique physique qui représente un emplacement en émettant un signal Bluetooth à faible puissance. La prise en charge des balises sera disponible dans une prochaine version.

* Une **bibliothèque** est une collection d’objets d’intérêt regroupés pour associer facilement des règles à un ensemble plutôt qu’à un seul objet d’intérêt.

* Une **extension** SDK est l’extension de lancement de plateforme d’expérience requise pour intégrer le SDK Places dans vos applications mobiles.

   Extension utilisée avec les autres SDK mobiles pour ajouter un contexte d’emplacement à vos expériences.

* Une **organisation** est l’entité Adobe qui identifie votre entreprise dans Adobe Experience Cloud.

   En règle générale, une organisation est le nom de votre société. Cependant, une entreprise peut avoir plusieurs organisations. L’administrateur de l’organisation peut configurer des groupes et des utilisateurs et configurer la fonctionnalité de connexion unique.

* L’ **orgID** est l’identifiant qui représente votre organisation dans Adobe Experience Platform.

   Pour plus d’informations, voir [Recherche de votre orgID](https://forums.adobe.com/thread/2339895).

* The **Experience Cloud ID** service provides a universal, persistent ID that identifies your visitors across all the solutions in the Experience Cloud.

   For more information, see [Overview](https://docs.adobe.com/content/help/en/id-service/using/intro/overview.html).

## Présentation de l’interface utilisateur Places

Pour accéder à l’interface utilisateur Places, dans un navigateur, accédez à l’interface utilisateur [Places](https://places.adobe.com) et connectez-vous avec votre Adobe ID.

Voici quelques informations de base pour vous familiariser avec l’interface utilisateur :

* Dans le coin supérieur droit, vous pouvez cliquer sur des boutons pour créer une bibliothèque, des points d’intérêt et filtrer votre recherche.
* Dans le coin inférieur droit de l’écran, il y a des boutons permettant d’effectuer un zoom avant ou arrière, de centrer sur votre emplacement actuel **[!UICONTROL Find Me]** et de basculer entre la vue de carte et la vue satellite.
* Cliquez deux fois pour effectuer un zoom avant ou cliquez et faites glisser pour recentrer la carte.
* Vous pouvez également utiliser les touches fléchées pour faire défiler la carte.

![](assets/location-services.png)


## Flux de travaux Places

Voici une vue générale du flux de travaux Places :

![](/help/assets/places-workflow-diagram-lc-1.png)