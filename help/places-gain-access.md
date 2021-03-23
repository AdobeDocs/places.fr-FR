---
title: 'Obtenir l''accès au service Places '
description: Cette section fournit des informations sur la façon d'ajouter un utilisateur au service Places et à l'Experience Platform Launch, de sorte que l'utilisateur puisse accéder au service Places.
translation-type: tm+mt
source-git-commit: ecf50d67d4c08e79d9c3be64480f27d435fd7fcb
workflow-type: tm+mt
source-wordcount: '1160'
ht-degree: 10%

---

# Accès au service Places {#adding-user-launch-places}

Vous pouvez accéder au service Lieux à partir du menu Accès rapide sur [Adobe Experience Cloud home](https://experience.adobe.com).
Si votre ID utilisateur a accès, l&#39;icône du service Lieux s&#39;affiche, comme indiqué ci-dessous :

![menu d&#39;accès rapide](/help/assets/quickaccess.png)

Vous pouvez également accéder au service Lieux à partir du menu Adobe Experience Platform :

![Menu Experience Platform](/help/assets/solutionaccessmenu.png)

Si le service Lieux n’apparaît dans aucun de ces menus, contactez un administrateur de votre organisation pour ajouter votre ID d’utilisateur au service principal Lieux dans le Admin Console.

## Ajouter un utilisateur au service Places et à l’Experience Platform Launch

Pour permettre aux utilisateurs d’accéder à l’[interface utilisateur Experience Platform Launch](https://launch.adobe.com), ils doivent être ajoutés au service principal Places dans le Admin Console en tant qu’utilisateur. Pour permettre aux utilisateurs d’accéder à l’Experience Platform Launch, de configurer les propriétés mobiles et d’utiliser des emplacements avec le kit SDK Adobe Experience Platform, ils doivent être ajoutés à l’Experience Platform Launch dans le Admin Console et recevoir les autorisations suivantes pour l’Experience Platform Launch :

* Tous les droits de propriété :
   * Développer
   * Approuver
   * Publiez
   * Gérer les extensions
   * Gestion des environnements
* Gérer l’autorisation Propriétés sous Droits de Société

Si c’est la première fois que vous ajoutez un utilisateur, procédez comme suit pour ajouter des utilisateurs au service Experience Platform Launch et aux services locaux. Si vous avez déjà ajouté des utilisateurs, plusieurs profils peuvent s’afficher. Assurez-vous donc de sélectionner le profil approprié.

>[!IMPORTANT]
>
>Seuls les administrateurs de l’organisation peuvent accéder au Admin Console et ajouter les utilisateurs.

### 1. Vérifiez que le service Places et l’Experience Platform Launch sont configurés.

1. Connectez-vous à votre organisation Experience Cloud.
1. Dans le coin supérieur droit, cliquez sur le sélecteur de shell Experience Cloud.

   ![interrupteur à coque](/help/assets/places_shell_switcher1.png)

1. Sous **[!UICONTROL Plateforme]**, cliquez sur **[!UICONTROL Administration]**.

   Si **[!UICONTROL Administration]** n’apparaît pas dans la liste, vous n’êtes pas un administrateur. Vous devez contacter l’administrateur de votre organisation pour effectuer cette procédure.

1. Dans la page Administration de l’Experience Cloud, sur la carte **[!UICONTROL Admin Console]**, cliquez sur **[!UICONTROL M’y amener]**.

1. Dans le Admin Console, si vous avez accès à plusieurs organisations, vérifiez que la bonne organisation est sélectionnée dans le coin supérieur droit de la page.

   Il s’agit de l’organisation à laquelle vous allez ajouter vos utilisateurs. Si l’organisation appropriée n’a pas été sélectionnée, cliquez sur l’organisation et sélectionnez l’organisation dans la liste déroulante.

   >[!IMPORTANT]
   >
   >Si vous n’avez pas accès à une organisation, cela signifie que vous n’avez pas d’accès administrateur à cette organisation.

1. Vérifiez que les cartes pour **[!UICONTROL Adobe Experience Platform Launch]** et **[!UICONTROL Services principaux des Places]** s’affichent.

   ![](/help/assets/places_provisioned1.png)

   S’ils s’affichent, le service Places et l’Experience Platform Launch ont été configurés pour votre organisation. S’ils ne s’affichent pas, ils doivent être configurés pour votre organisation.


### 2. Configurez le profil et ajoutez les autorisations

1. Configurez un profil Experience Platform Launch qui permet aux utilisateurs qui ont été ajoutés au profil d’utiliser l’Experience Platform Launch et ses propriétés mobiles avec le SDK Experience Platform.

   a. Dans la barre de menus, cliquez sur **[!UICONTROL Produit]**.

   b. Dans le volet de gauche, dans la liste des produits, cliquez sur **[!UICONTROL Adobe Experience Platform Launch]**.

   * Le ou les profils de l&#39;Experience Platform Launch s&#39;affichent à droite.
   * L’Experience Platform Launch possède un profil par défaut appelé *Launch - (nom de l’organisation)* .

      Si vous aviez déjà ajouté des utilisateurs à un Experience Platform Launch, plusieurs profils peuvent s’afficher.

1. Sélectionnez le profil approprié :

   a. Cliquez sur le nom du profil par défaut.

   b. Cliquez sur l&#39;onglet **[!UICONTROL Permissions]**.

   c. Cliquez sur **[!UICONTROL Modifier]** en regard de **[!UICONTROL Droits de propriété]**.

   d. Dans le volet de gauche, cliquez sur **[!UICONTROL + Ajouter all]**.

   Cette étape déplace toutes les autorisations disponibles vers la liste d’autorisations incluse.

   e. Cliquez sur **[!UICONTROL Droits de la Société]**.

   f. Dans le volet de gauche, cliquez sur **[!UICONTROL + Gérer les propriétés]**.

   g. Cliquez sur **[!UICONTROL Enregistrer]**.

>[!IMPORTANT]
>
>Pour le service Places, il existe un profil par défaut, mais vous n’avez pas à ajouter d’autorisations.

Vous avez correctement ajouté des autorisations au profil que vous avez créé.

### 3. Ajoutez un utilisateur ou un développeur à votre service Places et à vos profils Experience Platform Launch

Vous pouvez ajouter un utilisateur et/ou un développeur à votre service Places et à vos profils Experience Platform Launch.

### Ajout d’un utilisateur

Pour ajouter un utilisateur à votre service Lieux et à vos profils Experience Platform Launch :

1. Ajoutez un utilisateur au profil Experience Platform Launch.

   a. Dans la barre de menus, cliquez sur **[!UICONTROL Aperçu]**.

   b. Sur la carte **[!UICONTROL Adobe Experience Platform Launch]**, vérifiez les éléments suivants :

   * Deux points sont affichés au bas de la carte.
   * Le point à gauche est noir.

      Si le point à droite est noir, vous ne pouvez ajouter que des développeurs. Pour ajouter un utilisateur, cliquez sur le point à gauche.
   c. Cliquez sur **[!UICONTROL + Ajouter les utilisateurs]**.

   d. Saisissez l’Adobe ID de l’utilisateur.

   e. Effectuez l’une des étapes suivantes :

   * Si vous ajoutez un nouvel utilisateur, cliquez sur **[!UICONTROL Nouvel utilisateur]**, puis saisissez le prénom et le nom de l’utilisateur.
   * Si vous ajoutez un utilisateur existant, cliquez sur son nom.

   f. Dans la liste déroulante **[!UICONTROL Sélectionnez un profil pour ce produit]**, sélectionnez le profil que vous avez modifié précédemment.

   g. Cliquez sur **[!UICONTROL Enregistrer]**.

1. Ajoutez un utilisateur à **[!UICONTROL Place les services principaux]**.

   >[!TIP]
   >
   >Actuellement, tous les utilisateurs du service Lieux disposent des mêmes autorisations. Il n’est donc pas nécessaire de modifier ces autorisations.

   a. Sur la carte **[!UICONTROL Place les services principaux]**, vérifiez les éléments suivants :

   * Deux points sont affichés au bas de la carte.
   * Le point à gauche est noir.

   b. Cliquez sur **[!UICONTROL + Attribuer des utilisateurs]**.

   c. Saisissez l’Adobe ID de l’utilisateur.

   d. Effectuez l’une des étapes suivantes :

   * Si vous ajoutez un nouvel utilisateur, cliquez sur **[!UICONTROL Nouvel utilisateur]**, puis saisissez le prénom et le nom de l’utilisateur.
   * Si vous ajoutez un utilisateur existant, cliquez sur son nom.

   e. Dans la liste déroulante **[!UICONTROL Sélectionnez un profil pour ce produit]**, sélectionnez le profil Lieux.

   f. Cliquez sur **[!UICONTROL Enregistrer]**.

### Ajouter un développeur

Pour les utilisateurs qui doivent également accéder à l’API du service Web, vous devez les ajouter en tant que développeur.

Pour ajouter un développeur :

1. Sur la carte **[!UICONTROL Services principaux d’Places]**, vérifiez les éléments suivants :

   * Deux points sont affichés au bas de la carte.
   * Cliquez sur le point à droite pour que **[!UICONTROL Affecter des développeurs]** s’affiche au bas de la carte.

1. Cliquez sur **[!UICONTROL + Affecter des développeurs]**.

1. Saisissez l’Adobe ID de l’utilisateur.

1. Effectuez l’une des étapes suivantes :

   * Si vous ajoutez un nouvel utilisateur, cliquez sur **[!UICONTROL Nouvel utilisateur]** et saisissez son prénom et son nom.
   * Si vous ajoutez un utilisateur existant, cliquez sur son nom.

1. Dans la liste déroulante **[!UICONTROL Sélectionnez un profil pour ce produit]**, sélectionnez le profil Service Lieux.

1. Cliquez sur **[!UICONTROL Enregistrer]**.

Les utilisateurs reçoivent un e-mail leur indiquant qu’ils ont accès à Experience Platform Launch. Ils peuvent se connecter aux [Experience Platform Launch](https://launch.adobe.com) ou aux [interfaces utilisateur du service Places](https://places.adobe.com) pour cette organisation. Si vous effectuez l’étape 4 de la procédure **[!UICONTROL Ajouter un développeur]**, l’utilisateur peut aussi se connecter à la [console Adobe I/O](https://console.adobe.io) pour créer une intégration des Places et utiliser l’API REST Places.
