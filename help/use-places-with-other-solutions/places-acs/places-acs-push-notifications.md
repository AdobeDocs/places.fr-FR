---
title: Notifications Push
seo-title: Notifications Push
description: Cette section fournit des informations sur l’utilisation des emplacements avec des notifications Push dans Campaign Standard.
seo-description: 'Cette section fournit des informations sur l’utilisation des emplacements avec des notifications Push dans Campaign Standard. '
translation-type: tm+mt
source-git-commit: 4ee8adb73f6dec15030a160c27edbeca71d3507b

---


# Notifications Push avec le service d’emplacement {#push-notifications}

Ce guide explique comment utiliser les informations historiques de géolocalisation pour cibler les notifications Push diffusées via Adobe Campaign Standard.

## Conditions préalables 

Avant de commencer, effectuez les tâches suivantes :

* Disposez d’une application mobile configurée avec le SDK mobile Adobe Experience Platform, y compris l’extension [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.

* Intégrez le SDK [mobile](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform à votre application.
* Ajoutez [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) à la configuration de votre application mobile.

* [Créez un point d’accès](/help/poi-mgmt-ui/create-a-poi-ui.md) dans l’interface de gestion des points d’accès.

* Activez et installez l’extension [Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Création d’éléments de données dans Experience Platform Launch

Après avoir vérifié que le moniteur des lieux et des lieux pour les extensions du service d’emplacement fonctionne correctement dans votre application, créez des éléments de données dans le lancement de la plateforme d’expérience. Les éléments de données vous permettent de lire les informations fournies par les extensions provenant du concentrateur d’événements SDK Mobile et d’agir comme un alias pour récupérer les données de l’application cliente. Pour récupérer les données des extensions Lieux et envoyer les informations Lieux à Campaign, vous devez créer quelques éléments de données.

Pour créer un élément de données :

1. Dans votre propriété mobile de lancement de plateforme d’expérience, cliquez sur l’ **[!UICONTROL Data Elements]** onglet et sur **[!UICONTROLAAjouter un élément]** de données.
1. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Places]**.
1. Dans la liste **[!UICONTROL Data Element Type]** déroulante, sélectionnez **[!UICONTROL Name]**.
1. Dans le volet de droite, vous pouvez sélectionner **[!UICONTROL Current POI]** qui récupère le nom de l’API dans laquelle se trouve actuellement l’utilisateur.

   **[!UICONTROL Last Entered]** récupère le nom de l’API que l’utilisateur a saisi pour la dernière fois et **[!UICONTROL Last Exited]** fournit le nom de l’API qu’il a quitté pour la dernière fois. Dans cet exemple, nous allons sélectionner **[!UICONTROL Last Entered]** et taper le nom de l’élément de données, par exemple **[!UICONTROL Last Entered POI Name]** et en cliquant **[!UICONTROL Save]**.

   !["Messagerie push dans Campaign Standard"](/help/assets/ACS_Push1.png)

1. Repeat the steps 1-4 above and create data elements for *Last Entered POI Latitude*, *Last Entered POI Longitude*, and *Last Entered POI Radius*.

Outre les éléments de données du service d’emplacement, veillez à créer des éléments de données principaux pour Mobile pour l’ID ** d’application et l’ID ** Experience Cloud.

## Création d’une règle pour envoyer des données d’emplacement à Adobe Campaign Standard

Les règles de lancement de plate-forme d’expérience vous permettent de créer des processus complexes et multisolutions basés sur des déclencheurs d’événement. Les règles vous permettent de créer de nouvelles règles ou de modifier des règles existantes et de déployer dynamiquement les mises à jour sur vos applications mobiles. Dans l’exemple suivant, la règle est déclenchée lorsqu’un utilisateur entre dans un point d’accès géoclôturé. Une fois la règle déclenchée, une mise à jour est envoyée à Campaign Standard afin d’enregistrer une entrée dans une API spécifique pour un utilisateur particulier en fonction de l’ID d’expérience Cloud.

1. Dans la propriété Launch mobile, sur l’ **[!UICONTROL Rules]** onglet, cliquez sur **[!UICONTROL Add Rule]**.
1. Sous la **[!UICONTROL Events]** section, cliquez sur **[!UICONTROL +]** et sélectionnez **[!UICONTROL Places]** comme extension.
1. For the **[!UICONTROL Event Type]**, select **[!UICONTROL Enter POI]**.
1. Attribuez un nom à la règle, par exemple, **l’utilisateur a saisi l’API**.
1. Cliquez sur **[!UICONTROL Keep Changes]** (Nouvelle propriété).
1. Laissez la **[!UICONTROL Conditions]** section vide.

   Cette section vous permet de filtrer ou d’imposer des restrictions sur le moment où cette règle doit se déclencher.

1. Sous la **[!UICONTROL Actions]** section, cliquez sur **[!UICONTROL +]**.
1. Dans la liste **[!UICONTROL Extension]** déroulante, sélectionnez **[!UICONTROL Mobile Core]** , puis, dans la **[!UICONTROL Action Type]** liste déroulante, sélectionnez **[!UICONTROL Send Postback]**.
1. Dans **[!UICONTROL URL]**, vous devez construire votre point de fin d’emplacements Campaign Standard.

   L’URL doit ressembler à `https:///rest/head/mobileAppV5//locations/`.
Assurez-vous d’utiliser les éléments de données corrects que vous avez créés précédemment pour votre serveur Campaign et votre clé pKey.

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
1. Dans **[!UICONTROL Content Type]**, saisissez **[!UICONTROL application/json]**.
1. Cliquez sur **[!UICONTROL Keep Changes]** (Nouvelle propriété).

>[!IMPORTANT]
>
>* Il peut s’avérer utile de configurer un crochet Web Slack comme action supplémentaire pour vérifier que les entrées sont déclenchées et que les données appropriées sont collectées.


>* N’oubliez pas de publier les modifications récentes apportées à votre application pour vous assurer que la règle et tous vos éléments de données sont déployés dans le cadre de votre configuration. Après publication, vous devez relancer l’application mobile pour obtenir les dernières mises à jour de configuration.


## Utiliser des données d'emplacement pour cibler des messages de campagne

Maintenant que les données d’emplacement sont renseignées dans Campaign, nous pouvons utiliser les points d’intérêt comme outil de segmentation de l’audience.

1. Dans votre instance Adobe Campaign Standard, cliquez sur **[!UICONTROL Create Push Notification]**.
1. Pour le type de notification Push, sélectionnez **[!UICONTROL Send push to Campaign profiles]**.
1. Cliquez sur **[!UICONTROL Next]** et saisissez les détails généraux.
1. Dans l’écran Public, cliquez sur **[!UICONTROL Count]** pour déterminer le nombre estimé d’utilisateurs qui recevront la notification Push.

   >[!TIP]
   >
   >Dans cet exemple, le nombre sera de 3, car il existe trois périphériques installés sur lesquels l’application est en cours de test.

1. Dans le volet de gauche, développez l’ **[!UICONTROL Profile]** onglet et faites glisser le **[!UICONTROL POI location]** filtre vers la zone principale.
1. Dans la fenêtre de filtre d’API, entrez le nom exact de l’API que vous souhaitez cibler.

   >[!TIP]
   >
   >Vous pouvez effectuer des sélections supplémentaires afin de déterminer la période écoulée depuis la dernière visite de l’utilisateur à ce point d’intérêt.

   !["Messagerie push 2 in ACS"](/help/assets/ACS_push2.png)

1. Cliquez sur **[!UICONTROL Confirm]** (Nouvelle propriété).
1. Exécutez à nouveau le compte en haut pour voir la taille de votre audience changer.

   Si vous ne voyez pas la mise à jour de votre compte, vous avez peut-être saisi un nom d’API pour lequel aucun périphérique n’a déclenché une entrée. Le crochet Web Slack devient intéressant dans cette situation, car vous pouvez voir la liste des entrées d’API de différents périphériques de test.
1. Vous pouvez faire glisser d’autres filtres d’emplacement de point d’intérêt pour inclure plusieurs points d’intérêt dans votre message.
1. Click **[!UICONTROL Next]** to finish creating the push notification for delivery.

   !["Messagerie push 3 in ACS"](/help/assets/ACS_push3.html)

L’utilisation du service d’emplacement avec Adobe Campaign Standard vous offre un outil puissant pour segmenter et cibler vos messages sur les utilisateurs en fonction des entrées et des sorties de géolocalisation. Cette intégration vous aide à créer des cas d’utilisation plus personnalisés et contextuels.