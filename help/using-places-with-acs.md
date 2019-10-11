---
title: Utilisation de lieux avec Adobe Campaign Standard
seo-title: Utilisation de lieux avec Adobe Campaign Standard
description: Une bonne compréhension des préférences et des habitudes de vos clients est essentielle à toute campagne de marketing réussie. Le fait de savoir si un utilisateur a visité un emplacement physique peut également ajouter un contexte très utile pour établir une relation avec le consommateur.
seo-description: Une bonne compréhension des préférences et des habitudes de vos clients est essentielle à toute campagne de marketing réussie. Le fait de savoir si un utilisateur a visité un emplacement physique peut également ajouter un contexte très utile pour établir une relation avec le consommateur.
translation-type: tm+mt
source-git-commit: d7c5fe5d7a20a647240114d25307373b493ae2f5

---


# Utilisation de lieux avec Adobe Campaign Standard {#places-with-acs}

*Merci de nous avoir rendu visite la semaine dernière, nous aimerions vous offrir une surprise pour votre prochaine visite !*

Une bonne compréhension des préférences et des habitudes de vos clients est essentielle à toute campagne de marketing réussie. Les éléments recherchés par un utilisateur et l’historique d’achat précédent jouent un rôle important dans le ciblage du public. Le fait de savoir si un utilisateur a visité un emplacement physique peut également ajouter un contexte très utile pour établir une relation avec le consommateur.

Selon un rapport récent d'eMarketer, 85 % des détaillants très performants estiment que l'emplacement est très important pour leurs efforts de marketing. De plus, plus de 58 % des détaillants d’Amérique du Nord prévoient investir dans des technologies de proximité et de localisation afin d’améliorer l’expérience de leurs clients.

![](/help/assets/using-loc-services-acs_0.png)

Pensez à l’emplacement essentiel de votre expérience d’utilisation des smartphones. À quelle fréquence demandez-vous à votre smartphone de trouver des restaurants, des stations d'essence, des épiceries ou d'autres services à proximité.

Il est donc logique qu’en tant que marque, vous réfléchissiez à des façons d’exploiter l’emplacement dans vos campagnes marketing. Ce guide explique comment exploiter la puissance du service d’emplacement de la plate-forme Adobe Experience Platform pour ajouter un contexte d’emplacement à la messagerie via Adobe Campaign Standard, afin de vous permettre d’afficher des notifications Push personnalisées ou des messages in-app basés sur l’entrée de point d’intérêt historique.

Avant de commencer, ce guide suppose que vous disposez d’une application mobile configurée avec le SDK mobile Adobe Experience Platform avec l’extension Adobe Campaign Standard. Outre Adobe Experience Platform Mobile SDK et Campaign Standard, vous devez avoir accès au service d’emplacement de la plateforme d’expérience.

## Conditions préalables 

