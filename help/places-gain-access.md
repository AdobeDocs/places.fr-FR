---
title: Accéder au service Places
description: Cette section fournit des informations sur la manière d’ajouter un utilisateur à Places Service et à Experience Platform Launch, afin qu’il puisse accéder à Places Service.
exl-id: f388945e-cf26-4694-9697-9fe564ae4b69
TQID: https://experienceleague.adobe.com/EYg1wjQJZeHqX7vPnJ1VUZzojqG6ANjS8-VBXV3y51c
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9id: f7bdf6be-dd3b-4d2d-ac52-0e62ed0d3102
feature_v2: id: c132d929-fa62-4271-803e-b823be07b914id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: b64298cc-90cc-46b7-8917-ee391f1c7516id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0id: f5efb499-54f9-432b-ac5c-599dbac103afid: f6ff4d13-7b5c-4533-8556-95e76673d4cb
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66id: ebde5b41-29c9-4f5e-9ef6-1197e85409e3
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 919
ht-degree: 2%

---

# Accéder au service Places {#adding-user-launch-places}

Places Service est désormais disponible dans l’interface utilisateur de la collecte de données. Vous pouvez accéder à la collecte de données à partir du menu d&#39;accès rapide sur la page d&#39;accueil de [](https://experience.adobe.com?lang=fr).

![menu accès rapide](/help/assets/quickaccess.png)

Vous pouvez également accéder à Collecte de données à partir du menu Adobe Experience Platform :

![Menu ](/help/assets/solutionaccessmenu.png)

Si votre identifiant utilisateur dispose d’un accès, l’icône Places Service s’affiche dans le panneau de gauche sous Gestion des données dans la collecte de données, comme indiqué ci-dessous :

![Panneau de gauche Collecte de données](/help/assets/places_in_data_collection.png)

Si le service Places ne s’affiche pas à cet emplacement, contactez un administrateur de votre organisation pour ajouter votre identifiant utilisateur à Adobe Experience Platform dans Admin Console.

## Ajout d’un utilisateur pour accéder au service Places et à la collecte de données Experience Adobe Experience Platform

