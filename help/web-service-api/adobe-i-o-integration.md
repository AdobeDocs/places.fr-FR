---
title: Présentation de l’intégration Adobe I/O
description: Informations sur la création d’une intégration Adobe I/O.
translation-type: tm+mt
source-git-commit: c22efc36f2eac6b20fc555d998c3988d8c31169e
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 5%

---


# Présentation de l&#39;intégration et conditions préalables {#integration-prereqs}

Ces informations vous montrent comment créer une intégration Adobe I/O et un service Places.

## Conditions préalables pour l’accès des utilisateurs

Vérifiez auprès de l&#39;administrateur système de votre organisation que les tâches suivantes ont été effectuées :

* Place le service principal s’affiche dans la console d’administration de votre entreprise.
* Vous avez été ajouté à l’organisation.
* Vous avez été ajouté en tant qu’utilisateur au service principal Places de votre entreprise.

   Pour plus d’informations, voir *Ajouter un utilisateur ou un développeur à votre service Places et à vos profils Experience Platform Launch* dans [Accès au service Places](/help/places-gain-access.md).

* Vous avez été ajouté en tant que développeur pour Places Core Service dans votre entreprise.

   Pour plus d&#39;informations sur l&#39;ajout de développeurs, voir *Ajouter un utilisateur ou un développeur à votre service Places et à vos profils Experience Platform Launch* dans [Obtenir l&#39;accès au service Places](/help/places-gain-access.md).

   Pour plus d’informations sur le rôle de développeur, voir [Gérer les développeurs](https://helpx.adobe.com/fr/enterprise/using/manage-developers.html).

### Demandes d’API REST

Chaque requête à l’API REST du service Places nécessite les éléments suivants :

* Un ID d’organisation
* Une clé d&#39;API
* Jeton de porteur

Une intégration à Adobe I/O fournit ces éléments et un moyen de demander le jeton porteur à l’aide d’un JSON Web Token (JWT).

* Pour plus d’informations sur les JWT, voir [Introduction to JSON Web Tokens](https://jwt.io/introduction/).
* Pour créer une intégration pour le service Places, voir la section *Création d&#39;une intégration du service Places* ci-dessous.
* Pour comprendre l’intégration des clés d’API, la génération d’un JWT et de certificats de clé publique, voir [Aperçu de l’authentification Adobe I/O](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html).

>[!IMPORTANT]
>
>Si vous ne pouvez pas vous connecter à la console Adobe I/O ou si le service Places n&#39;est pas une option dans la *page Créer des intégrations*, voir *Exigences d&#39;organisation* dans [Présentation de l&#39;API des services Web](/help/web-service-api/places-web-services.md).

## Création d’une intégration du service Places

Pour créer une intégration du service Places, effectuez les tâches suivantes :

### Générer une paire de clés publique et privée

Pour créer une intégration du service Places, vous avez besoin d’une paire de clés publique et privée. Ces paires peuvent être achetées ou vous pouvez générer vos propres clés autosignées.

Pour générer vos propres clés autosignées :

1. Dans une fenêtre de terminal, copiez et collez chacune des lignes suivantes, puis appuyez sur **[!UICONTROL Entrée]** après avoir collé chaque ligne :

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >Nous vous recommandons de nommer vos clés pour en faciliter la référence et de les stocker dans un dossier. Si vous créez plusieurs intégrations, vous pouvez facilement identifier et gérer les clés qui appartiennent à l’intégration.

1. Entrez les informations demandées par OpenSSL :

   ```text
   Country Name (2 letter code:  // Example: US
   State or Province Name (full name):  // Example: California
   Locality Name (eg, city):  // Example: San Jose
   Organization Name (eg, company):  // Example: Places
   Organizational Unit Name (eg, section):  // Example: Engineering
   Common Name (eg, fully qualified host name):  // Example: places.com
   Email Address:  // Example:  poi@places.com
   ```

   Pour plus d’informations sur OpenSSL, voir [OpenSSL](https://www.openssl.org/).

   >[!IMPORTANT]
   >
   >Les informations que vous fournissez sont intégrées aux clés.

1. Accédez au répertoire dans lequel se trouvent les fichiers `.key` et `.crt`.

   Par exemple, sous MacOS, accédez à **[!UICONTROL Macintosh HD]** > **[!UICONTROL utilisateurs]** > **[!UICONTROL (votre nom d’utilisateur)]** > **[!UICONTROL Clés]**.

La vidéo suivante vous guide tout au long du processus de génération de la paire de clés :

![vidéo d’intégration](/help/assets/places_integration_video.gif)

### Création d’une intégration du service Places dans la console Adobe I/O

Pour créer une intégration du service Places :

1. Accédez à [https://console.adobe.io](https://console.adobe.io) et connectez-vous avec votre Adobe ID.
1. Dans la section **Début rapide**, cliquez sur **Créer l&#39;intégration**.
1. Sélectionnez **[!UICONTROL Access an API]** (Accéder à une API), puis cliquez sur **[!UICONTROL Continue]** (Continuer).

   **[!UICONTROL Accéder à une]** API est l’emplacement par défaut.

1. Si vous avez accès à plusieurs organisations Experience Cloud, sélectionnez l’organisation dans la liste déroulante située en haut à droite.
1. Sous **[!UICONTROL Experience Cloud]**, sélectionnez **[!UICONTROL Service des emplacements]** comme service d&#39;Adobe à intégrer et cliquez sur **[!UICONTROL Continuer]**.
1. Sélectionnez **[!UICONTROL Nouvelle intégration]** et cliquez sur **[!UICONTROL Continuer]**.
1. Dans l’écran Créer une intégration, saisissez un nom et une description.
1. Faites glisser votre fichier `xxxx_public.crt` que vous avez créé ci-dessus vers la zone de dépôt **[!UICONTROL Certificats de clés publiques]**.
1. Sélectionnez un profil de produit.

   Si vous ne savez pas quel profil sélectionner, contactez votre administrateur système.
1. Au bas de la page, cliquez sur **[!UICONTROL Créer une intégration]**.
1. Après quelques secondes, dans l’écran *Intégration créée*, vérifiez que le message suivant s’affiche :

   `Your integration has been created.`

1. La page des détails de l’intégration s’affiche avec le nom de l’intégration en haut.

   L&#39;onglet **[!UICONTROL Aperçu]** s&#39;affiche par défaut et affiche la clé d&#39;API, l&#39;ID de votre organisation, l&#39;ID du compte technique et d&#39;autres détails sur vos intégrations.

### Enregistrer l’ID d’organisation et la clé d’API

1. Dans la page des détails de l&#39;intégration, cliquez sur l&#39;onglet **[!UICONTROL Services]** et vérifiez que **[!UICONTROL Place Service]** s&#39;affiche sous **[!UICONTROL Configuré Services]**.
1. Dans l&#39;onglet **[!UICONTROL Aperçu]**, recherchez et enregistrez la clé d&#39;API (ID client) et l&#39;ID d&#39;organisation.

   Ces identifiants sont nécessaires pour chaque requête d’API REST du service Places.

![](/help/assets/places_orgid_api-key.png)

### Génération d’un jeton JWT

Dans la page des détails de l’intégration, cliquez sur l’onglet **[!UICONTROL JWT]** afin de pouvoir tester votre intégration en générant un JWT et en fournissant l’URL d’échange.

Pour générer un jeton JWT :

1. Dans un éditeur de texte, ouvrez le fichier `private.key` créé ci-dessus.
1. Sous l’onglet **[!UICONTROL JWT]**, copiez le contenu de la clé et collez-le dans le champ **[!UICONTROL Coller la clé privée]**.
1. Cliquez sur **[!UICONTROL Générer JWT]**.
1. Dans la section **[!UICONTROL Exemple de commande CURL]**, cliquez sur **[!UICONTROL Copier]** et collez le contenu dans votre invite de commande ou fenêtre de terminal.
1. Exécutez la commande en appuyant sur **[!UICONTROL Entrée]** sur votre clavier.
1. Recherchez les valeurs `"token_type": "bearer"` et `"access_token"`.

   La valeur du jeton d&#39;accès porteur est ce que vous utiliserez dans vos demandes d’API du service Lieux.

>[!IMPORTANT]
>
>Les jetons d&#39;accès d’Adobe sont valides **uniquement** pendant 24 heures. Enregistrez donc l’exemple de commande CURL (étape 5). Si le jeton d&#39;accès n’est plus valide, vous devez régénérer le jeton.