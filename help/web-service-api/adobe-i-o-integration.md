---
title: Présentation du projet Adobe Developer
description: Informations sur la création d’un projet d’API Adobe Developer.
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
source-git-commit: 3d477c6133b74a7e6380d0db1af5125aaa844035
workflow-type: tm+mt
source-wordcount: '497'
ht-degree: 2%

---

# Présentation de l’accès à l’API Places et conditions préalables {#developer-prereqs}

Ces informations vous montrent comment créer un projet dans la console Adobe Developer et générer un jeton d’accès à utiliser dans les demandes de l’API Places.

## Conditions préalables pour l’accès utilisateur

Vérifiez auprès de l’administrateur système de votre entreprise que les tâches suivantes ont été effectuées :

* Vous avez été ajouté à l’organisation.
* Vous avez été ajouté à un profil dans Adobe Experience Platform.

  Pour plus d’informations, voir *Ajout d’un utilisateur ou d’un développeur à vos profils Places Service et Experience Platform Launch* in [Accéder au service Places](/help/places-gain-access.md).

### Requêtes d’API REST

Chaque requête à l’API REST du service Places nécessite les éléments suivants :

* Un ID d’organisation
* Une clé API (également appelée ID client)
* Secret client
* Jeton porteur

Un projet avec la fonction [Console Adobe Developer](https://developer.adobe.com/console) fournit ces éléments.

* Pour créer un projet pour l’API Places Service, voir *Création d’un projet de service Places* ci-dessous.

>[!IMPORTANT]
>
>Si vous ne pouvez pas vous connecter à [Console Adobe Developer](https://developer.adobe.com/console)ou si le service Places n’est pas une option de la variable *Page Créer des intégrations*, voir *Exigences de l’organisation* in [Présentation de l’API des services Web](/help/web-service-api/places-web-services.md).

## Création d’un projet d’API de service Places

Pour créer une API de projet pour Places Service, procédez comme suit :

1. Connexion à [Site web Adobe Developer](https://developer.adobe.com) avec votre Adobe ID.
2. Cliquez sur **[!UICONTROL Console]** dans le coin supérieur droit de la page.
3. Si plusieurs organisations d’Adobe vous sont affectées, sélectionnez la bonne organisation dans la liste déroulante située dans le coin supérieur droit de la page.
4. Cliquez sur le bouton **[!UICONTROL Créer un projet]** bouton .
5. Cliquez sur **[!UICONTROL Ajouter une API]** dans la section Prise en main de votre nouveau projet .
6. Pour sélectionner l&#39;API Places, faites défiler la page jusqu&#39;à la carte Places et cochez la case dans le coin supérieur droit de la carte.
7. Cliquez sur le bouton **[!UICONTROL Suivant.]**
8. Sélectionnez l’option Serveur à serveur OAuth (s’il y a un choix).
9. Nommez les informations d’identification, puis cliquez sur **[!UICONTROL Suivant]**.
10. Sélectionnez un profil (tout doit fonctionner s’il en existe plusieurs).
11. Cliquez sur **[!UICONTROL Enregistrement et configuration de l’API]**.
12. Dans le panneau de gauche, cliquez sur le **[!UICONTROL OAuth serveur à serveur]** lien sous CREDENTIALS
13. Cette page fournit les informations suivantes :
   * Un moyen de générer un jeton d’accès à utiliser dans les demandes de l’API REST du service Places.
   * Affichez une commande curl pour obtenir un exemple de génération d’un jeton d’accès à partir de votre propre code.
   * Affichage de l’ID client (également appelé clé API)
   * Affichage du secret client
   * Affichage de l’ID d’organisation
   * Tous ces éléments sont requis dans les requêtes de l’API REST Places Service.
14. Vous pouvez renommer le projet en un nom plus explicite en cliquant sur le nom du projet dans le chemin d’accès en haut à gauche de la fenêtre.
15. Cliquez ensuite sur le bouton **[!UICONTROL Modifier le projet]** dans le coin supérieur droit de la page.

>[!IMPORTANT]
>
>Les jetons d’accès aux Adobes sont valides **only** pendant 24 heures, enregistrez l’exemple de commande CURL (étape 5). Si le jeton d’accès n’est plus valide, vous devez régénérer le jeton.
