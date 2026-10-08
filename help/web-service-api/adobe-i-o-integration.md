---
title: Présentation des projets Adobe Developer
description: Informations sur la création d’un projet API Adobe Developer.
exl-id: d7d31938-6c0e-40f8-a9d3-30af96043119
product_v2:
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
    internal-label: Experience Platform
source-git-commit: d8704da9c84a066f72471421290d4b46c65f41e1
workflow-type: tm+mt
source-wordcount: '504'
ht-degree: 2%
---
# Présentation et conditions préalables à l’accès à l’API Places {#developer-prereqs}

Ces informations vous montrent comment créer un projet dans le Adobe Developer Console et générer un jeton d’accès à utiliser dans les requêtes de l’API Places.

## Conditions préalables pour l’accès utilisateur

Vérifiez auprès de l’administrateur système de votre entreprise que les tâches suivantes ont été effectuées :

* Vous avez été ajouté à l’organisation.
* Vous avez été ajouté à un profil dans le Adobe Experience Platform.

  Pour plus d’informations, voir *Ajouter un utilisateur ou un développeur à vos profils Places Service et Experience Platform Launch* dans [Accéder au service Places](/help/places-gain-access.md).

### Requêtes d’API REST

Chaque requête à l’API REST Places Service nécessite les éléments suivants :

* ID d’organisation
* Une clé API (également appelée identifiant client)
* Secret client
* Jeton porteur

Un projet avec la console [&#128279;](https://developer.adobe.com/console) fournit ces éléments.

* Pour créer un projet pour l’API Places Service, reportez-vous à la section *Création d’un projet Places Service* ci-dessous.

>[!IMPORTANT]
>
>Si vous ne pouvez pas vous connecter à la console [&#128279;](https://developer.adobe.com/console) ou si Places Service n’est pas une option de la page *Créer des intégrations*, consultez *Exigences de l’organisation* dans [Présentation de l’API des services web](/help/web-service-api/places-web-services.md).

## Création d’un projet d’API Places Service

Pour créer un projet pour l’API Places Service, procédez comme suit :

1. Connectez-vous au [site web &#x200B;](https://developer.adobe.com) avec votre Adobe ID.
2. Cliquez sur **[!UICONTROL Console]** dans le coin supérieur droit de la page.
3. Si vous êtes affecté à plusieurs organisations Adobe, sélectionnez l’organisation appropriée dans la liste déroulante située dans le coin supérieur droit de la page.
4. Cliquez sur le bouton **[!UICONTROL Créer un projet]**.
5. Cliquez sur le bouton **[!UICONTROL Ajouter une API]** dans la section Prise en main de votre nouveau projet .
6. Pour sélectionner l’API Places, faites défiler la page jusqu’à la carte Places et cliquez sur la case à cocher située dans le coin supérieur droit de la carte.
7. Cliquez sur le bouton **[!UICONTROL Suivant]**.
8. Sélectionnez l’option OAuth de serveur à serveur (s’il y a un choix).
9. Nommez les informations d’identification et cliquez sur **[!UICONTROL Suivant]**.
10. Sélectionnez un profil (tout profil doit fonctionner s’il en existe plusieurs).
11. Cliquez sur **[!UICONTROL Enregistrer et configurer l’API]**.
12. Dans le panneau de gauche, cliquez sur le lien **[!UICONTROL OAuth serveur à serveur]** sous INFORMATIONS D’IDENTIFICATION
13. Cette page fournit les informations suivantes :
    * Méthode de génération d’un jeton d’accès à utiliser dans les requêtes API REST du service Places.
    * Affichez une commande curl pour obtenir un exemple de génération d’un jeton d’accès à partir de votre propre code.
    * Afficher l’ID client (également appelé clé API)
    * Afficher le secret client
    * Afficher l’ID d’organisation
    * Toutes ces informations sont requises dans les requêtes à l’API REST Places Service.
14. Vous pouvez donner au projet un nom plus explicite en cliquant sur le nom du projet dans le chemin d’accès en haut à gauche de la fenêtre
15. Cliquez ensuite sur le bouton **[!UICONTROL Modifier le projet]** en haut à droite de la page.

>[!IMPORTANT]
>
>Les jetons d’accès Adobe sont valides **uniquement** pendant 24 heures. Enregistrez donc l’exemple de commande CURL (étape 5). Si le jeton d’accès n’est plus valide, vous devez le régénérer.
