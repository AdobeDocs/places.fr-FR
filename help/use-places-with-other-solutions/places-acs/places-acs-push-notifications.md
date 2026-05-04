---
title: Notifications push avec Places Service
description: Cette section fournit des informations sur l’utilisation du service Places avec les notifications push dans Campaign Standard.
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
TQID: https://experienceleague.adobe.com/tjJD7Qn27sp8wnNcNdjnANIveyzjG1PZ--3C3rCjrMQ
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314id: e43347a8-f2c5-4aa4-8623-6f13875d7e3aid: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: c132d929-fa62-4271-803e-b823be07b914id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 1026
ht-degree: 4%

---

# Notifications push avec le service Places {#push-notifications}

Dans cette section, vous apprendrez à utiliser les informations de géolocalisation historiques pour cibler les notifications push diffusées via Adobe Campaign Standard.

## Conditions préalables

Avant de commencer, effectuez les tâches suivantes :

* Ayez une application mobile configurée avec le SDK Mobile Adobe Experience Platform, y compris l&#39;extension [Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Intégrez le [Adobe Experience Platform Mobile SDK](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) dans votre application.
* Ajoutez l’extension [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) à votre configuration d’application mobile.

* [Créez un point d’intérêt](/help/poi-mgmt-ui/create-a-poi-ui.md) dans l’interface de gestion des points d’intérêt du service Places.

