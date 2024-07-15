---
title: Notifications push avec Places Service
description: Cette section fournit des informations sur l’utilisation du service Places avec des notifications push en Campaign Standard.
exl-id: 4b50f552-deb8-49cd-9221-fbbf33aaa5f9
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '981'
ht-degree: 2%

---

# Notifications push avec le service Places {#push-notifications}

Dans cette section, vous apprendrez comment utiliser les informations de géolocalisation historiques pour cibler les notifications push diffusées via Adobe Campaign Standard.

## Conditions préalables

Avant de commencer, effectuez les tâches suivantes :

* Ayez une application mobile configurée avec le SDK Mobile Adobe Experience Platform, y compris l’ [extension Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard).

* Intégrez le [SDK Adobe Experience Platform Mobile](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) à votre application.
* Ajoutez l’[extension Adobe Campaign Standard](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) à la configuration de votre application mobile.

* [Créez un point ciblé](/help/poi-mgmt-ui/create-a-poi-ui.md) dans l’interface de gestion des points ciblés du service Places.

* Activez et installez l’ [extension Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).


## Création d’éléments de données dans Experience Platform Launch

Après avoir vérifié que l’extension Places et une solution de surveillance de région ([CoreLocation documentation](https://developer.apple.com/documentation/corelocation/monitoring_the_user_s_proximity_to_geographic_regions) pour iOS ou [Android Location documentation](https://developer.android.com/training/location/geofencing)) fonctionnent correctement dans votre application, vous devez créer des éléments de données dans Experience Platform Launch. Les éléments de données vous permettent de lire les informations fournies par les extensions provenant du hub d’événements du SDK Mobile et d’agir comme un alias pour récupérer les données de l’application cliente. Pour récupérer les données des extensions Places et envoyer les informations du service Places à Campaign, vous devez créer quelques éléments de données.

Pour créer un élément de données :

1. Dans la propriété mobile de votre Experience Platform Launch, cliquez sur l’onglet **[!UICONTROL Data Elements]** et cliquez sur **[!UICONTROL Ajouter un élément de données]**.
1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Places Service]**.
1. Dans la liste déroulante **[!UICONTROL Type d’élément de données]**, sélectionnez **[!UICONTROL Nom]**.
1. Dans le volet de droite, vous pouvez sélectionner **[!UICONTROL POI actuel]** qui récupère le nom du POI dans lequel l’utilisateur se trouve actuellement.

   **[!UICONTROL Dernière entrée]** récupère le nom du point ciblé que l’utilisateur a saisi pour la dernière fois et **[!UICONTROL Dernière sortie]** fournit le nom du point ciblé que l’utilisateur a laissé pour la dernière fois. Dans cet exemple, nous avons sélectionné **[!UICONTROL Dernière entrée]** et saisi un nom pour l’élément de données, tel que **[!UICONTROL Nom du dernier point d’entrée]**, puis cliqué sur **[!UICONTROL Enregistrer]**.

   ![&quot;Messagerie push en Campaign Standard&quot;](/help/assets/ACS_Push1.png)

1. Répétez les étapes 1 à 4 ci-dessus et créez des éléments de données pour *Latitude du dernier POI d’entrée*, *Longitude du dernier POI d’entrée* et *Rayon du dernier POI d’entrée*.

Outre les éléments de données pour Places Service, veillez à créer des éléments de données Mobile Core pour *ID d’application* et *ID d’Experience Cloud*.

## Création d’une règle pour envoyer des données d’emplacement à Adobe Campaign Standard

Les règles dans Experience Platform Launch vous permettent de créer des processus complexes et multi-solutions basés sur des déclencheurs d’événement. Avec les règles, vous pouvez créer de nouvelles règles ou modifier des règles existantes et déployer dynamiquement les mises à jour dans vos applications mobiles. Dans l’exemple suivant, la règle sera déclenchée lorsqu’un utilisateur entre dans un point ciblé géociblé. Une fois la règle déclenchée, une mise à jour est envoyée au Campaign Standard afin d’enregistrer une entrée dans un point ciblé spécifique pour un utilisateur spécifique en fonction de l’ID Experience Cloud.

1. Dans la propriété mobile de votre Experience Platform Launch, sur l’onglet **[!UICONTROL Rules]**, cliquez sur **[!UICONTROL Add Rule]**.
1. Dans la section **[!UICONTROL Events]**, cliquez sur **[!UICONTROL +]** et sélectionnez **[!UICONTROL Places Service]** comme extension.
1. Pour le **[!UICONTROL Type d’événement]**, sélectionnez **[!UICONTROL Saisir le POI]**.
1. Nommez la règle, par exemple **L’utilisateur a saisi le point ciblé**.
1. Cliquez sur **[!UICONTROL Conserver les modifications]**.
1. Laissez la section **[!UICONTROL Conditions]** vide.

   Cette section vous permet de filtrer ou d’appliquer des restrictions sur le moment où cette règle doit se déclencher.

1. Sous la section **[!UICONTROL Actions]**, cliquez sur **[!UICONTROL +]**.
1. Dans la liste déroulante **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Mobile Core]** et dans la liste déroulante **[!UICONTROL Action Type]**, sélectionnez **[!UICONTROL Send Postback]**.
1. Dans **[!UICONTROL URL]**, vous devez construire votre point de terminaison des emplacements de Campaign Standard.

   L’URL doit ressembler à `https:///rest/head/mobileAppV5//locations/`.
