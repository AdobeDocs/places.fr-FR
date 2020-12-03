---
title: Notifications Push avec le service Places
description: Cette section fournit des informations sur l'utilisation du service Lieux avec des notifications Push en Campaign Standard.
translation-type: tm+mt
source-git-commit: fd469358845e14c47a58b40bb18c9144828a8996
workflow-type: tm+mt
source-wordcount: '911'
ht-degree: 2%

---


# Notifications Push avec le service Places {#push-notifications}

Dans cette section, vous apprendrez comment utiliser les informations de géolocalisation historiques pour cible des notifications Push diffusées via Adobe Campaign Standard.

## Conditions préalables 

Avant de commencer, effectuez les tâches suivantes :

* Disposez d’une application mobile configurée avec le Adobe Experience Platform Mobile SDK, y compris l’extension [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.

* Intégrez le SDK [](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform Mobile à votre application.
* Ajoutez l’extension [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) Adobe Campaign Standard à votre configuration d’application mobile.

* [Créez un POI](/help/poi-mgmt-ui/create-a-poi-ui.md) dans l’interface de gestion du POI du service Places.

* Activez et installez l’extension [](/help/places-ext-aep-sdks/places-extension/places-extension.md)Places.


## Création d’éléments de données dans l’Experience Platform Launch

Après avoir vérifié que l&#39;extension Places et l&#39;extension Places Monitor fonctionnent correctement dans votre application, vous devez créer des éléments de données dans l&#39;Experience Platform Launch. Les éléments de données vous permettent de lire les informations fournies par les extensions provenant du hub de événement SDK Mobile et d’agir en tant qu’alias pour récupérer les données de l’application cliente. Pour récupérer les données des extensions Places et envoyer les informations du service Places à Campaign, vous devez créer quelques éléments de données.

Création d’un élément de données:

1. Dans la propriété mobile de votre Experience Platform Launch, cliquez sur l’ **[!UICONTROL Data Elements]** onglet et sur **[!UICONTROL Add Data Element]**.
1. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Places Service]**.
1. Dans la liste **[!UICONTROL Data Element Type]** déroulante, sélectionnez **[!UICONTROL Name]**.
1. Dans le volet de droite, vous pouvez sélectionner **[!UICONTROL Current POI]** qui récupère le nom de l’API dans lequel se trouve actuellement l’utilisateur.

   **[!UICONTROL Last Entered]** récupère le nom de l’API que l’utilisateur a saisi pour la dernière fois et **[!UICONTROL Last Exited]** fournit le nom de l’API que l’utilisateur a laissé pour la dernière fois. Dans cet exemple, nous avons sélectionné **[!UICONTROL Last Entered]** et saisi un nom pour l’élément de données, par exemple **[!UICONTROL Last Entered POI Name]** et cliqué **[!UICONTROL Save]**.

   ![&quot;Messagerie push en Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Repeat the steps 1-4 above and create data elements for *Last Entered POI Latitude*, *Last Entered POI Longitude*, and *Last Entered POI Radius*.

Outre les éléments de données du service Places, veillez à créer des éléments de données Mobile Core pour l’ID ** d’application et l’ID ** d’Experience Cloud.

## Créer une règle pour envoyer des données d’emplacement à l’Adobe Campaign Standard

Les règles de l’Experience Platform Launch vous permettent de créer des workflows complexes et multi-solutions basés sur des déclencheurs de événement. Les règles vous permettent de créer de nouvelles règles ou de modifier des règles existantes et de déployer dynamiquement les mises à jour sur vos applications mobiles. Dans l’exemple suivant, la règle est déclenchée lorsqu’un utilisateur entre dans un point d’accès géoclôturé. Une fois la règle déclenchée, une mise à jour est envoyée au Campaign Standard pour enregistrer une entrée dans un point d’accès défini pour un utilisateur particulier en fonction de son ID d’Experience Cloud.

1. Dans la propriété mobile de votre Experience Platform Launch, sur l’ **[!UICONTROL Rules]** onglet, cliquez sur **[!UICONTROL Add Rule]**.
1. Sous la **[!UICONTROL Events]** section, cliquez sur **[!UICONTROL +]** et sélectionnez **[!UICONTROL Places Service]** l’extension.
1. For the **[!UICONTROL Event Type]**, select **[!UICONTROL Enter POI]**.
1. Attribuez un nom à la règle, par exemple, l’ **utilisateur a saisi l’API**.
1. Cliquez sur **[!UICONTROL Keep Changes]**.
1. Laissez la **[!UICONTROL Conditions]** section vide.

   Cette section vous permet de filtrer ou d’imposer des restrictions sur le moment où cette règle doit se déclencher.

1. Sous la **[!UICONTROL Actions]** section, cliquez sur **[!UICONTROL +]**.
1. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Mobile Core]** et dans la liste **[!UICONTROL Action Type]** déroulante, sélectionnez **[!UICONTROL Send Postback]**.
1. Dans **[!UICONTROL URL]**, vous devez construire votre point de terminaison d&#39;emplacements Campaign Standards.

   L’URL doit ressembler à `https:///rest/head/mobileAppV5//locations/`.
Assurez-vous d’utiliser les éléments de données corrects que vous avez créés précédemment pour votre serveur Campaign et votre clé.

1. Cliquez sur la zone pour ajouter un corps de publication et envoyer les éléments suivants :

   ```
   {
    "locationData": {
    "distances": "{%%Last Entered POI Radius%%}",
    "poiLabel": "{%%Last Entered POI Name%%}",
    "latitude": "{%%Last Entered POI Lat%%}",
    "longitude": "{%%Last Entered POI Long%%}",
    "appId": "{%%AppID%%}",
    "marketingCloudId": “{%%ecid%%}”
    }
   }
   ```

1. Veillez à utiliser les éléments de données que vous avez créés dans la section précédente.
1. Dans **[!UICONTROL Content Type]**, tapez **[!UICONTROL application/json]**.
1. Cliquez sur **[!UICONTROL Keep Changes]**.

>[!IMPORTANT]
>
>* Il peut s’avérer utile de configurer un hook Web Slack en tant qu’action supplémentaire pour vérifier que les entrées sont déclenchées et que les données appropriées sont collectées.
>* Pensez à publier les dernières modifications apportées à votre application pour vous assurer que la règle et tous vos éléments de données sont déployés dans le cadre de votre configuration. Après la publication, relancez l’application mobile pour obtenir les dernières mises à jour de configuration.


## Utiliser les données d&#39;emplacement pour cible des messages Campaign

Maintenant que les données d’emplacement sont renseignées dans Campaign, nous pouvons utiliser les points d’accès comme outil de segmentation des audiences.

1. Dans votre instance Adobe Campaign Standard, cliquez sur **[!UICONTROL Create Push Notification]**.
1. Pour le type de notification Push, sélectionnez **[!UICONTROL Send push to Campaign profiles]**.
1. Cliquez sur **[!UICONTROL Next]** et tapez les détails généraux.
1. Dans l’écran Audience, cliquez sur **[!UICONTROL Count]** pour déterminer le nombre estimé d’utilisateurs qui recevront la notification Push.

   >[!TIP]
   >
   >Dans cet exemple, le nombre sera de 3, car trois périphériques installés sur lesquels l&#39;application est testée.

1. Dans le volet de gauche, développez l’ **[!UICONTROL Profile]** onglet et faites glisser le **[!UICONTROL POI location]** filtre vers la zone principale.
1. Dans la fenêtre Filtre POI, entrez le nom exact de la POI que vous souhaitez cible.

   >[!TIP]
   >
   >Vous pouvez effectuer d’autres sélections pour déterminer la période écoulée depuis la dernière visite de l’utilisateur à ce point d’intérêt.

   ![&quot;Messagerie Push 2 in ACS&quot;](/help/assets/ACS_push2.png)

1. Cliquez sur **[!UICONTROL Confirm]**.
1. Exécutez à nouveau le décompte en haut pour voir la taille de votre audience changer.

   Si vous ne voyez pas la mise à jour de votre compte, vous avez peut-être saisi un nom d’API pour lequel aucun périphérique n’a déclenché une entrée. Le crochet Web du Slack devient intéressant dans ce cas, car vous pouvez voir la liste des entrées d’API provenant de divers périphériques de test.

1. Vous pouvez faire glisser d’autres filtres d’emplacement de point d’intérêt pour inclure plusieurs points d’intérêt dans votre message.
1. Click **[!UICONTROL Next]** to finish creating the push notification for delivery.

   ![&quot;Messagerie Push 3 in ACS&quot;](/help/assets/ACS_push3.png)

L’utilisation du service Places avec Adobe Campaign Standard vous offre un outil puissant pour segmenter et cible vos messages aux utilisateurs en fonction des entrées et sorties de géo-clôtures. Cette intégration vous aide à créer des cas d’utilisation plus personnalisés et contextuels.