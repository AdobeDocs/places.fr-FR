---
title: Messages in-app avec le service Places
description: Cette section fournit des informations sur l’utilisation de la messagerie Push en Campaign Standard avec des messages In-App en Campaign Standard.
translation-type: tm+mt
source-git-commit: 462df20bb351795dc72009cc18d390cb45e262a8
workflow-type: tm+mt
source-wordcount: '356'
ht-degree: 3%

---


# Messagerie in-app avec le service Places {#in-app-messages-loc-service}

Ces informations vous aident à comprendre comment utiliser les informations du service Places pour envoyer des messages in-app ou des notifications locales.

## Conditions préalables 

Avant de commencer, effectuez les tâches suivantes :

* Disposez d’une application mobile configurée avec le Adobe Experience Platform Mobile SDK, y compris l’extension [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.

* Intégrez le SDK [](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform Mobile à votre application.
* Ajoutez l’extension [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) Adobe Campaign Standard à votre configuration d’application mobile.

* [Créez un POI](/help/poi-mgmt-ui/create-a-poi-ui.md) dans l’interface de gestion du POI du service Places.

* Installez et configurez l&#39;extension [](/help/places-ext-aep-sdks/places-extension/places-extension.md) Places et les extensions [](/help/places-ext-aep-sdks/places-monitor-extension/places-monitor-extension.md) Places Monitor dans votre application mobile.

## Envoi d’un message intégré à l’application en fonction d’une entrée ou d’une sortie de géolocalisation

1. Dans votre instance Adobe Campaign Standard, cliquez sur **[!UICONTROL Create In-App message]**.
1. Pour le type de message, sélectionnez **[!UICONTROL Target all users of a Mobile application]**.
1. Cliquez sur **[!UICONTROL Next]** et tapez les détails généraux.
1. Dans le volet de gauche, vérifiez que vous pouvez utiliser divers déclencheurs liés à Places Services.

   * Vous pouvez choisir d’afficher le message in-app si l’utilisateur a entré une clôture de point d’accès (POI).
   * Vous pouvez également utiliser des métadonnées définies dans l’interface utilisateur de Places Services pour filtrer l’audience.

   Dans l’exemple ci-dessous, vous pouvez déclencher un message in-app qui s’affiche uniquement pour les utilisateurs qui entrent dans l’un des centres de vacances participant à un programme de boisson gratuite et vous souhaitez envoyer un bon à ces utilisateurs à leur arrivée.

   ![&quot;Métadonnées des emplacements de messages in-app&quot;](/help/assets/last-entered-vacation.png)

1. Click the **[!UICONTROL Next]** to finish creating the In-app message for delivery.

   ![&quot;créer un événement&quot;](/help/assets/prepare-ACS.png)

   Pour tester la diffusion de messages in-app, lancez l’application dans Xcode ou Android studio et utilisez le simulateur d’emplacement pour sélectionner un point d’intérêt correspondant aux critères de messagerie.

   ![&quot;coupon de boisson&quot;](/help/assets/drink-coupon-on-app.png)

L’utilisation de Places Services avec Adobe Campaign Standard vous offre un outil puissant pour segmenter et cible vos messages aux utilisateurs en fonction des entrées et sorties de géo-clôtures. Cette intégration vous permet de créer des cas d’utilisation plus personnalisés et contextuels.

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Service d&#39;emplacement Adobe Experience Platform avec messagerie Campaign](https://www.youtube.com/watch?v=ikiTTQw9c-o)
