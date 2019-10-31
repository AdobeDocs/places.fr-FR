---
title: Utilisation de métadonnées avec des points d’intérêt
seo-title: Utilisation de métadonnées avec des points d’intérêt
description: Cette section fournit des informations et des stratégies sur l’utilisation des métadonnées avec les points d’intérêt.
seo-description: 'Cette section fournit des informations et des stratégies sur l’utilisation des métadonnées avec les points d’intérêt. '
translation-type: tm+mt
source-git-commit: 6a01c7c2c573baf572fdc27f47f8fc62322cfd02

---


# Stratégies d’utilisation des métadonnées avec des points d’intérêt {#using-metadata-pois}

Dans le service d’emplacement, lorsque vous créez une nouvelle API, les seuls éléments requis sont Nom, Rayon, Latitude et Longitude. Pour plus d’informations sur la création d’une API, voir [Création d’une API](/help/poi-mgmt-ui/create-a-poi-ui.md). Si, toutefois, vous ne saisissez que les informations minimales, vous ne pourrez pas créer de valeur supplémentaire.

Les métadonnées du point d’intérêt peuvent être utilisées de différentes manières. Du point de vue de la gestion des points d’intérêt, l’ajout de valeurs de métadonnées peut faciliter la recherche ou le filtrage d’une liste de milliers d’points d’intérêt potentiels. La création de métadonnées pour les attributs clés liés à un point d’intérêt peut générer une valeur dans les processus en aval. Par exemple, une chaîne d'hôtels qui crée des points d'intérêt pour chaque établissement peut vouloir inclure des métadonnées comme si l'établissement possède une piscine ou non, un restaurant et un bar, ou s'il possède une salle de sport. Ces métadonnées peuvent être incluses en tant que données contextuelles dans Analytics et peuvent également être utilisées pour des offres ou des messages ciblés.

## Métadonnées du service d’emplacement au lancement

Dans le lancement d’Adobe Experience Platform, vous pouvez créer des éléments de données pour chaque champ de métadonnées du service d’emplacement qui est important à des fins de suivi ou de messagerie.

![élément de données de l'installation de gymnastique](/help/assets/gymfacility.png)

Vous pouvez ensuite créer une action avec l’extension Analytics pour créer un accès qui inclut les métadonnées que vous souhaitez utiliser comme données contextuelles.

![action pour le gymnase](/help/assets/Analytics-gym.png)

## Messagerie in-app dans Adobe Campaign

Les métadonnées peuvent servir de filtre pour les notifications locales et les messages in-app définis dans Adobe Campaign Standard. L’utilisation de métadonnées comme filtre permet de créer un message plus pertinent contextuel par rapport à l’emplacement réel.

![filtrage des notifications locales et des messages in-app dans ACS](/help/assets/ACS_gym_metadata.png)