1. Intégrez le SDK [mobile](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform à votre application.
1. Ajoutez [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) à la configuration de votre application mobile.
1. [Créez un ou plusieurs points d’intérêt](/help/places-database-management-1/managing-pois-in-the-places-ui.md).

>[!TIP]
>
>Si vous recherchez des méthodes de téléchargement en masse ou de gestion des points d’intérêt, examinez ce [script pour télécharger des points d’intérêt à partir d’un fichier CSV](https://github.com/adobe/places-scripts) . De plus, les API [Places](/help/places-rest-apis/api-usage/api-usage.md) peuvent être utilisées pour créer ou gérer des points d’intérêt.

Si vous n'avez pas accès à Places, vous pouvez [demander l'accès ici](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u).

### Activation et installation des extensions Places dans votre application

Après avoir créé des points d’intérêt dans l’interface Lieux, vous devrez ajouter la fonctionnalité Lieux à votre application.

1. Suivez les instructions pour activer les extensions du moniteur des lieux et des lieux dans votre application.
1. Dans l’extension Places, vérifiez que vous avez sélectionné la bibliothèque appropriée des points d’intérêt que vous avez créés précédemment.

   D’autres bibliothèques peuvent être ajoutées à la configuration de l’extension à tout moment.

1. Vérifiez que vous avez ajouté ces configurations à une bibliothèque et publié les modifications de configuration dans Launch.
1. Dans l'onglet **[UICONTROL Launch Environnements]** , cliquez sur l'icône des instructions d'installation pour afficher les instructions de téléchargement des fichiers CocoaPod et Gradle appropriés vers votre projet d'application.
1. Dans votre application, suivez les instructions pour ajouter le mode d’arrière-plan Emplacement à votre application et démarrez le moniteur de lieux.
1. Testez votre application via un simulateur de périphérique pour voir la demande d’application à proximité des points d’intérêt en fonction de l’usurpation de l’emplacement du périphérique.

### Création d’éléments de données dans le lancement de la plateforme d’expérience

Une fois que vous avez vérifié que les extensions Places et Places Monitor fonctionnent correctement dans votre application, créez des éléments de données dans le lancement de la plate-forme d’expérience afin de lire les informations fournies par les extensions et provenant du concentrateur d’événements du SDK mobile. Les éléments de données agissent essentiellement comme un alias pour récupérer les données de l’application cliente. Créons quelques éléments de données pour récupérer les données des extensions Places.

1. Dans votre propriété Experience Platform Launch mobile, sur l’ **[!UICONTROL Data Elements]** onglet et cliquez sur **[!UICONTROL Add Data Element]**.
1. Dans le menu de l'extension, sélectionnez **[!UICONTROL Places]**.
1. Dans la liste **[!UICONTROL Data Element]** déroulante, sélectionnez **[!UICONTROL Name}**.
1. Dans la fenêtre à droite, vous pouvez sélectionner **[!UICONTROL Current POI]** qui va récupérer le nom du point d’accès dans lequel se trouve actuellement l’utilisateur.

   * **[!UICONTROL Last Entered]** récupère le nom de l’API que l’utilisateur a saisi pour la dernière fois dans une
   * **[!UICONTROL Last Exited]** fournira le nom du point d’accès que l’utilisateur a quitté pour la dernière fois.

1. Sélectionnez **[!UICONTROL Last Entered]**.
1. Tapez le nom de l’élément de données, par exemple **[!UICONTROL Last Entered POI Name]**, puis cliquez sur **[!UICONTROL Save]**.


   ![](/help/assets/using-loc-services-acs_1.png)

1. Répétez les mêmes étapes ci-dessus et créez des éléments de données pour la latitude *de la* dernière page d’entrée, la longitude *de la* dernière entrée, le rayon ** de la dernière entrée.

Outre les éléments de données pour Places, veillez à créer également des éléments de données de base Mobile pour l’ID *d’* application et l’ID ** Experience Cloud.

### Création d’une règle pour envoyer des données d’emplacement à Adobe Campaign Standard

Les règles de lancement de plate-forme d’expérience vous permettent de créer des flux de travail complexes à plusieurs solutions en fonction de déclencheurs d’événements. Vous pouvez en créer de nouvelles ou apporter des modifications aux règles existantes et faire en sorte que les mises à jour soient déployées dynamiquement dans vos applications mobiles. Dans cet exemple, nous allons créer une règle qui est déclenchée lorsqu’un utilisateur entre dans un point d’accès géoclôturé. Une fois la règle déclenchée, une mise à jour est envoyée à Campaign Standard pour enregistrer une entrée dans un point d’accès spécifique pour l’utilisateur. Ce point d’accès repose sur l’ID Experience Cloud.

1. Dans votre propriété Experience Platform Launch mobile, cliquez sur l’ **[!UICONTROL Rules]** onglet et sur **[!UICONTROL Add Rule]**.
1. Dans la **[!UICONTROL Events]** section, cliquez sur **[!UICONTROL +]** et sélectionnez **[!UICONTROL Places]**.
1. Dans **[!UICONTROL Event Type]**, sélectionnez **[!UICONTROL Enter POI]**.
1. Entrez un nom pour la règle, par exemple **[!UICONTROL User entered POI]**.
1. Cliquez sur **[!UICONTROL Keep Changes]** (Nouvelle propriété).
1. Laissez la **[!UICONTROL Conditions]** section vide.

   Cette section vous permet de filtrer ou d’imposer des restrictions sur le moment où cette règle doit se déclencher.

1. In the **[!UICONTROL Actions]** section, click **[!UICONTROL +]**.
1. Dans **[!UICONTROL Extension]**, sélectionnez **[!UICONTROL Mobile Core]** et, dans **[!UICONTROL Action Type]**, sélectionnez **[!UICONTROL Send Postback]**.

1. Pour l’URL, vous devez construire votre point de terminaison d’emplacements Campaign Standard.

   L’URL doit ressembler à celle ci-dessous. Veillez à utiliser les éléments de données corrects que vous avez créés précédemment pour votre serveur Campaign et votre clé publicitaire.

   `https://{%%camp-server%%}/rest/head/mobileAppV5/{%%pkey%%}/locations/`

1. Cliquez sur la zone pour ajouter un corps de publication et envoyer les éléments suivants :

   ```text
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

1. Utilisez les éléments de données spécifiques que vous avez créés dans la section précédente.
1. Dans **[!UICONTROL Content Type]**, saisissez **[!UICONTROL application/json]**.
1. Cliquez **[!UICONTROL Keep Changes]** une fois cette configuration effectuée.

   Il peut s’avérer utile de configurer un crochet Web Spénurie en tant qu’action supplémentaire pour vérifier que mon action est déclenchée et que les données appropriées sont collectées.

   >[!IMPORTANT]
   >
   >N’oubliez pas de publier les modifications récentes apportées à votre application pour vous assurer que la règle et tous vos éléments de données sont déployés dans le cadre de votre configuration. Après la publication, vous devez relancer l’application mobile pour obtenir les dernières mises à jour de configuration.

### Utiliser les données d’emplacement pour cibler les messages de Campaign Standard

Maintenant que les données d’emplacement sont renseignées dans Campaign, nous pouvons utiliser les points ciblés comme outil de segmentation de l’audience.

1. Dans l’instance Adobe Campaign Standard, cliquez sur **[UICONTROL Create Push Notification]**.
1. Pour le type de notification Push, sélectionnez **[UICONTROL Send push to app subscribers (UICONTROL Envoyer Push aux abonnés]** de l’application).

   Ce type de push ciblera tous les utilisateurs de votre application. Si vos utilisateurs de mobiles sont associés à un profil de campagne, vous pouvez également sélectionner **[UICONTROL Send push to Campaign profiles]** i.

1. Cliquez sur **[!UICONTROL Next]** et saisissez les détails généraux dans l’écran suivant.
1. Dans l’écran Public, cliquez sur **[!UICONTROL Count]** pour connaître le nombre estimé d’utilisateurs qui recevront la notification Push.

   Dans ce cas, le nombre est de trois, car trois périphériques sont installés sur l’application de test.

1. Dans la barre latérale gauche, développez l’ **[!UICONTROL Profile]** onglet et faites glisser le **[!UICONTROL POI location]** filtre sur la zone principale.
1. Dans la fenêtre de filtre d’API, entrez le nom exact de l’API que vous souhaitez cibler.

   Vous pouvez effectuer des sélections supplémentaires afin de déterminer la période écoulée depuis la dernière visite de l’utilisateur dans ce point d’intérêt.

   ![](/help/assets/using-loc-services-acs_2.png)

1. Cliquez sur [!**Confirmation]UICONTROL**.
1. Exécutez à nouveau le compte en haut pour voir la taille de votre audience changer.

   Si vous ne voyez pas la mise à jour de votre compte, vous avez peut-être saisi un nom d’API pour lequel aucun périphérique n’a déclenché une entrée. C'est là que le crochet web Slack devient précieux, car vous pouvez voir la liste des entrées de point d'accès de différents périphériques de test.
1. Vous pouvez faire glisser d’autres filtres d’emplacement de point d’intérêt pour inclure plusieurs points d’intérêt dans votre message.
1. Cliquez sur **[!UICONTROL Next]** pour terminer la création de la notification Push en vue de la remise.

   ![](/help/assets/using-loc-services-acs_3.png)

Outre les notifications Push, vous pouvez également utiliser les données d’emplacement pour segmenter les utilisateurs qui souhaitent recevoir un message in-app.

1. Dans votre instance Adobe Campaign Standard, cliquez sur **[!UICONTROL Create In-App message]**.
1. Pour le type de message, sélectionnez **[!UICONTROL Target all users of a Mobile application]**.
1. Cliquez sur **[!UICONTROL Next]** et saisissez les détails généraux dans l’écran suivant.
1. Dans le volet de gauche, vérifiez que vous pouvez désormais utiliser divers déclencheurs liés aux emplacements.
1. Si l’utilisateur a saisi une clôture géographique de point d’accès, vous pouvez choisir d’afficher le message in-app.

   Vous pouvez également utiliser les métadonnées que vous avez définies dans l’interface utilisateur Lieux pour filtrer votre audience. Dans cet exemple, je veux déclencher un message in-app présenté uniquement aux utilisateurs qui ont quitté pour la dernière fois un point de contact qui avait également une fonction de gym. Peut-être que je veux leur envoyer un sondage pour voir s'ils ont utilisé/aimé la salle de gym.

1. Cliquez sur **[!UICONTROL Next]** pour terminer la création du message in-app en vue de la diffusion.

   ![](/help/assets/using-loc-services-acs_4.png)

L’utilisation de lieux avec Adobe Campaign Standard vous offre un outil très puissant pour segmenter et cibler vos messages sur les utilisateurs en fonction de leur emplacement historique. Cette simple intégration ouvre la porte à la création de cas d'utilisation plus personnalisés et contextuels.

Nous améliorons constamment Places et les solutions intégrées pour intégrer le contexte d’emplacement dans les processus mobiles. L'un des produits qui profitera de Places est la prochaine solution du voyage avec déclenchement qui permettra aux clients de créer des flux de travail en temps réel en fonction de déclencheurs d'événements tels que l'emplacement.

## Liens recommandés

Pour plus d’informations, voir :

* [Adobe Experience Location Service](https://www.adobe.com/experience-platform/location-service.html)
* [Adobe Campaign Standard ](https://www.adobe.com/marketing/campaign.html)
* [S’inscrire pour accéder à Adobe Places bêta](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u)
* [Adobe Experience Platform Mobile SDK](https://sdkdocs.com/)
* [Intégration d’Adobe Campaign avec SDK de plateforme d’expérience](https://helpx.adobe.com/campaign/kb/configuring-app-sdk.html)
