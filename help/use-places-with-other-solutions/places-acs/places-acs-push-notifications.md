---
title: Notifications Push
seo-title: Notifications Push
description: Cette section fournit des informations sur l’utilisation des emplacements avec des notifications Push dans Campaign Standard.
seo-description: 'Cette section fournit des informations sur l’utilisation des emplacements avec des notifications Push dans Campaign Standard. '
translation-type: tm+mt
source-git-commit: 0612e2fb06e45ff25ad580e3336be3eb48bb39b9

---


# Notifications Push avec le service d’emplacement de plateforme d’expérience {#push-notifications}

Ce guide explique comment utiliser les informations historiques de géolocalisation pour cibler les notifications Push diffusées via Adobe Campaign Standard.

>[!IMPORTANT]
>
>Avant de commencer, effectuez les tâches suivantes :
>
>* Configurez une application mobile avec le SDK mobile Adobe Experience Platform, y compris l’extension [](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard)Adobe Campaign Standard.
   >
   >
* Intégrez le SDK [mobile](https://aep-sdks.gitbook.io/docs/getting-started/get-the-sdk) Adobe Experience Platform à votre application.
>* Ajoutez [Adobe Campaign Standard Extension](https://aep-sdks.gitbook.io/docs/using-mobile-extensions/adobe-campaign-standard) à la configuration de votre application mobile.
   >
   >
* [Créez un point d’accès](/help/poi-mgmt-ui/create-a-poi-ui.md) dans l’interface de gestion des points d’accès.
   >
   >
* Activez et installez l’extension [Places](/help/places-ext-aep-sdks/places-extension/places-extension.md).



## Création d’éléments de données dans Experience Platform Launch

Après avoir vérifié que le moniteur des lieux et des lieux pour les extensions du service d’emplacement fonctionne correctement dans votre application, créez des éléments de données dans le lancement de la plateforme d’expérience. Les éléments de données vous permettent de lire les informations fournies par les extensions provenant du concentrateur d’événements Mobile SDK et d’agir comme un alias pour récupérer les données de l’application cliente. Créons quelques éléments de données pour récupérer les données des extensions Lieux, afin que nous puissions envoyer les informations Lieux à Campaign.

1. Dans la propriété mobile de lancement de plate-forme d’expérience, cliquez sur l’onglet Eléments **de** données, puis sur **Ajouter un élément** de données.
2. Dans la liste déroulante **Extension** , sélectionnez **Lieux**.
3. Dans la liste déroulante Type **d’élément de** données, sélectionnez **Nom**.
4. Dans le volet droit, vous pouvez sélectionner l’API **** active qui récupère le nom de l’API dans laquelle se trouve actuellement l’utilisateur.

   **La fonction Dernière entrée** récupère le nom du point d’accès saisi par l’utilisateur pour la dernière fois et la fonction **Dernière sortie** fournit le nom du point d’accès que l’utilisateur a laissé pour la dernière fois. Dans cet exemple, nous allons sélectionner **Dernière entrée** et taper un nom pour l’élément de données, tel que Nom **du point d’entrée** dernier et cliqué sur **Enregistrer**.

   !["Messagerie push dans Campaign Standard"](/help/assets/ACS_Push1.png)


5. Répétez les mêmes étapes ci-dessus et créez des éléments de données pour la Latitude _du point d’entrée_ dernier, la Longitude _du point d’entrée_ dernier et le rayon __ du point d’entrée dernier.

Outre les éléments de données du service d’emplacement, veillez à créer des éléments de données principaux pour Mobile pour l’ID __ d’application et l’ID __ Experience Cloud.

## Création d’une règle pour envoyer des données d’emplacement à Adobe Campaign Standard

Les règles de lancement de plate-forme d’expérience vous permettent de créer des processus complexes et multisolutions basés sur des déclencheurs d’événement. Ce qui est génial avec les règles, c’est que vous pouvez créer de nouvelles règles ou modifier des règles existantes et que les mises à jour soient dynamiquement déployées dans vos applications mobiles. Dans cet exemple, nous allons créer une règle qui sera déclenchée lorsqu’un utilisateur accède à un point d’accès géociblé. Une fois la règle déclenchée, une mise à jour est envoyée à Campaign pour enregistrer une entrée dans un point d’intérêt spécifique pour un utilisateur particulier en fonction de l’ID d’expérience Cloud.

1. Dans la propriété Launch mobile, cliquez sur l’onglet **Rules** et sur **Add Rule**.
2. Dans la section **Evénements** , cliquez sur **+** et sélectionnez **Lieux** comme extension.
3. Pour le type **d’** événement, sélectionnez **Entrer un point d’accès (POI**).
4. Attribuez un nom à la règle, par exemple, **l’utilisateur a saisi l’API**.
5. Click **Keep Changes**.
6. La section **Conditions** vous permet de filtrer ou d’imposer des restrictions quant au moment où cette règle doit se déclencher.  Pour l'instant, nous laisserons ce blanc.
7. Dans la section **Actions** , cliquez sur **+** pour créer une action.
8. Dans la liste déroulante **Extension** , sélectionnez **Mobile Core,** puis dans la liste déroulante Type **d’** action, sélectionnez **Envoyer le postback.**
9. Pour l’ **URL**, vous devez construire votre point de terminaison d’emplacements Campaign Standard.  L’URL doit ressembler à celle ci-dessous. Assurez-vous d’utiliser les éléments de données corrects que vous avez créés précédemment pour votre serveur Campaign et votre clé pKey. `https:///rest/head/mobileAppV5//locations/`
10. Cliquez sur la zone pour ajouter un corps de publication et envoyer les éléments suivants :

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

11. Vérifiez que vous utilisez les éléments de données que vous avez créés dans la section précédente.
12. Dans Type **de** contenu, saisissez **application/json**.
13. Cliquez sur **Conserver les modifications** après avoir configuré cette option.
14. Il peut s’avérer utile de configurer un crochet Web SBlack comme une action supplémentaire pour vérifier que les entrées sont déclenchées et que les données appropriées sont collectées.


>N’oubliez pas de publier les modifications récentes apportées à votre application pour vous assurer que la règle et tous vos éléments de données sont déployés dans le cadre de votre configuration. Après publication, vous devez relancer l’application mobile pour obtenir les dernières mises à jour de configuration.

## Utiliser des données d'emplacement pour cibler des messages de campagne

Maintenant que les données d’emplacement sont renseignées dans Campaign, nous pouvons utiliser les points d’intérêt comme outil de segmentation de l’audience.

1. Dans votre instance Adobe Campaign Standard, cliquez sur **Créer une notification** Push.
2. Pour le type de notification Push, sélectionnez **Envoyer la notification Push vers les profils** Campagne.
3. Cliquez sur **Suivant** et entrez les détails généraux dans l’écran suivant.
4. Dans l’écran Public, cliquez sur **Compter** pour connaître le nombre estimé d’utilisateurs qui recevront la notification Push.

   *Dans ce cas, mon nombre sera égal à trois, car j'ai trois périphériques que j'ai installés pour tester l'application.*

5. Dans la barre latérale gauche, développez l’onglet **Profil** et faites glisser le filtre d’emplacement **** du point d’accès (POI) vers la zone principale.
6. Dans la fenêtre de filtre d’API, entrez le nom exact de l’API que vous souhaitez cibler.

   *Vous pouvez effectuer des sélections supplémentaires afin de déterminer la période écoulée depuis la dernière visite de l’utilisateur dans ce point d’intérêt.*

   !["Messagerie push 2 in ACS"](/help/assets/ACS_push2.png)


7. Cliquez sur **Confirmer**.
8. Exécutez à nouveau le compte en haut pour voir la taille de votre audience changer.  Si vous ne voyez pas la mise à jour de votre compte, vous avez peut-être saisi un nom d’API pour lequel aucun périphérique n’a déclenché une entrée. C'est là que le crochet web Slack devient précieux, car vous pouvez voir la liste des entrées de point d'accès à partir de divers périphériques de test.
9. Vous pouvez faire glisser d’autres filtres d’emplacement de point d’intérêt pour inclure plusieurs points d’intérêt dans votre message.
10. Cliquez sur **Suivant** pour terminer la création de la notification Push en vue de sa remise.

   !["Messagerie push 3 in ACS"](/help/assets/ACS_push3.html)

L’utilisation du service d’emplacement avec Adobe Campaign Standard vous offre un outil puissant pour segmenter et cibler vos messages sur les utilisateurs en fonction des entrées et sorties de géolocalisation. Cette simple intégration ouvre la porte à la création de cas d'utilisation plus personnalisés et contextuels.