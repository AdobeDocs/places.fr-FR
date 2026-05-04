---
title: Utilisation de métadonnées avec des points d’intérêt
description: Cette section fournit des informations et des stratégies sur l’utilisation des métadonnées avec les points d’intérêt.
exl-id: e669e560-a999-43ff-aeb4-06e6308b0d5c
TQID: https://experienceleague.adobe.com/wTzahAs7MMSv0q-cEhkNObBpALUJXqDXlOcqjitezwY
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: dfc56824-e8b9-499e-85d4-21aedb507314id: e43347a8-f2c5-4aa4-8623-6f13875d7e3aid: e55547f1-a1ff-40c6-8978-026e40ab7fa4id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: a004cc84-67b9-4a33-a3a7-8ec7273ef4dcid: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 296
ht-degree: 0%

---

# Stratégies d’utilisation des métadonnées avec les points d’intérêt {#using-metadata-pois}

Dans Places Service, lorsque vous créez un point d’intérêt, les seuls éléments requis sont le nom, le rayon, la latitude et la longitude. Pour plus d’informations sur la création d’un point d’intérêt, voir [ Créer un point d’intérêt ](/help/poi-mgmt-ui/create-a-poi-ui.md). Cependant, si vous saisissez uniquement les informations minimales, vous raterez une occasion de créer de la valeur supplémentaire.

Les métadonnées de point d’intérêt peuvent être utilisées de différentes manières. Du point de vue de la gestion des points d’intérêt, l’ajout de valeurs de métadonnées peut vous aider à rechercher ou à filtrer une liste de milliers de points d’intérêt potentiels. La création de métadonnées pour les attributs clés liés à un point d’intérêt peut générer de la valeur dans les workflows en aval. Par exemple, une chaîne hôtelière qui crée des points d’intérêt pour chaque propriété peut vouloir inclure des métadonnées comme si la propriété de l’hôtel possède une piscine ou non, un restaurant et un bar, ou si elle possède une salle de sport. Ces métadonnées peuvent être incluses en tant que données contextuelles dans les analyses et peuvent également être utilisées pour les offres ou les messages ciblés.

## Métadonnées du service Places dans Launch

Dans Experience Platform Launch, vous pouvez créer des éléments de données pour chaque champ de métadonnées du service Places qui est important à des fins de suivi ou de messagerie.

![élément de données pour la salle de sport](/help/assets/gymfacility.png)

Vous pouvez ensuite créer une action avec l’extension Analytics pour créer un nouvel accès contenant les métadonnées souhaitées en tant que données contextuelles.

![action pour le gymnase](/help/assets/Analytics-gym.png)

## Messagerie In-App dans Adobe Campaign

Les métadonnées peuvent être utilisées comme filtre pour les notifications locales et les messages in-app définis dans Adobe Campaign Standard. L’utilisation des métadonnées comme filtre permet de créer un message plus pertinent et contextuel par rapport à l’emplacement réel.

![filtrer les notifications locales et les messages in-app dans ACS](/help/assets/ACS_gym_metadata.png)
