---
title: Utilisation de métadonnées avec des points ciblés
description: Cette section fournit des informations et des stratégies sur l’utilisation des métadonnées avec les points ciblés.
exl-id: e669e560-a999-43ff-aeb4-06e6308b0d5c
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '293'
ht-degree: 0%

---

# Stratégies d’utilisation des métadonnées avec les points ciblés {#using-metadata-pois}

Dans Places Service, lorsque vous créez un point ciblé, les seuls éléments requis sont Nom, Rayon, Latitude et Longitude. Pour plus d’informations sur la création d’un point ciblé, voir [Création d’un point ciblé](/help/poi-mgmt-ui/create-a-poi-ui.md). Toutefois, si vous ne saisissez que les informations minimales, vous ne saurez pas l’occasion de créer une valeur supplémentaire.

Les métadonnées des points ciblés peuvent être utilisées de différentes manières. Du point de vue de la gestion des points ciblés, l’ajout de valeurs de métadonnées peut vous aider à rechercher ou à filtrer une liste de milliers de points ciblés potentiels. La création de métadonnées pour les attributs clés liés à un point ciblé peut générer de la valeur dans les workflows en aval. Par exemple, une chaîne d’hôtels créant des points ciblés pour chaque propriété peut vouloir inclure des métadonnées telles que si l’établissement dispose d’une piscine ou non, ou d’un restaurant et d’un bar, ou s’il dispose d’un centre de remise en forme. Ces métadonnées peuvent être incluses en tant que données contextuelles dans Analytics et peuvent également être utilisées pour les offres ou les messages ciblés.

## Métadonnées du service Places dans Launch

Dans Experience Platform Launch, vous pouvez créer des éléments de données pour chaque champ de métadonnées du service Places qui est important à des fins de suivi ou de messagerie.

![élément de données de l’installation de gymnase](/help/assets/gymfacility.png)

Vous pouvez ensuite créer une action avec l’extension Analytics pour la création d’un accès qui comprend les métadonnées souhaitées en tant que données contextuelles.

![action pour le gymnase](/help/assets/Analytics-gym.png)

## Messagerie in-app dans Adobe Campaign

Les métadonnées peuvent être utilisées comme filtre pour les notifications locales et les messages in-app définis dans Adobe Campaign Standard. L’utilisation de métadonnées comme filtre permet de créer un message plus pertinent, contextuel à l’emplacement réel.

![filtrage des notifications locales et des messages in-app dans ACS](/help/assets/ACS_gym_metadata.png)
