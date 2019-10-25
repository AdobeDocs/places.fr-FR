---
title: 'Présentation de l’API des services Web '
seo-title: 'Présentation de l’API des services Web '
description: Places est l’ensemble de services qui permet aux clients d’Adobe d’hydrater plus facilement les solutions Adobe Experience Cloud et Adobe Experience Platform avec des données d’emplacement et une expérience appropriée pour la personne appropriée au bon moment et au bon endroit.
seo-description: Places est l’ensemble de services qui permet aux clients d’Adobe d’hydrater plus facilement les solutions Adobe Experience Cloud et Adobe Experience Platform avec des données d’emplacement et une expérience appropriée pour la personne appropriée au bon moment et au bon endroit.
translation-type: tm+mt
source-git-commit: e204958ac3acbf5fb45d2347987f35557be70e43

---


# Présentation de l’API des services Web {#places-web-services-api}

Places est l’ensemble de services qui permet aux clients d’Adobe d’hydrater plus facilement les solutions Adobe Cloud Platform et Adobe Experience Platform avec des données d’emplacement et l’expérience appropriée pour la personne appropriée au bon moment et au bon endroit.

Les API de services Web vous permettent d’effectuer les opérations suivantes :

* Gestion des géographies
* Mesurer l’emplacement des utilisateurs même lorsque l’application est en arrière-plan
* Utiliser les données en temps réel quand cela est important

Cette section fournit des informations sur l’utilisation des API REST et de la base de données POI, qui contient les données POI de votre entreprise.

## API REST

L’API REST Places vous permet de travailler par programmation avec les points d’accès de votre entreprise. Ces API vous permettent de créer, de mettre à jour et de supprimer vos bibliothèques et les points d’intérêt de ces bibliothèques. Ces API utilisent les normes JSON (JavaScript Object Notation) pour formater les données envoyées et reçues. L’un des principaux avantages de JSON est qu’il facilite l’écriture, la lecture et l’analyse des requêtes d’API par les développeurs et les machines.

Avant d’utiliser l’API des services Web, assurez-vous que les conditions suivantes ont été remplies :

* Les emplacements sont configurés dans votre organisation et vous disposez d’un accès approprié en tant qu’utilisateur.

   Pour plus d’informations, voir la section Conditions requises *pour l’* organisation ci-dessous.

* Une fois que Places a été configurée dans votre organisation et que vous avez accès à cette fonctionnalité, créez une intégration Adobe pour Places.

   Pour plus d’informations, voir *Création d’une intégration* de lieux dans la présentation [de l’intégration des E/S](/help/web-service-api/adobe-i-o-integration.md)Adobe.

Informations supplémentaires:

* Pour plus d’informations sur les API disponibles et leur utilisation, voir [Gestion des bibliothèques](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) et [Gestion des API](/help/web-service-api/api-usage/manage-pois/manage-pois.md).
* Pour plus d’informations sur les en-têtes et les paramètres de ces API, voir [En-têtes et paramètres](/help/web-service-api/api-usage/headers-and-parameters.md).

## Besoins organisationnels {#org-requirements}

Pour accéder aux API REST des services Web, vérifiez auprès de votre administrateur système que les tâches suivantes ont été accomplies :

* Les emplacements ont été configurés et apparaissent dans l’organisation.
* Vous avez été ajouté à l’organisation.
* Vous avez été ajouté à Places dans votre organisation.

   Pour plus d’informations, voir *Ajout d’un utilisateur aux emplacements et lancement* de la plate-forme d’expérience dans les questions [](/help/places-faqs.md)fréquentes.

* Vous avez été ajouté en tant que développeur Places à votre organisation.

   Pour plus d’informations sur le rôle de développeur, voir [Gestion des développeurs](https://helpx.adobe.com/enterprise/using/manage-developers.html).