* Activez et installez l’extension [ Places ](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Création d’éléments de données dans Experience Platform Launch

Après avoir vérifié que l’extension Places et une solution de surveillance des régions ([documentation CoreLocation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) pour iOS ou [documentation sur l’emplacement d’Android](https://developer.android.com/training/location/geofencing)) fonctionnent correctement dans votre application, vous devez créer des éléments de données dans Experience Platform Launch. Les éléments de données vous permettent de lire les informations fournies par les extensions qui transitent par le hub d’événements Mobile SDK et d’agir comme un alias pour récupérer les données de l’application cliente. Pour récupérer les données des extensions Places et envoyer les informations du Service Places à Campaign, vous devez créer quelques éléments de données.

Pour créer un élément de données :

1. Dans la propriété mobile Experience Platform Launch, cliquez sur l’onglet **[!UICONTROL Data Elements]**, puis sur **[!UICONTROL Add Data Element]**.
1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Places Service]**.
1. Dans la liste déroulante **[!UICONTROL Type d’élément de données]**, sélectionnez **[!UICONTROL Nom]**.
1. Dans le volet de droite, vous pouvez sélectionner **[!UICONTROL Point d’intérêt actuel]** qui récupère le nom du point d’intérêt dans lequel se trouve actuellement l’utilisateur.

   **[!UICONTROL Dernière entrée]** récupère le nom du point d’intérêt que l’utilisateur a saisi en dernier, et **[!UICONTROL Dernière sortie]** fournit le nom du dernier point d’intérêt que l’utilisateur a quitté. Dans cet exemple, nous avons sélectionné **[!UICONTROL Dernière saisie]** et saisi un nom pour l’élément de données, tel que **[!UICONTROL Nom du point d’intérêt saisi en dernier]** puis cliqué sur **[!UICONTROL Enregistrer]**.

   ![« Messages push dans Campaign Standard« ](/help/assets/ACS_Push1.png)

1. Répétez les étapes 1 à 4 ci-dessus et créez des éléments de données pour *Latitude du point d’intérêt saisi en dernier*, *Longitude du point d’intérêt saisi en dernier* et *Rayon du point d’intérêt saisi en dernier*.

Outre les éléments de données pour Places Service, veillez à créer des éléments de données principaux mobiles pour *ID de l’application* et *Experience Cloud ID*.

## Création d’une règle pour envoyer des données d’emplacement à Adobe Campaign Standard

Les règles d’Experience Platform Launch vous permettent de créer des workflows complexes et multi-solutions basés sur des déclencheurs d’événement. Grâce aux règles, vous pouvez créer des règles ou modifier des règles existantes et déployer les mises à jour de manière dynamique sur vos applications mobiles. Dans l’exemple suivant, la règle sera déclenchée lorsqu’un utilisateur saisit un point d’intérêt géoréférencé. Une fois la règle déclenchée, une mise à jour est envoyée à Campaign Standard pour enregistrer une entrée dans un point d’intérêt spécifique pour un utilisateur particulier en fonction de l’Experience Cloud ID.

1. Dans la propriété mobile Experience Platform Launch, dans l’onglet **[!UICONTROL Règles]**, cliquez sur **[!UICONTROL Ajouter une règle]**.
1. Dans la section **[!UICONTROL Événements]**, cliquez sur **[!UICONTROL +]** et sélectionnez **[!UICONTROL Service Places]** comme extension.
1. Pour le **[!UICONTROL Type d’événement]**, sélectionnez **[!UICONTROL Saisir un point ciblé]**.
1. Nommez la règle, par exemple **POI saisi par l’utilisateur**.
1. Cliquez sur **[!UICONTROL Conserver les modifications]**.
1. Ne renseignez pas la section **[!UICONTROL Conditions]**.

   Cette section vous permet de filtrer ou de placer des restrictions sur le moment où cette règle doit se déclencher.

1. Dans la section **[!UICONTROL Actions]**, cliquez sur **[!UICONTROL +]**.
1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Mobile Core]** et dans la liste déroulante **[!UICONTROL Type d’action]**, sélectionnez **[!UICONTROL Envoyer le postback]**.
1. Dans **[!UICONTROL URL]**, vous devez créer le point d’entrée des emplacements Campaign Standard.

   L’URL doit ressembler à `https:///rest/head/mobileAppV5//locations/`.
Assurez-vous d’utiliser les éléments de données corrects que vous avez créés précédemment pour votre serveur Campaign et pKey.

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
1. Dans **[!UICONTROL Type de contenu]**, saisissez **[!UICONTROL application/json]**.
1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

>[!IMPORTANT]
>
>* Il peut s’avérer utile de configurer un hook web Slack en tant qu’action supplémentaire pour vérifier que les entrées sont déclenchées et que les données appropriées sont collectées.
>* N’oubliez pas de publier les modifications récentes apportées à votre application pour vous assurer que la règle et tous vos éléments de données sont déployés dans le cadre de votre configuration. Après avoir publié, relancez l’application mobile pour obtenir les dernières mises à jour de configuration.

## Utilisation des données d’emplacement pour cibler les messages de campagne

Maintenant que des données de localisation sont renseignées dans Campaign, nous pouvons utiliser les points d’intérêt comme outil de segment d’audience.

1. Dans votre instance Adobe Campaign Standard, cliquez sur **[!UICONTROL Créer une notification push]**.
1. Pour le type de notification push, sélectionnez **[!UICONTROL Envoyer un push aux profils Campaign]**.
1. Cliquez sur **[!UICONTROL Suivant]** et saisissez les détails généraux.
1. Dans l’écran Audience , cliquez sur **[!UICONTROL Comptage]** pour déterminer le nombre estimé d’utilisateurs auxquels la notification push sera envoyée.

   >[!TIP]
   >
   >Dans cet exemple, le nombre sera de 3, car il y a trois périphériques installés sur lesquels l’application est testée.

1. Dans le volet de gauche, développez l’onglet **[!UICONTROL Profil]** et faites glisser le filtre **[!UICONTROL Emplacement du point d’intérêt]** vers la zone principale.
1. Dans la fenêtre Filtre de point d’intérêt , saisissez le nom exact du point d’intérêt que vous souhaitez cibler.

   >[!TIP]
   >
   >Vous pouvez effectuer des sélections supplémentaires pour déterminer la période écoulée depuis la dernière visite de l’utilisateur dans ce point d’intérêt.

   ![« Messages push 2 dans ACS »](/help/assets/ACS_push2.png)

1. Cliquez sur **[!UICONTROL Confirmer]**.
1. Exécutez à nouveau le comptage en haut pour voir la modification de la taille de votre audience.

   Si vous ne voyez pas la mise à jour de votre nombre, il se peut que vous ayez saisi un nom de point d’intérêt pour lequel aucun appareil n’a déclenché d’entrée. Le hook web Slack devient utile dans cette situation, car vous pouvez voir une liste des entrées de point d’intérêt de divers appareils de test.

1. Vous pouvez faire glisser des filtres d’emplacement de point d’intérêt supplémentaires pour inclure plusieurs points d’intérêt dans votre message.
1. Cliquez sur **[!UICONTROL Suivant]** pour terminer la création de la notification Push de diffusion.

   ![« Messagerie push 3 dans ACS »](/help/assets/ACS_push3.png)

L’utilisation du service Places avec Adobe Campaign Standard vous offre un outil puissant pour segmenter et cibler vos messages vers les utilisateurs en fonction des entrées et des sorties de clôture géographique. Cette intégration vous permet de créer des cas d’utilisation plus personnalisés et contextuels.
