---
title: Places Service
description: 'Le service Places est un contexte important pour comprendre l’engagement des utilisateurs mobiles. En utilisant ce contexte, les développeurs d’applications mobiles peuvent améliorer la conception de l’application et en faire une expérience plus personnalisée et plus attrayante. '
translation-type: tm+mt
source-git-commit: 05b4d29aa7925f7a43e70c644e3cb88045cbe446
workflow-type: tm+mt
source-wordcount: '708'
ht-degree: 10%

---


# Places Service {#home}

![&quot;Places Service&quot;](/help/assets/places-service-header.png)

La localisation est un contexte important pour comprendre et interagir avec les utilisateurs mobiles. En utilisant ce contexte, les développeurs d’applications mobiles peuvent améliorer la conception de l’application et en faire une expérience plus personnalisée et plus attrayante.

Le service Places, précédemment appelé Adobe Experience Platform Location Service, est un service de géolocalisation qui permet aux applications mobiles connaissant l&#39;emplacement de comprendre le contexte de l&#39;emplacement en utilisant des interfaces SDK riches et faciles à utiliser, accompagnées d&#39;une base de données flexible de points d&#39;intérêt (POI).

Le service Places vous permet d’effectuer les opérations suivantes :

* Créez et gérez une base de données des points d’intérêt qui peut être exploitée avec d’autres solutions Adobe Experience Cloud.
* Joignez des métadonnées personnalisées aux points d’intérêt afin de les rendre plus riches et plus significatives en spécifiant des attributs supplémentaires.
* Visualisez les points d’intérêt sur une carte pour comprendre facilement le contexte spatial et ajouter/modifier des attributs de métadonnées.
* Configurez le SDK en Adobe Experience Platform Launch pour définir les règles déclenchées par l’emplacement et les conditions basées sur les métadonnées.
* Réduisez le code que vous devez écrire pour surveiller l&#39;emplacement d&#39;un périphérique et utilisez l&#39;extension Lieux pour déclencher automatiquement les règles propres à l&#39;emplacement.

Cela vous permettra d&#39;agir à partir des signaux de localisation en temps réel, quand et où cela compte. Le contexte approprié offre une expérience d’engagement mobile plus enrichissante.

Voici quelques-unes des façons d&#39;utiliser Places :

* Envoyez une notification en temps réel lorsque quelqu&#39;un entre dans un POI, *&quot;Hey..bienvenue au stade.&quot;*
* Comparez le trafic de pied de vos propres magasins à celui de vos concurrents.
* Segmentez une audience en fonction du comportement hors ligne en utilisant des profils d’audience avec contexte d’emplacement.
* Cible d’un utilisateur avec une expérience en magasin, le cas échéant.

## Place les composants Service

Le service Places comprend les composants suivants :

* **Service Web**

   Vous pouvez créer et gérer des points d’intérêt à l’aide des API REST Places. Pour plus d’informations sur les API REST, voir [Gestion des bibliothèques](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) et [Gestion des API](/help/web-service-api/api-usage/manage-pois/manage-pois.md).

* **Interface de gestion des POI**

   Visualisez les points d’intérêt sur une carte pour comprendre le contexte spatial et ajouter/modifier les points d’intérêt et leurs métadonnées personnalisées.

* **Extension Places**

   Interface API mobile multiplate-forme permettant d’intégrer le contexte d’emplacement dans vos applications mobiles. Pour plus d’informations sur les SDK, voir [Place extension](/help/places-ext-aep-sdks/places-extension/places-extension.md).

* **Règles de lancement**

   Règles de lancement géointelligentes qui vous permettent de déclencher des actions avec des événements d’entrée et de sortie. Les règles vous permettent également d’utiliser des attributs géographiques dans des conditions pour personnaliser l’expérience.

* **Extension du moniteur de lieux**

   Le SDK mobile multiplate-forme qui peut être intégré dans votre application mobile pour surveiller automatiquement les modifications d’emplacement de votre utilisateur et déclencher des règles de lieux. Pour plus d’informations, voir [Place Monitor extension](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md).

## Terminologie

Voici quelques termes courants utilisés dans cette documentation :

* Un **point d’intérêt (POI)** est un emplacement géographique qui présente un intérêt pour votre organisation.

   Vous pouvez définir des points d’intérêt avec des attributs tels que le nom, le rayon, l’adresse, la catégorie et les balises de métadonnées.

* Un **géofence** est un type d&#39;IPE.

   Ce type d’IPE est une limite géographique virtuelle définie par les coordonnées de latitude et de longitude.

* Une **balise** est un type d&#39;IPE.

   Ce type de point d&#39;accès est un périphérique physique qui représente un emplacement en émettant un signal Bluetooth à faible puissance. La prise en charge des balises sera disponible dans une prochaine version.

* Une **bibliothèque** est une collection de POI permettant l’association plus simple de règles à un ensemble de POI plutôt qu’à un POI unique.

* Une **extension** est l’extension Experience Platform Launch requise pour intégrer le SDK Places dans vos applications mobiles.

   Extension utilisée avec les autres SDK mobiles pour ajouter un contexte d’emplacement à vos expériences.

* Une **organisation** est l’entité Adobe qui identifie votre société dans Adobe Experience Cloud.

   En règle générale, une organisation est votre nom de société. Cependant, une société peut avoir plusieurs organisations. L’administrateur de l’organisation peut configurer des groupes et des utilisateurs et configurer la fonctionnalité de connexion unique.

* L’**orgID** est l’identifiant représentant votre organisation dans Adobe Experience Platform.

   Pour plus d’informations, voir [Recherche de votre orgID](https://forums.adobe.com/thread/2339895).

* Le service **ID d’Experience Cloud** fournit un identifiant universel et persistant qui identifie vos visiteurs dans toutes les solutions de l’Experience Cloud.

   Pour plus d’informations, voir [Aperçu](https://docs.adobe.com/content/help/fr-FR/id-service/using/intro/overview.html).