Assurez-vous d’utiliser les éléments de données corrects que vous avez créés précédemment pour votre serveur Campaign et votre clé publicitaire.

1. Cliquez sur la case pour ajouter un corps de publication et envoyez les éléments suivants :

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

1. Assurez-vous d’utiliser les éléments de données que vous avez créés dans la section précédente.
1. Dans **[!UICONTROL Type de contenu]**, saisissez **[!UICONTROL application/json]**.
1. Cliquez sur **[!UICONTROL Conserver les modifications]**.

>[!IMPORTANT]
>
>* Il peut s’avérer utile de configurer un crochet web de Slack comme action supplémentaire pour vérifier que les entrées sont déclenchées et que les données appropriées sont collectées.
>* N’oubliez pas de publier les modifications récentes apportées à votre application pour vous assurer que la règle et tous vos éléments de données sont déployés dans le cadre de votre configuration. Après la publication, lancez à nouveau l’application mobile pour obtenir les dernières mises à jour de configuration.

## Utiliser les données de localisation pour cibler les messages de Campaign

Maintenant que les données de localisation sont renseignées dans Campaign, nous pouvons utiliser les points ciblés comme outil de segmentation d’audience.

1. Dans votre instance Adobe Campaign Standard, cliquez sur **[!UICONTROL Créer une notification push]**.
1. Pour le type de notification push, sélectionnez **[!UICONTROL Envoyer une notification push aux profils Campaign]**.
1. Cliquez sur **[!UICONTROL Suivant]** et saisissez les détails généraux.
1. Dans l’écran Audience, cliquez sur **[!UICONTROL Comptage]** pour déterminer le nombre estimé d’utilisateurs auxquels la notification push sera envoyée.

   >[!TIP]
   >
   >Dans cet exemple, le nombre sera de 3, car l’application est en cours de test sur trois périphériques installés.

1. Dans le volet de gauche, développez l’onglet **[!UICONTROL Profil]** et faites glisser le filtre **[!UICONTROL Emplacement du POI]** vers la zone principale.
1. Dans la fenêtre de filtrage des points ciblés, saisissez le nom exact du point ciblé que vous souhaitez cibler.

   >[!TIP]
   >
   >Vous pouvez effectuer des sélections supplémentaires pour déterminer la période depuis la dernière visite de l’utilisateur à ce point ciblé.

   ![&quot;Messagerie push 2 dans ACS&quot;](/help/assets/ACS_push2.png)

1. Cliquez sur **[!UICONTROL Confirmer]**.
1. Effectuez à nouveau le décompte en haut pour voir la taille de votre audience changer.

   Si vous ne voyez pas votre mise à jour de comptage, vous avez peut-être saisi un nom de point ciblé pour lequel aucun périphérique n’a déclenché d’entrée. Le point d’extension web du Slack s’avère utile dans ce cas, car vous pouvez voir la liste des entrées de points ciblés de différents appareils de test.

1. Vous pouvez faire glisser d’autres filtres d’emplacement des points ciblés pour inclure plusieurs points ciblés dans votre message.
1. Cliquez sur **[!UICONTROL Suivant]** pour terminer la création de la notification Push de diffusion.

   ![&quot;Messagerie push 3 dans ACS&quot;](/help/assets/ACS_push3.png)

L’utilisation de Places Service avec Adobe Campaign Standard vous offre un outil puissant pour segmenter et cibler vos messages vers les utilisateurs en fonction des entrées et des sorties de géo-barrières. Cette intégration vous aide à créer des cas d’utilisation plus personnalisés et contextuels.
