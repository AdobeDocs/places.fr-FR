---
title: Messages In-App avec Places Service
description: Cette section fournit des informations sur l’utilisation de la messagerie push en Campaign Standard avec les messages In-App en Campaign Standard.
exl-id: c80727b8-20c9-4ca0-9f2c-20ec646bb7fa
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '394'
ht-degree: 4%

---

# Messagerie In-App avec Places Service {#in-app-messages-loc-service}

Ces informations vous aident à comprendre comment utiliser les informations du service Places pour envoyer des messages In-App ou des notifications locales.

## Conditions préalables

Avant de commencer, effectuez les tâches suivantes :

* disposer d’une application mobile configurée avec le SDK Mobile Adobe Experience Platform, y compris le [Extension Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Intégrez la variable [SDK Adobe Experience Platform Mobile](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) dans votre application.
* Ajoutez la variable [Extension Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) à la configuration de votre application mobile.

* [Création d’un point ciblé](/help/poi-mgmt-ui/create-a-poi-ui.md) dans l’interface de gestion des points ciblés du service Places.

* Installez et configurez le [Extension Places](/help/places-ext-aep-sdks/places-extension/places-extension.md) et une solution de surveillance de région ([Documentation CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) pour iOS ou [Documentation sur l’emplacement Android](https://developer.android.com/training/location/geofencing)) dans votre application mobile.

## Envoi d’un message In-App basé sur une entrée ou une sortie de géolocalisation

1. Dans votre instance Adobe Campaign Standard, cliquez sur **[!UICONTROL Créer un message In-App]**.
1. Pour le type de message, sélectionnez **[!UICONTROL Cibler tous les utilisateurs d&#39;une application mobile]**.
1. Cliquez sur **[!UICONTROL Suivant]** et saisissez les détails généraux.
1. Dans le volet de gauche, vérifiez que vous pouvez utiliser divers déclencheurs liés à Places Services.

   * Vous pouvez choisir d’afficher le message in-app si l’utilisateur a entré une géo-barrière de point ciblé.
   * Vous pouvez également utiliser des métadonnées définies dans l’interface utilisateur des services Places pour filtrer l’audience.

   Dans l’exemple ci-dessous, vous pouvez déclencher un message in-app qui s’affiche uniquement pour les utilisateurs qui se rendent dans l’un des centres de vacances participant à un programme de boissons gratuites. Vous souhaitez envoyer un bon à ces utilisateurs lorsqu’ils arrivent.

   ![&quot;Métadonnées Places de message in-app&quot;](/help/assets/last-entered-vacation.png)

1. Cliquez sur le bouton **[!UICONTROL Suivant]** pour terminer la création du message in-app pour la diffusion.

   ![&quot;créer un événement&quot;](/help/assets/prepare-ACS.png)

   Pour tester la diffusion des messages in-app, lancez l’application dans Xcode ou Android Studio et utilisez le simulateur d’emplacement pour sélectionner un point ciblé qui correspond aux critères de messagerie.

   ![&quot;coupon de boisson&quot;](/help/assets/drink-coupon-on-app.png)

L’utilisation de Places Services avec Adobe Campaign Standard vous offre un outil puissant pour segmenter et cibler vos messages vers les utilisateurs en fonction des entrées et des sorties de géo-barrières. Cette intégration vous permet de créer des cas d’utilisation plus personnalisés et contextuels.

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Service de localisation Adobe Experience Platform avec messagerie Campaign](https://www.youtube.com/watch?v=ikiTTQw9c-o)
