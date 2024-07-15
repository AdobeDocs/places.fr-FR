---
title: Accéder au service Places
description: Cette section fournit des informations sur la manière d'ajouter un utilisateur à Places Service et un Experience Platform Launch, de sorte que l'utilisateur puisse accéder au service Places.
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
source-git-commit: c9058e9b70c2ef97151078f43913963471730bd2
workflow-type: tm+mt
source-wordcount: '907'
ht-degree: 1%

---

# Accéder au service Places {#adding-user-launch-places}

Places Service est désormais disponible dans l’interface utilisateur de collecte de données. Vous pouvez accéder à la collecte de données à partir du menu d’accès rapide sur [Adobe Experience Cloud home](https://experience.adobe.com?lang=fr).

![menu d’accès rapide](/help/assets/quickaccess.png)

Vous pouvez également accéder à la collecte de données à partir du menu Adobe Experience Platform :

![Menu Experience Platform](/help/assets/solutionaccessmenu.png)

Si votre ID utilisateur y a accès, l’icône du service Places s’affiche dans le panneau de gauche sous Data Management dans Data Collection, comme indiqué ci-dessous :

![Panneau de gauche Collecte de données](/help/assets/places_in_data_collection.png)

Si vous ne voyez pas le service Places à cet emplacement, contactez un administrateur de votre entreprise pour ajouter votre ID utilisateur à Adobe Experience Platform dans l’Admin Console.

## Ajout d’un utilisateur pour accéder à Places Service et à la collecte de données Experience Adobe Experience Platform

Places est désormais inclus dans Adobe Experience Platform. Pour permettre aux utilisateurs d&#39;accéder au [service Places](https://experience.adobe.com/#/data-collection/places), ils doivent être ajoutés à Adobe Experience Platform dans l&#39;Admin Console en tant qu&#39;utilisateur. Pour permettre aux utilisateurs d’accéder à la collecte de données Experience Platform avec les autorisations requises pour configurer les propriétés mobiles et utiliser Places avec le SDK Adobe Experience Platform, ils doivent également être ajoutés à la collecte de données Adobe Experience Platform dans l’Admin Console et se voir attribuer les autorisations suivantes pour la collecte de données Adobe Experience Platform :

* Toutes les autorisations sous Droits de propriété :
   * Approuver
   * Développer
   * Modifier la propriété
   * Gérer les environnements
   * Gérer les extensions
   * Publier
* Gérer l’autorisation Propriétés sous Droits d’entreprise

Si c’est la première fois que vous ajoutez un utilisateur, procédez comme suit pour ajouter des utilisateurs à la collecte de données Adobe Experience Platform et à Adobe Experience Platform. Si vous avez déjà ajouté des utilisateurs, plusieurs profils peuvent s’afficher. Veillez donc à sélectionner le profil correct.

>[!IMPORTANT]
>
>Seuls les administrateurs de l’organisation peuvent accéder à l’Admin Console et ajouter les utilisateurs.

### 1. Vérifiez que la collecte de données Adobe Experience Platform et Adobe Experience Platform sont configurées.

1. Connectez-vous à votre organisation Experience Cloud, [Adobe Experience Cloud home](https://experience.adobe.com).
1. Dans le coin supérieur droit, cliquez sur le sélecteur de shell Experience Cloud pour afficher un menu déroulant.

   ![sélecteur de shell](/help/assets/places_shell_switcher1.png)

1. Au bas de la liste, cliquez sur **[!UICONTROL Admin Console]**. (Un lien vers l’ **[!UICONTROL Admin Console]** se trouve également dans la section Accès rapide ).

   Si vous ne voyez pas **[!UICONTROL Admin Console]** dans la liste, vous n’êtes pas administrateur. Vous devez contacter votre administrateur d’organisation pour terminer cette procédure.

1. Dans l’Admin Console, si vous avez accès à plusieurs organisations, vérifiez que la bonne organisation est sélectionnée en haut à droite de la page.

   Il s’agit de l’organisation à laquelle vous allez ajouter vos utilisateurs. Si la bonne organisation n’a pas été sélectionnée, cliquez sur l’organisation et sélectionnez la bonne organisation dans la liste déroulante.

   >[!IMPORTANT]
   >
   >Si l’organisation souhaitée ne figure pas dans la liste déroulante, cela signifie que vous n’avez pas d’accès administrateur à cette organisation.

1. Dans l’Admin Console, cliquez sur l’onglet Produits et vérifiez que les cartes pour **[!UICONTROL Collecte de données Adobe Experience Platform]** et **[!UICONTROL Adobe Experience Platform]** s’affichent.

   ![](/help/assets/places_provisioned1.png)

   Ces deux produits sont automatiquement configurés pour toutes les organisations. Ils doivent donc être présents.


### 2. Ajouter un utilisateur à ces produits

#### Ajout d’un utilisateur pour permettre l’accès à l’interface utilisateur de Places Service

1. Dans l’onglet Produits , cliquez sur la carte **[!UICONTROL Adobe Experience Platform]** .
2. Un utilisateur peut être ajouté à n’importe quel profil dans **[!UICONTROL Adobe Experience Platform]** pour accéder à Places, aucune autorisation spécifique ne doit être définie.
3. Choisissez un profil (s’il en existe plusieurs) et cliquez dessus pour l’ouvrir.
4. Cliquez sur le bouton bleu **Ajouter un utilisateur**, renseignez l’utilisateur avec son Adobe ID et son nom, puis cliquez sur Enregistrer pour terminer l’ajout.

#### Ajout d’un utilisateur à la collecte de données

1. Dans l’onglet Produits , cliquez sur la carte **[!UICONTROL Collecte de données Adobe Experience Platform]** .
2. Par défaut, un profil nommé **Default Data Collection All Access** a été créé. L’ajout d’un utilisateur à ce profil lui garantit les autorisations appropriées pour travailler avec Places Service et la collecte de données. Si un autre profil est sélectionné, assurez-vous que les autorisations mentionnées ci-dessus sont incluses.
3. Choisissez un profil (s’il en existe plusieurs) et cliquez dessus pour l’ouvrir.
4. Cliquez sur le bouton bleu **Ajouter un utilisateur**, renseignez l’utilisateur avec son Adobe ID et son nom, puis cliquez sur Enregistrer pour terminer l’ajout.

#### Ajoutez un utilisateur en tant que développeur pour Places Service.

Pour les utilisateurs qui doivent également accéder à l’API REST Places Service, vous devez les ajouter en tant que développeur.
1. Dans l’onglet Produits , cliquez sur la carte **[!UICONTROL Adobe Experience Platform]** .
2. Si l&#39;utilisateur a déjà été ajouté à la carte **[!UICONTROL Adobe Experience Platform]** via les instructions ci-dessus, sélectionnez le même profil précédemment utilisé et cliquez dessus.
3. Dans le profil, cliquez sur l’onglet **Développeurs**
4. Cliquez sur le bouton bleu **Ajouter un développeur** , renseignez l’utilisateur avec son Adobe ID et son nom, puis cliquez sur Enregistrer pour terminer l’ajout.

Une fois les étapes ci-dessus terminées, l’utilisateur reçoit un courrier électronique l’informant qu’il a accès à **[!UICONTROL Adobe Experience Platform]** et à la **[!UICONTROL collecte de données Adobe Experience Platform]**. Ils peuvent alors se connecter à [Adobe Experience Cloud](https://experience.adobe.com) pour cette organisation et accéder au service Places et à la collecte de données. Si vous effectuez également les étapes **[!UICONTROL Ajouter un développeur]**, l’utilisateur peut également se connecter à [Adobe Developer Console](https://developer.adobe.com/console/home) pour créer un projet qui donnerait accès à l’API REST du service Places.
