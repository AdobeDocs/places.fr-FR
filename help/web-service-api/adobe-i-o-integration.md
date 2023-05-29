---
title: Présentation de l’intégration Adobe I/O
description: Informations sur la création d’une intégration Adobe I/O.
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '879'
ht-degree: 6%

---

# Présentation de l’intégration et conditions préalables {#integration-prereqs}

Ces informations vous montrent comment créer un Adobe I/O et une intégration avec Places Service.

## Conditions préalables pour l’accès utilisateur

Vérifiez auprès de l’administrateur système de votre entreprise que les tâches suivantes ont été effectuées :

* Places Core Service apparaît dans la console d’administration de votre entreprise.
* Vous avez été ajouté à l’organisation.
* Vous avez été ajouté en tant qu’utilisateur à Places Core Service dans votre entreprise.

   Pour plus d’informations, voir *Ajout d’un utilisateur ou d’un développeur à vos profils Places Service et Experience Platform Launch* in [Accéder au service Places](/help/places-gain-access.md).

* Vous avez été ajouté en tant que développeur à Places Core Service dans votre entreprise.

   Pour plus d’informations sur l’ajout de développeurs, voir *Ajout d’un utilisateur ou d’un développeur à vos profils Places Service et Experience Platform Launch* in [Accéder au service Places](/help/places-gain-access.md).

   Pour plus d’informations sur le rôle de développeur, voir [Gérer les développeurs](https://helpx.adobe.com/fr/enterprise/using/manage-developers.html).

### Requêtes d’API REST

Chaque requête à l’API REST du service Places nécessite les éléments suivants :

* ID d’organisation
* Une clé API
* Jeton porteur

Une intégration avec Adobe I/O fournit ces éléments et un moyen de demander le jeton porteur à l’aide d’un jeton web JSON (JWT).

* Pour plus d’informations sur les jetons JWT, voir [Présentation des jetons Web JSON](https://jwt.io/introduction/).
* Pour créer une intégration pour Places Service, reportez-vous à la section *Création d&#39;une intégration avec Places Service* ci-dessous.
* Pour comprendre l’intégration de la clé API, la génération d’un JWT et de certificats de clé publique, voir [Présentation de l’authentification des Adobes I/O](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html).

>[!IMPORTANT]
>
>Si vous ne pouvez pas vous connecter à la console Adobe I/O ou si le service Places n’est pas une option de la *Page Créer des intégrations*, voir *Exigences de l’organisation* in [Présentation de l’API des services Web](/help/web-service-api/places-web-services.md).

## Création d’une intégration avec Places Service

Pour créer une intégration avec Places Service, effectuez les tâches suivantes :

### Génération d’une paire de clés publique et privée

Pour créer une intégration avec Places Service, vous avez besoin d’une paire de clés publique et privée. Vous pouvez acheter ces paires ou générer vos propres clés autosignées.

Pour générer vos propres clés auto-signées :

1. Dans une fenêtre de terminal, copiez et collez chacune des lignes suivantes, puis appuyez sur **[!UICONTROL Entrée]** après avoir collé chaque ligne :

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >Nous vous recommandons de nommer vos clés à des fins de référence et de les stocker dans un dossier. Si vous créez plusieurs intégrations, vous pouvez facilement identifier et gérer les clés appartenant à l’intégration.

1. Saisissez les informations demandées par OpenSSL :

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

1. Accédez au répertoire dans lequel le `.key` et `.crt` Les fichiers sont situés.

   Par exemple, dans MacOS, accédez à **[!UICONTROL Macintosh HD]** > **[!UICONTROL utilisateurs]** > **[!UICONTROL (votre nom d’utilisateur)]** > **[!UICONTROL Clés]**.

La vidéo suivante vous guide tout au long du processus de génération de la paire de clés :

![vidéo d’intégration](/help/assets/places_integration_video.gif)

### Création d’une intégration du service Places dans la console Adobe I/O

Pour créer une intégration avec Places Service :

1. Accédez à [https://console.adobe.io](https://console.adobe.io) et connectez-vous avec votre Adobe ID.
1. Dans le **Démarrage rapide** , cliquez sur **Création d’une intégration**.
1. Sélectionnez **[!UICONTROL Access an API]** (Accéder à une API), puis cliquez sur **[!UICONTROL Continue]** (Continuer).

   **[!UICONTROL Accès à une API]** est l’emplacement par défaut.

1. Si vous avez accès à plusieurs organisations Experience Cloud, sélectionnez l’organisation dans la liste déroulante en haut à droite.
1. Sous **[!UICONTROL Experience Cloud]**, sélectionnez **[!UICONTROL Places Service]** comme service Adobe auquel vous souhaitez intégrer et cliquez sur **[!UICONTROL Continuer]**.
1. Sélectionner **[!UICONTROL Nouvelle intégration]** et cliquez sur **[!UICONTROL Continuer]**.
1. Dans l’écran Créer une intégration , saisissez un nom et une description.
1. Faites glisser et déposez votre `xxxx_public.crt` , que vous avez créé ci-dessus, dans le fichier **[!UICONTROL Certificats de clés publiques]** zone de dépôt.
1. Sélection dʼun profil de produit.

   Si vous ne savez pas quel profil sélectionner, contactez votre administrateur système.
1. Au bas de la page, cliquez sur **[!UICONTROL Création d’une intégration]**.
1. Après quelques secondes, dans la variable *Intégration créée* Vérifiez que le message suivant s’affiche :

   `Your integration has been created.`

1. La page des détails de l’intégration s’affiche avec le nom de l’intégration en haut.

   Le **[!UICONTROL Présentation]** s’affiche par défaut et affiche la clé API, l’ID d’organisation, l’ID de compte technique et d’autres détails sur vos intégrations.

### Enregistrez l’ID d’organisation et la clé API

1. Sur la page des détails de l’intégration, cliquez sur le **[!UICONTROL Services]** et confirmez que **[!UICONTROL Places Service]** s’affiche sous **[!UICONTROL Services configurés]**.
1. Sur le **[!UICONTROL Présentation]** Recherchez et enregistrez la clé API (ID client) et l’ID d’organisation.

   Ces identifiants sont nécessaires pour chaque requête de l’API REST du service Places.

![](/help/assets/places_orgid_api-key.png)

### Génération d’un jeton JWT

Sur la page des détails de l’intégration, cliquez sur le **[!UICONTROL JWT]** afin que vous puissiez tester votre intégration en générant un jeton JWT et en fournissant l’URL d’échange.

Pour générer un jeton JWT :

1. Dans un éditeur de texte, ouvrez votre `private.key` fichier créé que vous avez créé ci-dessus.
1. Sous l’onglet **[!UICONTROL JWT]**, copiez le contenu de la clé et collez-le dans le champ **[!UICONTROL Coller la clé privée]**.
1. Cliquez sur **[!UICONTROL Génération de JWT]**.
1. Dans la section **[!UICONTROL Exemple de commande CURL]**, cliquez sur **[!UICONTROL Copier]** et collez le contenu dans votre invite de commande ou fenêtre de terminal.
1. Exécutez la commande en appuyant sur **[!UICONTROL Entrée]** sur votre clavier.
1. Recherchez la variable `"token_type": "bearer"` et le `"access_token"` .

   La valeur du jeton d’accès au porteur est ce que vous utiliserez dans vos demandes d’API du service Places.

>[!IMPORTANT]
>
>Les jetons d’accès aux Adobes sont valides **only** pendant 24 heures, enregistrez l’exemple de commande CURL (étape 5). Si le jeton d’accès n’est plus valide, vous devez régénérer le jeton.