Places est désormais inclus dans Adobe Experience Platform. Pour permettre aux utilisateurs d’accéder au [service Places](https://experience.adobe.com/#/data-collection/places), ils doivent être ajoutés en tant qu’utilisateur à Adobe Experience Platform dans Admin Console. Pour permettre aux utilisateurs d&#39;avoir accès à la collecte de données Experience Platform avec les autorisations requises pour configurer les propriétés mobiles et utiliser Places avec le SDK Adobe Experience Platform, ils doivent également être ajoutés à la collecte de données Adobe Experience Platform dans Admin Console et recevoir les autorisations suivantes pour la collecte de données Adobe Experience Platform :

* Toutes les autorisations sous Droits de propriété :
   * Approuver
   * Développer
   * Modifier la propriété
   * Gérer les environnements
   * Gérer les extensions
   * Publier
* Autorisation Gérer les propriétés sous Droits d’entreprise

Si vous ajoutez un utilisateur pour la première fois, procédez comme suit pour ajouter des utilisateurs à la collecte de données Adobe Experience Platform et à Adobe Experience Platform. Si vous avez déjà ajouté des utilisateurs, plusieurs profils peuvent être affichés. Veillez donc à sélectionner le profil approprié.

>[!IMPORTANT]
>
>Seuls les administrateurs d’organisation peuvent accéder à Admin Console et ajouter les utilisateurs.

### &#x200B;1. Vérifiez que Adobe Experience Platform et la collecte de données Adobe Experience Platform sont configurés

1. Connectez-vous à votre organisation Experience Cloud, [Accueil Adobe Experience Cloud](https://experience.adobe.com?lang=fr).
1. Dans le coin supérieur droit, cliquez sur le sélecteur de shell Experience Cloud pour afficher un menu déroulant.

   ![sélecteur de coque](/help/assets/places_shell_switcher1.png)

1. Au bas de la liste, cliquez sur ****. (Vous trouverez également un lien vers **** dans la section Accès rapide).

   Si vous ne voyez pas **** dans la liste, vous n’êtes pas un administrateur. Vous devez contacter l’administrateur de votre organisation pour effectuer cette procédure.

1. Dans Admin Console, si vous avez accès à plusieurs organisations, vérifiez que l’organisation appropriée est sélectionnée en haut à droite de la page.

   Il s’agit de l’organisation à laquelle vous allez ajouter vos utilisateurs. Si l’organisation appropriée n’a pas été sélectionnée, cliquez sur l’organisation et sélectionnez-la dans la liste déroulante.

   >[!IMPORTANT]
   >
   >Si l’organisation souhaitée ne figure pas dans la liste déroulante, cela signifie que vous ne disposez pas d’un accès administrateur à cette organisation.

1. Dans Admin Console, cliquez sur l’onglet Produits et vérifiez que les cartes de **[!UICONTROL Collecte de données Adobe Experience Platform]** et **[!UICONTROL Adobe Experience Platform]** s’affichent.

   ![](/help/assets/places_provisioned1.png)

   Ces 2 produits sont automatiquement mis en service pour toutes les organisations. Ils doivent donc être présents.


### &#x200B;2. Ajouter un utilisateur à ces produits

#### Ajout d’un utilisateur pour fournir l’accès à l’interface utilisateur du service Places

1. Dans l&#39;onglet Produits , cliquez sur la vignette ****.
2. Un utilisateur peut être ajouté à n&#39;importe quel profil dans **** pour accéder à Places, aucune autorisation spécifique ne doit être définie.
3. Choisissez un profil (s’il en existe plusieurs) et cliquez dessus pour l’ouvrir.
4. Cliquez sur le bouton bleu **Ajouter un utilisateur**, renseignez l’utilisateur avec son AdobeID et son nom, puis cliquez sur Enregistrer pour terminer l’ajout.

#### Ajout d’un utilisateur à la collecte de données

1. Dans l’onglet Produits , cliquez sur la vignette **[!UICONTROL Collecte de données]**.
2. Par défaut, un profil nommé **Tous les accès de la collecte de données par défaut** aura été créé. L’ajout d’un utilisateur à ce profil garantit qu’il dispose des autorisations appropriées pour travailler avec le service Places et la collecte de données. Si un autre profil est sélectionné, assurez-vous que les autorisations mentionnées ci-dessus sont incluses.
3. Choisissez un profil (s’il en existe plusieurs) et cliquez dessus pour l’ouvrir.
4. Cliquez sur le bouton bleu **Ajouter un utilisateur**, renseignez l’utilisateur avec son AdobeID et son nom, puis cliquez sur Enregistrer pour terminer l’ajout.

#### Ajoutez un utilisateur en tant que développeur pour Places Service.

Pour les utilisateurs qui ont également besoin d’accéder à l’API REST Places Service, vous devez les ajouter en tant que développeur.
1. Dans l&#39;onglet Produits , cliquez sur la vignette ****.
2. Si l&#39;utilisateur a déjà été ajouté à la carte **** via les instructions ci-dessus, choisissez le même profil précédemment utilisé et cliquez dessus.
3. Dans le profil, cliquez sur l’onglet **Développeurs**
4. Cliquez sur le bouton bleu **Ajouter un développeur**, renseignez l’utilisateur avec son Adobe ID et son nom, puis cliquez sur Enregistrer pour terminer l’ajout.

Une fois les étapes ci-dessus terminées, l’utilisateur recevra un e-mail l’informant qu’il a accès à **** et à **[!UICONTROL la collecte de données Adobe Experience Platform]**. Ils peuvent ensuite se connecter à [](https://experience.adobe.com?lang=fr) pour cette organisation et accéder au service Places et à la collecte de données. Si vous suivez également les étapes **[!UICONTROL Ajouter un développeur]**, l’utilisateur peut également se connecter à [Adobe Developer Console](https://developer.adobe.com/console/home) pour créer un projet qui donnerait accès à l’API REST Places Service.
