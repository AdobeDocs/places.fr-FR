---
title: 'Présentation des services Web Places '
seo-title: 'Présentation des services Web Places '
description: Places est l’ensemble de services qui permet aux clients d’Adobe d’hydrater plus facilement les solutions Adobe Experience Cloud et Adobe Experience Platform avec des données d’emplacement et une expérience appropriée pour la personne appropriée au bon moment et au bon endroit.
seo-description: Places est l’ensemble de services qui permet aux clients d’Adobe d’hydrater plus facilement les solutions Adobe Experience Cloud et Adobe Experience Platform avec des données d’emplacement et une expérience appropriée pour la personne appropriée au bon moment et au bon endroit.
translation-type: tm+mt
source-git-commit: f6c92bbd4fb21999f5c96ea0df8ede6919d1bc79

---


# Présentation des services Web Places {#places-web-services-api}

Places est l’ensemble de services qui permet aux clients d’Adobe d’hydrater plus facilement les solutions Adobe Cloud Platform et Adobe Experience Platform avec des données d’emplacement et l’expérience appropriée pour la personne appropriée au bon moment et au bon endroit.

Les emplacements vous permettent d’effectuer les opérations suivantes :

* Gestion des géographies
* Mesurer l’emplacement des utilisateurs même lorsque l’application est en arrière-plan
* Utiliser les données en temps réel quand cela est important

Cette section fournit des informations sur l’utilisation des API REST et de la base de données Places, qui contient les données d’API de votre entreprise.

## API PLACES REST

L’API REST Places vous permet de travailler par programmation avec les points d’accès de votre entreprise. Ces API vous permettent de créer, de mettre à jour et de supprimer vos bibliothèques et les points d’intérêt de ces bibliothèques. Ces API utilisent les normes JSON (JavaScript Object Notation) pour formater les données envoyées et reçues. L’un des principaux avantages de JSON est qu’il facilite l’écriture, la lecture et l’analyse des requêtes d’API par les développeurs et les machines.

Avant d’utiliser l’API Lieux, assurez-vous que les conditions suivantes ont été remplies :

* Les emplacements sont configurés dans votre organisation et vous disposez d’un accès approprié en tant qu’utilisateur.

   For more information, see the *Organization requirements* section below.

* Une fois que Places a été configurée dans votre organisation et que vous avez accès à cette fonctionnalité, créez une intégration Adobe pour Places.

   Pour plus d’informations, voir *Création d’une intégration* de lieux dans la présentation [de l’intégration des E/S](/help/places-web-service-api/adobe-i-o-integration.md)Adobe.

Informations supplémentaires:

* Pour plus d’informations sur les API disponibles et leur utilisation, voir [Gestion des bibliothèques](/help/places-web-service-api/api-usage/manage-libraries/manage-libraries.md) et [Gestion des API](/help/places-web-service-api/api-usage/manage-pois/manage-pois.md).
* Pour plus d’informations sur les en-têtes et les paramètres de ces API, voir [En-têtes et paramètres](/help/places-web-service-api/api-usage/headers-and-parameters.md).

## Besoins organisationnels {#org-requirements}

Pour accéder aux API REST de Places, vérifiez auprès de votre administrateur système que les tâches suivantes ont été accomplies :

* Les emplacements ont été configurés et apparaissent dans l’organisation.
* Vous avez été ajouté à l’organisation.
* Vous avez été ajouté à Places dans votre organisation.

   Pour plus d’informations, voir *Ajout d’un utilisateur à Places et lancement* de plateformes d’expérience dans [Places FAQs](/help/places-faqs.md).

* Vous avez été ajouté en tant que développeur Places à votre organisation.

   Pour plus d’informations sur le rôle de développeur, voir [Gestion des développeurs](https://helpx.adobe.com/enterprise/using/manage-developers.html).