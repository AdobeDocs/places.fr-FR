---
title: Présentation de l’intégration des E/S Adobe
seo-title: Présentation de l’intégration des E/S Adobe
description: Informations sur la création d’une intégration d’E/S Adobe.
seo-description: Informations sur la création d’une intégration d’E/S Adobe.
translation-type: tm+mt
source-git-commit: 95c29df19f61e7854e39b47e39471f7f1e94b736

---


# Présentation de l’intégration et conditions préalables {#integration-prereqs}

Ces informations vous montrent comment créer une intégration d’E/S Adobe et d’emplacements.

## Conditions préalables pour l’accès utilisateur

Vérifiez auprès de l’administrateur système de votre entreprise que les tâches suivantes ont été accomplies :

* Place le service principal s’affiche dans la console d’administration de votre entreprise.
* Vous avez été ajouté à l’organisation.
* Vous avez été ajouté en tant qu’utilisateur au service principal Places de votre entreprise.

   Pour plus d’informations, reportez-vous à la section *Ajout d’un utilisateur ou d’un développeur à vos profils* de lancement du service d’emplacement et de plateforme d’expérience dans la section Questions [](/help/places-faqs.md)fréquentes.

* Vous avez été ajouté en tant que développeur à Places Core Service dans votre entreprise.

   Pour plus d’informations sur l’ajout de développeurs, reportez-vous à la section *Ajout d’un utilisateur ou d’un développeur à vos profils* de lancement de plateforme d’exploitation et de service d’emplacement dans la [Foire aux questions](/help/places-faqs.md).

   Pour plus d’informations sur le rôle de développeur, voir [Gestion des développeurs](https://helpx.adobe.com/enterprise/using/manage-developers.html).

### Demandes d’API REST

Chaque requête à l’API REST Places requiert les éléments suivants :

* Un ID d’organisation
* Une clé API
* Jeton porteur

Une intégration avec les E/S Adobe fournit ces éléments et un moyen de demander le jeton porteur à l’aide d’un JSON Web Token (JWT).

* Pour plus d’informations sur les JWT, voir [Présentation des jetons](https://jwt.io/introduction/)Web JSON.
* Pour créer une intégration pour Places, voir la section *Création d’une intégration* Places ci-dessous.
* Pour comprendre l’intégration des clés d’API, la génération d’un fichier JWT et de certificats de clé publique, voir Présentation [de l’authentification](https://www.adobe.io/apis/cloudplatform/console/authentication/gettingstarted.html)des E/S Adobe.

>[!IMPORTANT]
>
>Si vous ne pouvez pas vous connecter à la console d’E/S d’Adobe ou si le service d’emplacement de la plateforme d’expérience n’est pas une option de la page ** Créer des intégrations, voir Conditions requises *pour l’* organisation dans la présentation [de l’API des services](/help/web-service-api/places-web-services.md)Web.

## Création d’une intégration Places

Pour créer une intégration Places, procédez comme suit :

### Générer une paire de clés publique et privée

Pour créer une intégration Places, vous avez besoin d’une paire de clés publique et privée. Vous pouvez acheter ces paires ou générer vos propres clés autosignées.

Pour générer vos propres clés autosignées :

1. Dans une fenêtre de terminal, copiez et collez chacune des lignes suivantes et appuyez sur **[!UICONTROL Enter]** après avoir collé chaque ligne :

   ```text
      mkdir keys
      cd keys
      openssl req -x509 -sha256 -nodes -days 365 -newkey rsa:2048 -keyout places_integration_test_private.key -out    places_integration_test_public.crt
   ```

   >[!IMPORTANT]
   >
   >Nous vous recommandons de nommer vos clés pour une référence facile et de les stocker dans un dossier. Si vous créez plusieurs intégrations, vous pouvez facilement identifier et gérer les clés appartenant à l’intégration.

2. Entrez les informations demandées par OpenSSL :

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

3. Accédez au répertoire contenant les fichiers `.key` et `.crt` .

   Par exemple, dans iOS, sélectionnez **[!UICONTROL Macintosh HD]** &gt; **[!UICONTROL users]** &gt; **[!UICONTROL (your user name)]** &gt; **[!UICONTROL Keys]**.

La vidéo suivante vous guide tout au long du processus de génération de la paire de clés :

![vidéo d’intégration](/help/assets/places_integration_video.gif)

### Création d’une intégration Places dans la console d’E/S Adobe

Pour créer une intégration Places :

1. Accédez à [https://console.adobe.io](https://console.adobe.io) et connectez-vous avec votre Adobe ID.
2. dans la section **Démarrage** rapide, cliquez sur **Créer une intégration**.
3. Sélectionnez **[!UICONTROL Access an API]** puis cliquez sur **[!UICONTROL Continue]**.

   **[!UICONTROL Access an API]** est l’emplacement par défaut.

4. Si vous avez accès à plusieurs organisations Experience Cloud, sélectionnez l’organisation dans la liste déroulante en haut à droite.
5. Sous **[!UICONTROL Experience Cloud]**, sélectionnez **[!UICONTROL Places]** le service Adobe auquel vous souhaitez intégrer, puis cliquez sur **[!UICONTROL Continue]**.
6. Sélectionnez **[!UICONTROL New integration]** puis cliquez sur **[!UICONTROL Continue]**.
7. Dans l’écran Créer une intégration, saisissez un nom et une description.
8. Faites glisser votre `xxxx_public.crt` fichier que vous avez créé ci-dessus vers la zone de **[!UICONTROL Public keys certificates]** dépôt.
9. Sélectionnez un profil de produit.

   Si vous ne savez pas quel profil sélectionner, contactez votre administrateur système.
10. At the bottom of the page, click **[!UICONTROL Create integration]**.
11. Au bout de quelques secondes, dans l’écran *Intégration créée* , vérifiez que le message suivant s’affiche :

   `Your integration has been created.`

12. La page des détails de l’intégration s’affiche avec le nom de l’intégration en haut.

   L’ **[!UICONTROL Overview]** onglet s’affiche par défaut et affiche la clé d’API, l’ID de votre organisation, l’ID de compte technique et d’autres détails sur vos intégrations.

### Enregistrer l’ID d’organisation et la clé d’API

1. Dans la page des détails de l’intégration, cliquez sur l’ **[!UICONTROL Services]** onglet et vérifiez que **[!UICONTROL Places]** l’élément est affiché sous **[!UICONTROL Configured Services]**.
2. Dans l’ **[!UICONTROL Overview]** onglet, recherchez et enregistrez la clé d’API (ID client) et l’ID d’organisation.

   Ces identifiants sont nécessaires pour chaque requête d’API REST Places.

![](/help/assets/places_orgid_api-key.png)

### Générer un jeton JWT

Dans la page des détails de l’intégration, cliquez sur l’ **[!UICONTROL JWT]** onglet afin de pouvoir tester votre intégration en générant un fichier JWT et en fournissant l’URL d’échange.

Pour générer un jeton JWT :

1. Dans un éditeur de texte, ouvrez le `private.key` fichier créé ci-dessus.
2. Sur l’ **[!UICONTROL JWT]** onglet, copiez le contenu de la clé et collez-le dans le **[!UICONTROL Paste private key]** champ.
3. Cliquez sur **[!UICONTROL Generate JWT]** (Nouvelle propriété).
4. Dans la **[!UICONTROL Sample CURL command]** section, cliquez **[!UICONTROL Copy]** et collez le contenu dans votre invite de commande ou dans la fenêtre du terminal.
5. Exécutez la commande en appuyant **[!UICONTROL Enter]** sur votre clavier.
6. Recherchez la `"token_type": "bearer"` valeur et la `"access_token"` valeur.

   La valeur du jeton d’accès au porteur est ce que vous utiliserez dans vos demandes d’API Lieux.

>[!IMPORTANT]
>
>Les jetons d’accès Adobe sont valides **uniquement** pendant 24 heures. Enregistrez donc l’exemple de commande CURL (étape 5). Si le jeton d’accès n’est plus valide, vous devez régénérer le jeton.