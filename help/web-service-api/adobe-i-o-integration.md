---
title: Présentation du projet Adobe Developer
description: Informations sur la création d’un projet d’API Adobe Developer.
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 3d477c6133b74a7e6380d0db1af5125aaa844035
workflow-type: tm+mt
source-wordcount: '494'
ht-degree: 1%

---

# Présentation de l’accès à l’API Places et conditions préalables {#developer-prereqs}

Ces informations vous montrent comment créer un projet dans Adobe Developer Console et générer un jeton d’accès à utiliser dans les demandes d’API Places.

## Conditions préalables pour l’accès utilisateur

Vérifiez auprès de l’administrateur système de votre entreprise que les tâches suivantes ont été effectuées :

* Vous avez été ajouté à l’organisation.
* Vous avez été ajouté à un profil dans Adobe Experience Platform.

  Pour plus d&#39;informations, voir *Ajout d&#39;un utilisateur ou d&#39;un développeur à votre service Places et profils Experience Platform Launch* dans [Accès à Places Service](/help/places-gain-access.md).

### Requêtes d’API REST

Chaque requête à l’API REST du service Places nécessite les éléments suivants :

* Un ID d’organisation
* Une clé API (également appelée ID client)
* Secret client
* Jeton porteur

Un projet avec la [console Adobe Developer](https://developer.adobe.com/console) fournit ces éléments.

* Pour créer une API de projet pour Places Service, reportez-vous à la section *Création d&#39;un projet de service Places* ci-dessous.

>[!IMPORTANT]
>
>Si vous ne pouvez pas vous connecter à la [console Adobe Developer](https://developer.adobe.com/console), ou si le service Places n’est pas une option sur la *page Créer des intégrations*, reportez-vous à la section *Configuration requise de l’organisation* dans la [présentation de l’API des services Web](/help/web-service-api/places-web-services.md).

## Création d’un projet d’API de service Places

Pour créer une API de projet pour Places Service, procédez comme suit :

1. Connectez-vous à [site web Adobe Developer](https://developer.adobe.com) avec votre Adobe ID.
2. Cliquez sur **[!UICONTROL Console]** dans le coin supérieur droit de la page.
3. Si plusieurs organisations d’Adobe vous sont affectées, sélectionnez la bonne organisation dans la liste déroulante située dans le coin supérieur droit de la page.
4. Cliquez sur le bouton **[!UICONTROL Créer un projet]** .
5. Cliquez sur le bouton **[!UICONTROL Ajouter une API]** dans la section Prise en main de votre nouveau projet .
6. Pour sélectionner l&#39;API Places, faites défiler la page jusqu&#39;à la carte Places et cochez la case dans le coin supérieur droit de la carte.
7. Cliquez sur le bouton **[!UICONTROL Suivant]**.
8. Sélectionnez l’option Serveur à serveur OAuth (s’il y a un choix).
9. Nommez les informations d’identification et cliquez sur **[!UICONTROL Suivant]**.
10. Sélectionnez un profil (tout doit fonctionner s’il en existe plusieurs).
11. Cliquez sur **[!UICONTROL Enregistrer et configurer l’API]**.
12. Dans le panneau de gauche, cliquez sur le lien **[!UICONTROL OAuth Server-to-Server]** sous CREDENTIALS
13. Cette page fournit les informations suivantes :
   * Un moyen de générer un jeton d’accès à utiliser dans les demandes de l’API REST du service Places.
   * Affichez une commande curl pour obtenir un exemple de génération d’un jeton d’accès à partir de votre propre code.
   * Affichage de l’ID client (également appelé clé API)
   * Affichage du secret client
   * Affichage de l’ID d’organisation
   * Tous ces éléments sont requis dans les requêtes de l’API REST Places Service.
14. Vous pouvez renommer le projet en un nom plus explicite en cliquant sur le nom du projet dans le chemin d’accès en haut à gauche de la fenêtre.
15. Cliquez ensuite sur le bouton **[!UICONTROL Modifier le projet]** en haut à droite de la page.

>[!IMPORTANT]
>
>Les jetons d’accès aux Adobes sont **uniquement** valides pendant 24 heures. Enregistrez donc l’exemple de commande CURL (étape 5). Si le jeton d’accès n’est plus valide, vous devez régénérer le jeton.
