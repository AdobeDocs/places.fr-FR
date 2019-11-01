---
title: Questions fréquentes
seo-title: Questions fréquentes
description: Cette rubrique fournit des informations supplémentaires sur certaines questions fréquentes.
seo-description: Cette rubrique fournit des informations supplémentaires sur certaines questions fréquentes.
translation-type: tm+mt
source-git-commit: a2e30282789d9834e5c65502e28ddb25f3c55dfa

---


# Questions fréquentes

Voici quelques informations et des questions fréquentes sur le service d’emplacement.

## Taille et fiabilité

Important à noter pour toutes les géofinitions utilisées dans la surveillance de région à partir d’une application mobile, indépendamment de l’utilisation d’Adobe ou d’un autre service. Les systèmes d’exploitation recommandent certains paramètres à garder à l’esprit lors de la création de géoofences. Pour une fiabilité maximale, les clôtures doivent avoir un rayon d’au moins 100 mètres. Il est possible de créer de petites grilles, mais les événements d’entrée et de sortie peuvent ne pas être générés ou être générés une fois que l’utilisateur a cessé de se déplacer pendant une période donnée.

En outre, la précision et la fiabilité peuvent être réduites en fonction de conditions matérielles telles que l'arrêt ou l'indisponibilité du Wi-Fi, et en fonction de l'emplacement de l'appareil par rapport à l'obstacle des signaux GPS. Par exemple, les zones montagneuses, les zones urbaines et les zones intérieures peuvent réduire la précision de l’emplacement à partir des systèmes d’exploitation iOS et Android.

## Comment se déclenche un événement de sortie ?

Lorsque le moniteur de lieux (SDK) obtient une nouvelle liste des points d’intérêt proches, il enregistre une région avec le système d’exploitation pour chaque point d’intérêt. Le système d’exploitation est maintenant chargé d’avertir le SDK lorsque le périphérique franchit une limite (entrée ou sortie) pour l’une des régions surveillées. Le SDK déclenche uniquement un événement de sortie lorsque le système d’exploitation avertit le SDK que l’événement s’est produit. La raison principale de cette notification est la sensibilité temporelle des données d’emplacement.

Si le système d’exploitation ne peut pas diffuser d’événement de sortie lorsque le périphérique quitte une région, il est plus sûr que le SDK omette simplement l’événement de sortie. Si le SDK fabrique un événement de sortie sans que l’événement ne soit déclenché par le système d’exploitation, il est possible que l’événement de sortie soit traité bien en dehors de la période pendant laquelle le périphérique se trouvait près de l’API.

## Ajout d’un utilisateur au service d’emplacement et au lancement de la plateforme d’expérience {#adding-user-launch-places}

