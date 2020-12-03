---
title: 'Obtenir l''accès au service Places '
description: Cette section fournit des informations sur la façon d'ajouter un utilisateur au service Places et à l'Experience Platform Launch, de sorte que l'utilisateur puisse accéder au service Places.
translation-type: tm+mt
source-git-commit: 26538602a73e806a4822705c7a3aa44d76351030
workflow-type: tm+mt
source-wordcount: '1079'
ht-degree: 7%

---

# Obtenir l&#39;accès au service Places {#adding-user-launch-places}

Vous pouvez accéder au service Lieux à partir du menu d&#39;accès rapide sur la page d&#39;accueil [de](https://experience.adobe.com)Adobe Experience Cloud.
Si votre ID utilisateur a accès, l&#39;icône du service Lieux s&#39;affiche, comme indiqué ci-dessous :

![menu d&#39;accès rapide](/help/assets/quickaccess.png)

Vous pouvez également accéder au service Lieux à partir du menu Adobe Experience Platform :

![Menu Experience Platform](/help/assets/solutionaccessmenu.png)

Si le service Lieux n’apparaît dans aucun de ces menus, contactez un administrateur de votre organisation pour ajouter votre ID d’utilisateur au service principal Lieux dans le Admin Console.

## Ajouter un utilisateur au service Places et à l’Experience Platform Launch

Pour permettre aux utilisateurs d’accéder à l’interface utilisateur [de l’](https://launch.adobe.com)Experience Platform Launch, ils doivent être ajoutés au service principal Places dans le Admin Console en tant qu’utilisateur. Pour permettre aux utilisateurs d’accéder à l’Experience Platform Launch, de configurer les propriétés mobiles et d’utiliser des emplacements avec le kit SDK Adobe Experience Platform, ils doivent être ajoutés à l’Experience Platform Launch dans le Admin Console et recevoir les autorisations suivantes pour l’Experience Platform Launch :

* Tous les droits de propriété :
   * Développer
   * Approuver
   * Publiez
   * Gérer les extensions
   * Gérer les environnements
* Gérer l’autorisation Propriétés sous Droits de Société

Si c’est la première fois que vous ajoutez un utilisateur, procédez comme suit pour ajouter des utilisateurs au service Experience Platform Launch et aux services locaux. Si vous avez déjà ajouté des utilisateurs, plusieurs profils peuvent s’afficher. Assurez-vous donc de sélectionner le profil approprié.

>[!IMPORTANT]
>
>Seuls les administrateurs de l’organisation peuvent accéder au Admin Console et ajouter les utilisateurs.

### 1. Vérifiez que le service Places et l’Experience Platform Launch sont configurés.

1. Connectez-vous à votre organisation Experience Cloud.
1. Dans le coin supérieur droit, cliquez sur le sélecteur de shell Experience Cloud.

   ![interrupteur à coque](/help/assets/places_shell_switcher1.png)

1. Sous **[!UICONTROL Platform]** (Événements), cliquez sur **[!UICONTROL Administration]** (Ajouter).

   Si vous ne voyez pas **Administration** dans la liste, vous n’êtes pas un administrateur. Vous devez contacter l’administrateur de votre organisation pour effectuer cette procédure.

1. Dans la page Administration des Experience Cloud, sur la **[!UICONTROL Admin Console]** carte, cliquez sur **[!UICONTROL Take me there]**.

1. Dans le Admin Console, si vous avez accès à plusieurs organisations, vérifiez que la bonne organisation est sélectionnée dans le coin supérieur droit de la page.

   Il s’agit de l’organisation à laquelle vous allez ajouter vos utilisateurs. Si l’organisation appropriée n’a pas été sélectionnée, cliquez sur l’organisation et sélectionnez l’organisation dans la liste déroulante.

   >[!IMPORTANT]
   >
   >Si vous n’avez pas accès à une organisation, cela signifie que vous n’avez pas d’accès administrateur à cette organisation.

1. Vérifiez que les cartes pour **[!UICONTROL Adobe Experience Platform Launch]** et **[!UICONTROL Places Core Services]** sont affichées.

   ![](/help/assets/places_provisioned1.png)

   S’ils s’affichent, le service Places et l’Experience Platform Launch ont été configurés pour votre organisation. S’ils ne s’affichent pas, ils doivent être configurés pour votre organisation.


### 2. Configurez le profil et ajoutez les autorisations

1. Configurez un profil Experience Platform Launch qui permet aux utilisateurs qui ont été ajoutés au profil d’utiliser l’Experience Platform Launch et ses propriétés mobiles avec le SDK Experience Platform.

   a. Dans la barre de menus, cliquez sur **[!UICONTROL Product]**.

   b. Dans le volet de gauche, dans la liste des produits, cliquez sur **[!UICONTROL Adobe Experience Platform Launch]**.

   * Le ou les profils de l&#39;Experience Platform Launch s&#39;affichent à droite.
   * L’Experience Platform Launch possède un profil par défaut appelé *Launch - (nom de l’organisation)* .

      Si vous aviez déjà ajouté des utilisateurs à un Experience Platform Launch, plusieurs profils peuvent s’afficher.

1. Sélectionnez le profil approprié :

   a. Cliquez sur le nom du profil par défaut.

   b. Click the **[!UICONTROL Permissions]** tab.

   c. Cliquez sur **[!UICONTROL Edit]** en regard de **[!UICONTROL Property Rights]**.

   d. Dans le volet de gauche, cliquez sur **[!UICONTROL + Add all]**.

   Cette étape déplace toutes les autorisations disponibles vers la liste d’autorisations incluse.

   e. Cliquez sur **[!UICONTROL Company Rights]**.

   f. Dans le volet de gauche, cliquez sur **[!UICONTROL + Manage Properties]**.

   g. Cliquez sur **[!UICONTROL Save]**.

>[!IMPORTANT]
>
>Pour le service Places, il existe un profil par défaut, mais vous n’avez pas à ajouter d’autorisations.

Vous avez correctement ajouté des autorisations au profil que vous avez créé.

### 3. Ajoutez un utilisateur ou un développeur à votre service Places et à vos profils Experience Platform Launch

Vous pouvez ajouter un utilisateur et/ou un développeur à votre service Places et à vos profils Experience Platform Launch.

### Ajout d’un utilisateur

Pour ajouter un utilisateur à votre service Lieux et à vos profils Experience Platform Launch :

1. Ajoutez un utilisateur au profil Experience Platform Launch.

   a. Dans la barre de menus, cliquez sur **[!UICONTROL Overview]**.

   b. Sur la **[!UICONTROL Adobe Experience Platform Launch]** carte, vérifiez les éléments suivants :

   * Deux points sont affichés au bas de la carte.
   * Le point à gauche est noir.

      Si le point à droite est noir, vous ne pouvez ajouter que des développeurs. Pour ajouter un utilisateur, cliquez sur le point à gauche.
   c. Cliquez sur **[!UICONTROL + Add Users]**.

   d. Saisissez l’Adobe ID de l’utilisateur.

   e. Effectuez l’une des étapes suivantes :

   * Si vous ajoutez un nouvel utilisateur, cliquez sur **[!UICONTROL New user]**, puis saisissez son prénom et son nom.
   * Si vous ajoutez un utilisateur existant, cliquez sur son nom.

   f. Dans la liste **[!UICONTROL Please select a profile for this product]** déroulante, sélectionnez le profil que vous avez modifié précédemment.

   g. Cliquez sur **[!UICONTROL Save]**.

1. Add a user to **[!UICONTROL Places Core Services]**.

   >[!TIP]
   >
   >Actuellement, tous les utilisateurs du service Lieux disposent des mêmes autorisations. Il n’est donc pas nécessaire de modifier ces autorisations.

   a. Sur la **[!UICONTROL Places Core Services]** carte, vérifiez les éléments suivants :

   * Deux points sont affichés au bas de la carte.
   * Le point à gauche est noir.

   b. Cliquez sur **[!UICONTROL + Assign Users]**.

   c. Saisissez l’Adobe ID de l’utilisateur.

   d. Effectuez l’une des étapes suivantes :

   * Si vous ajoutez un nouvel utilisateur, cliquez sur **[!UICONTROL New user]**, puis saisissez son prénom et son nom.
   * Si vous ajoutez un utilisateur existant, cliquez sur son nom.

   e. Dans la liste **[!UICONTROL Please select a profile for this product]** déroulante, sélectionnez le profil Lieux.

   f. Cliquez sur **[!UICONTROL Save]**.

### Ajouter un développeur

Pour les utilisateurs qui doivent également accéder à l’API du service Web, vous devez les ajouter en tant que développeur.

Pour ajouter un développeur :

1. Sur la **[!UICONTROL Places Core Services]** carte, vérifiez les éléments suivants :

   * Deux points sont affichés au bas de la carte.
   * Cliquez sur le point sur la droite pour **[!UICONTROL Assign Developers]** afficher la partie inférieure de la carte.

1. Cliquez sur **[!UICONTROL + Assign Developers]**.

1. Saisissez l’Adobe ID de l’utilisateur.

1. Effectuez l’une des étapes suivantes :

   * Si vous ajoutez un nouvel utilisateur, cliquez sur **[!UICONTROL New user]** et saisissez son prénom et son nom.
   * Si vous ajoutez un utilisateur existant, cliquez sur son nom.

1. Dans la liste **[!UICONTROL Please select a profile for this product]** déroulante, sélectionnez le profil Service Lieux.

1. Cliquez sur **Enregistrer**.

Les utilisateurs reçoivent un e-mail leur indiquant qu’ils ont accès à Experience Platform Launch. They can can log in to the [Experience Platform Launch](https://launch.adobe.com) or the [Places Service](https://places.adobe.com) UIs for this organization. Si vous effectuez l’étape 4 de la procédure **Ajouter un développeur**, l’utilisateur peut aussi se connecter à la [console Adobe I/O](https://console.adobe.io) pour créer une intégration des Places et utiliser l’API REST Places.
