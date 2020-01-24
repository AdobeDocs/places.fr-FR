---
title: Utilisation de métadonnées avec des points d’intérêt
description: Cette section fournit des informations et des stratégies sur l’utilisation des métadonnées avec les points d’intérêt.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# Stratégies d’utilisation des métadonnées avec des points d’intérêt {#using-metadata-pois}

Dans le service Places, lorsque vous créez une nouvelle API, les seuls éléments requis sont Nom, Rayon, Latitude et Longitude. Pour plus d’informations sur la création d’une API, voir [Création d’une API](/help/poi-mgmt-ui/create-a-poi-ui.md). Si, toutefois, vous ne saisissez que les informations minimales, vous ne pourrez pas créer de valeur supplémentaire.

Les métadonnées de l’API peuvent être utilisées de différentes manières. Du point de vue de la gestion des points d’intérêt, l’ajout de valeurs de métadonnées peut vous aider à rechercher ou à filtrer une liste de milliers d’points d’intérêt potentiels. La création de métadonnées pour les attributs clés liés à un point d’intérêt peut générer une valeur dans les processus en aval. Par exemple, une chaîne d&#39;hôtels qui crée des points d&#39;intérêt pour chaque établissement peut vouloir inclure des métadonnées comme si l&#39;établissement possède une piscine ou non, un restaurant et un bar, ou s&#39;il possède une salle de sport. Ces métadonnées peuvent être incluses en tant que données contextuelles dans Analytics et peuvent également être utilisées pour des offres ou des messages ciblés.

## Place les métadonnées du service dans le lancement

Dans le lancement de la plate-forme d’expérience, vous pouvez créer des éléments de données pour chaque champ de métadonnées du service Places qui est important à des fins de suivi ou de messagerie.

![élément de données de l&#39;installation de gymnastique](/help/assets/gymfacility.png)

Vous pouvez ensuite créer une action avec l’extension Analytics pour créer un accès qui inclut les métadonnées que vous souhaitez utiliser comme données contextuelles.

![action pour le gymnase](/help/assets/Analytics-gym.png)

## Messagerie in-app dans Adobe Campaign

Les métadonnées peuvent servir de filtre pour les notifications locales et les messages in-app définis dans Adobe Campaign Standard. L’utilisation de métadonnées comme filtre permet de créer un message plus pertinent contextuel par rapport à l’emplacement réel.

![filtrage des notifications locales et des messages in-app dans ACS](/help/assets/ACS_gym_metadata.png)