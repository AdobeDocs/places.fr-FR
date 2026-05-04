---
title: Messages In-App avec Places Service
description: Cette section fournit des informations sur l’utilisation de la messagerie push dans Campaign Standard avec les messages In-App dans Campaign Standard.
exl-id: c80727b8-20c9-4ca0-9f2c-20ec646bb7fa
TQID: https://experienceleague.adobe.com/H2gW4nvnx8Es33S8nCt52OIUsNOY5SG1SZVJPw0BFFg
product_v2:
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dfc56824-e8b9-499e-85d4-21aedb507314
  - id: e43347a8-f2c5-4aa4-8623-6f13875d7e3a
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
  - id: f002a92a-b99f-47a4-90c8-65e0e415bc7a
feature_v2:
  - id: d833d0ef-8ed5-4cff-a5e7-9f12abd02a31
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dc
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 415
ht-degree: 5%

---

# Messagerie In-App avec Places Service {#in-app-messages-loc-service}

Ces informations vous aident à comprendre comment utiliser les informations du service Places pour envoyer des messages In-App ou des notifications locales.

## Conditions préalables

Avant de commencer, effectuez les tâches suivantes :

* Ayez une application mobile configurée avec le SDK Mobile Adobe Experience Platform, y compris l&#39;extension [Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Intégrez le [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) dans votre application.
* Ajoutez l’extension [&#128279;](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) à votre configuration d’application mobile.

* [Créez un point d’intérêt](/help/poi-mgmt-ui/create-a-poi-ui.md) dans l’interface de gestion des points d’intérêt du service Places.

* Installez et configurez l&#39;extension [Places](/help/places-ext-aep-sdks/places-extension/places-extension.md) ainsi qu&#39;une solution de surveillance des zones géographiques ([documentation CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) pour iOS ou [documentation sur l&#39;emplacement d&#39;Android](https://developer.android.com/training/location/geofencing)) dans votre application mobile.

## Envoi d’un message In-App en fonction d’une entrée ou d’une sortie de clôture géographique

1. Dans votre instance Adobe Campaign Standard, cliquez sur **[!UICONTROL Créer un message In-App]**.
1. Pour le type de message, sélectionnez **[!UICONTROL Cibler tous les utilisateurs d&#39;une application mobile]**.
1. Cliquez sur **[!UICONTROL Suivant]** et saisissez les détails généraux.
1. Dans le volet de gauche, vérifiez que vous pouvez utiliser divers déclencheurs liés aux services Places.

   * Vous pouvez choisir d’afficher le message in-app si l’utilisateur a saisi une clôture géographique de point d’intérêt.
   * Vous pouvez également utiliser des métadonnées définies dans l’interface utilisateur de Places Services pour filtrer l’audience.

   Dans l’exemple ci-dessous, vous pouvez déclencher un message in-app qui s’affiche uniquement pour les utilisateurs et utilisatrices qui accèdent à l’un des centres de vacances participant à un programme de boisson gratuite et auquel vous souhaitez envoyer un coupon à leur arrivée.

   ![« Métadonnées des emplacements de message in-app »](/help/assets/last-entered-vacation.png)

1. Cliquez sur le **[!UICONTROL Suivant]** pour terminer la création du message in-app à diffuser.

   ![« créer un événement »](/help/assets/prepare-ACS.png)

   Pour tester la diffusion de messages in-app, lancez l’application dans Xcode ou Android Studio et utilisez le simulateur d’emplacement pour sélectionner un point d’intérêt correspondant aux critères de messagerie.

   ![« coupon de boisson »](/help/assets/drink-coupon-on-app.png)

L’utilisation de Places Services avec Adobe Campaign Standard vous offre un outil puissant pour segmenter et cibler vos messages vers les utilisateurs en fonction des entrées et des sorties de clôture géographique. Cette intégration vous permet de créer des cas d’utilisation plus personnalisés et contextuels.

<!--I changed this embed to a link to pass validation. We should not link to youtube videos, so please upload this to MCP-->

[Service de localisation Adobe Experience Platform avec messagerie Campaign](https://www.youtube.com/watch?v=ikiTTQw9c-o)
