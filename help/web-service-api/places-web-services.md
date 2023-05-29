---
title: Présentation de l’API des services web
description: Places Service est l’ensemble des services qui permet aux clients d’Adobe d’hydrater les solutions Adobe Experience Cloud et Adobe Experience Platform avec des données de localisation et l’expérience appropriée à la bonne personne au bon moment et au bon endroit.
exl-id: 9e7358d1-3ba0-4304-aeb2-fed7162afb57
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '335'
ht-degree: 1%

---

# Présentation de l’API des services web {#places-web-services-api}

Places Service est l’ensemble des services qui permet aux clients d’Adobe d’hydrater les solutions Adobe Cloud Platform et Adobe Experience Platform avec des données de localisation et l’expérience appropriée à la bonne personne au bon moment et au bon endroit.

Les API de services Web vous permettent d’effectuer les opérations suivantes :

* Gestion des clôtures virtuelles
* Mesurer l’emplacement des utilisateurs même lorsque l’application est en arrière-plan
* Utiliser les données en temps réel lorsqu’elles sont importantes

Cette section fournit des informations sur l’utilisation des API REST et de la base de données POI, qui contient les données POI de votre organisation.

## API REST

L’API REST de Places Service vous permet de travailler par programmation avec les points ciblés de votre entreprise. Ces API vous permettent de créer, de mettre à jour et de supprimer vos bibliothèques et vos points ciblés dans ces bibliothèques. Ces API utilisent les normes JSON (JavaScript Object Notation) pour formater les données envoyées et reçues. L’avantage principal de JSON est qu’il facilite l’écriture, la lecture et l’analyse des requêtes d’API par les développeurs et les machines.

Avant de pouvoir utiliser l’API des services Web, assurez-vous que les conditions suivantes ont été remplies :

* Places Service est configuré dans votre organisation et vous disposez d’un accès approprié en tant qu’utilisateur.

   Pour plus d’informations, voir *Conditions préalables pour l’accès utilisateur* in [Présentation de l’intégration et conditions préalables](/help/web-service-api/adobe-i-o-integration.md).

* Une fois que le service Places est configuré dans votre organisation et que vous y avez accès, créez une intégration d’Adobe pour le service Places.

   Pour plus d’informations, voir *Création d&#39;une intégration avec Places Service* in [Présentation de l’intégration et conditions préalables](/help/web-service-api/adobe-i-o-integration.md).

Informations supplémentaires :

* Pour plus d’informations sur les API disponibles et leur utilisation, voir [Gestion des bibliothèques](/help/web-service-api/api-usage/manage-libraries/manage-libraries.md) et [Gestion des points ciblés](/help/web-service-api/api-usage/manage-pois/manage-pois.md).
* Pour plus d’informations sur les en-têtes et les paramètres de ces API, voir [En-têtes et paramètres](/help/web-service-api/api-usage/headers-and-parameters.md).