Pour permettre aux utilisateurs d’accéder à l’interface utilisateur [du service de](https://places.adobe.com)lancement, ils doivent être ajoutés au service Places Core dans la console d’administration en tant qu’utilisateur. Pour permettre aux utilisateurs d’accéder au lancement de la plateforme d’expérience, de configurer les propriétés mobiles et d’utiliser Places avec le SDK Adobe Experience Platform, ils doivent être ajoutés au lancement de la plateforme d’expérience dans la console d’administration et bénéficier des autorisations suivantes pour le lancement de la plateforme d’expérience :

* Tous les droits de propriété :
   * Développer
   * Approuver
   * Publiez
   * Gestion des extensions
   * Gestion des environnements
* Autorisation de gestion des propriétés sous Droits d’entreprise

S’il s’agit de la première fois que vous ajoutez un utilisateur, procédez comme suit pour ajouter des utilisateurs au service de localisation et de lancement de la plateforme d’expérience. Si vous avez déjà ajouté des utilisateurs, plusieurs profils peuvent s’afficher, assurez-vous donc de sélectionner le profil approprié.

>[!IMPORTANT]
>
>Seuls les administrateurs de l’organisation peuvent accéder à la Console d’administration et ajouter les utilisateurs.

### 1. Vérifiez que le service d’emplacement et le lancement de la plateforme d’expérience sont configurés.

Pour vérifier que le service d’emplacement et le lancement de la plateforme d’expérience sont configurés :

1. Connectez-vous à votre organisation Experience Cloud.
1. Dans le coin supérieur droit, cliquez sur le sélecteur de shell Experience Cloud.

   ![interrupteur à coque](/help/assets/places_shell_switcher1.png)

1. Sous **[!UICONTROL Platform]** (Événements), cliquez sur **[!UICONTROL Administration]** (Ajouter).

   Si vous ne voyez pas **Administration** dans la liste, vous n’êtes pas un administrateur. Vous devez contacter votre administrateur pour terminer cette procédure.

1. Dans la page Administration d’Experience Cloud, sur la **[!UICONTROL Admin Console]** carte, cliquez sur **[!UICONTROL Take me there]**.

1. Dans la console d’administration, si vous avez accès à plusieurs organisations, vérifiez que l’organisation appropriée est sélectionnée dans le coin supérieur droit de la page.

   Il s’agit de l’organisation à laquelle vous allez ajouter vos utilisateurs. Si l'organisation appropriée n'a pas été sélectionnée, cliquez sur l'organisation et sélectionnez l'organisation dans la liste déroulante.

   >[!IMPORTANT]
   >
   >Si vous n’avez pas accès à une organisation, cela signifie que vous n’avez pas accès administrateur à cette organisation.

1. Vérifiez que les cartes pour **[!UICONTROL Adobe Experience Platform Launch]** et **[!UICONTROL Places Core Services]** sont affichées.

   ![](/help/assets/places_provisioned1.png)

   S’ils sont affichés, le service d’emplacement et le lancement de la plateforme d’expérience ont été configurés pour votre entreprise. S’ils ne sont pas affichés, ils doivent être configurés pour votre entreprise.

   >[!IMPORTANT]
   >
   >Pendant la période bêta, une fois l'enquête [](https://forms.office.com/Pages/ResponsePage.aspx?id=Wht7-jR7h0OUrtLBeN7O4fkr821yYptFo-ghlnlXCyhUM0dQVkJCSzVDMFNGWEFXWUUwNEJWSjhSRS4u)bêta terminée, la demande est envoyée à l'équipe de mise en service.

### 2. Configuration du profil et ajout des autorisations

Pour configurer le profil et ajouter les autorisations :

1. Configurez un profil de lancement de plateforme d’expérience, qui permet aux utilisateurs qui ont été ajoutés au profil d’utiliser le lancement de plateforme d’expérience et ses propriétés mobiles avec le SDK de plateforme d’expérience.

   a. Dans la barre de menus, cliquez sur **[!UICONTROL Product]**.

   b. Dans le volet de gauche, dans la liste des produits, cliquez sur **[!UICONTROL Adobe Experience Platform Launch]**.

   * Le ou les profils de lancement de plateforme d’expérience s’affichent sur la droite.
   * Le lancement de la plateforme d’expérience a un profil par défaut appelé *Launch - (nom de l’organisation)* .

      Si vous avez précédemment ajouté des utilisateurs au lancement de la plateforme d’expérience, plusieurs profils peuvent s’afficher.

1. Sélectionnez le profil correct :

   a. Cliquez sur le nom du profil par défaut.

   b. Cliquez sur l’ **[!UICONTROL Permissions]** onglet.

   c. Cliquez **[!UICONTROL Edit]** en regard de **[!UICONTROL Property Rights]**.

   d. Dans le volet de gauche, cliquez sur **[!UICONTROL + Add all]**.

   Cette étape déplace toutes les autorisations disponibles vers la liste des autorisations incluses.

   e. Cliquez sur **[!UICONTROL Company Rights]**.

   f. Dans le volet de gauche, cliquez sur **[!UICONTROL + Manage Properties]**.

   g. Cliquez sur **[!UICONTROL Save]**.

>[!IMPORTANT]
>
>Pour le service d’emplacement, il existe un profil par défaut, mais vous n’avez pas à ajouter d’autorisations.

Vous avez correctement ajouté des autorisations au profil que vous avez créé.

### 3. Ajout d’un utilisateur ou d’un développeur à vos profils de lancement du service d’emplacement et de plateforme d’expérience

Vous pouvez ajouter un utilisateur et/ou un développeur à vos profils de lancement de service d’emplacement et de plateforme d’expérience.

### Ajout d’un utilisateur

Pour ajouter un utilisateur à vos profils de lancement du service d’emplacement et de la plateforme d’expérience :

1. Ajoutez un utilisateur au profil de lancement de plateforme d’expérience.

   a. Dans la barre de menus, cliquez sur **[!UICONTROL Overview]**.

   b. Sur la **[!UICONTROL Adobe Experience Platform Launch]** carte, vérifiez les éléments suivants :

   * Deux points sont affichés au bas de la carte.
   * Le point à gauche est noir.

      Si le point sur le côté droit est noir, vous ne pouvez ajouter que des développeurs. Pour ajouter un utilisateur, cliquez sur le point à gauche.
   c. Cliquez sur **[!UICONTROL + Add Users]**.

   d. Saisissez l’ID Adobe de l’utilisateur.

   e. Effectuez l’une des étapes suivantes :

   * Si vous ajoutez un nouvel utilisateur, cliquez sur **[!UICONTROL New user]**, puis saisissez son prénom et son nom.
   * Si vous ajoutez un utilisateur existant, cliquez sur son nom.
   f. Dans la liste **[!UICONTROL Please select a profile for this product]** déroulante, sélectionnez le profil que vous avez modifié précédemment.

   g. Cliquez sur **[!UICONTROL Save]**.

1. Ajoutez un utilisateur à **[!UICONTROL Places Core Services]**.

   >[!TIP]
   >
   >Actuellement, tous les utilisateurs du service d’emplacement disposent des mêmes autorisations. Il n’est donc pas nécessaire de modifier ces autorisations.

   a. Sur la **[!UICONTROL Places Core Services]** carte, vérifiez les éléments suivants :

   * Deux points sont affichés au bas de la carte.
   * Le point à gauche est noir.
   b. Cliquez sur **[!UICONTROL + Assign Users]**.

   c. Saisissez l’ID Adobe de l’utilisateur.

   d. Effectuez l’une des étapes suivantes :

   * Si vous ajoutez un nouvel utilisateur, cliquez sur **[!UICONTROL New user]**, puis saisissez son prénom et son nom.
   * Si vous ajoutez un utilisateur existant, cliquez sur son nom.
   e. Dans la liste **[!UICONTROL Please select a profile for this product]** déroulante, sélectionnez le profil Lieux.

   f. Cliquez sur **[!UICONTROL Save]**.

### Ajout d’un développeur

Pour les utilisateurs qui ont également besoin d’accéder à l’API du service Web, vous devez les ajouter en tant que développeur.

Pour ajouter un développeur :

1.  Sur la **[!UICONTROL Places Core Services]** carte, vérifiez les éléments suivants :

   * Deux points sont affichés au bas de la carte.
   * Cliquez sur le point à droite pour **[!UICONTROL Assign Developers]** afficher la partie inférieure de la carte.

1. Cliquez sur **[!UICONTROL + Assign Developers]** (Nouvelle propriété).

1.  Saisissez l’ID Adobe de l’utilisateur.

1.  Effectuez l’une des étapes suivantes :

   * Si vous ajoutez un nouvel utilisateur, cliquez sur **[!UICONTROL New user]** et saisissez son prénom et son nom.
   * Si vous ajoutez un utilisateur existant, cliquez sur son nom.

1. Dans la liste **[!UICONTROL Please select a profile for this product]** déroulante, sélectionnez le profil Service d’emplacement.

1. Cliquez sur **Enregistrer**.

Les utilisateurs reçoivent un courrier électronique leur indiquant qu’ils ont accès au lancement de la plateforme d’expérience. Ils peuvent se connecter au lancement [de la plateforme](https://launch.adobe.com) d’expérience ou aux interfaces utilisateur [des lieux](https://places.adobe.com) pour cette organisation. Si vous exécutez l’étape 4 de la procédure **Ajouter un développeur** , l’utilisateur peut également se connecter à la console [d’E/S](https://console.adobe.io) Adobe pour créer une intégration Places et utiliser l’API REST Places.