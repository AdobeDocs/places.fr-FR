---
title: Gestion des bibliothèques dans l’interface utilisateur de Places Service
description: Gérez vos bibliothèques à l’aide de l’interface utilisateur du service Places.
exl-id: 2fb999b4-854a-430f-bb89-4c786d1a89cc
TQID: https://experienceleague.adobe.com/PP7P3aOL3EKSEPJWedHtfyHRzbCueMtNS-J7Ao4mawo
product_v2:
  - id: cb954087-f4fc-4456-afb9-e939cabcdc79
  - id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87
  - id: dc5cf79d-43c4-4731-bffa-1df5d7549cb1
  - id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2:
  - id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2:
  - id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2:
  - id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 434
ht-degree: 14%

---

# Gestion des bibliothèques {#manage-libraries-places-ui}

Une bibliothèque est une collection de points d’intérêt. Vous pouvez avoir jusqu’à 150 000 POI dans une bibliothèque et il peut y avoir jusqu’à 100 bibliothèques par organisation Experience Cloud.

Il existe différentes manières d’organiser vos points d’intérêt en bibliothèques en fonction de ce qui est le plus utile pour votre organisation. Certains clients peuvent préférer créer une bibliothèque distincte pour chaque application mobile, tandis que d’autres peuvent utiliser des bibliothèques pour regrouper des types spécifiques de points d’intérêt tels que des cafés, des parcs, des hôtels, etc. Par exemple, une grande entreprise de divertissement peut avoir une bibliothèque qui comprend ses salles extérieures dans une bibliothèque et ses magasins de détail dans une autre bibliothèque. Une administration municipale peut avoir une bibliothèque qui comprend tous les bâtiments de la ville et une autre qui comprend tous les parcs de la ville.

Les bibliothèques sont définies par les éléments suivants :

| Clés : | Description : |
| :--- | :--- |
| Identifiant | identifiant unique attribué à la bibliothèque lors de sa création |
| Nom | nom convivial donné à une bibliothèque |
| Classer | Ces classements peuvent être ignorés s’il n’y a pas de géorepères qui se chevauchent dans votre organisation. En cas de superposition de POI, nous vous recommandons de placer chacune des clôtures virtuelles dans des bibliothèques distinctes afin qu’elles puissent être pondérées les unes par rapport aux autres. Un utilisateur ne peut se situer que dans une clôture virtuelle à la fois. <br><br>Le ranking le plus élevé de la clôture virtuelle dans laquelle se trouve un utilisateur détermine l’abonnement actuel de cet utilisateur à la clôture. S’il existe des limites géographiques ayant le même classement de bibliothèque, la plus petite est la limite géographique actuelle de l’utilisateur. <br><br>Le SDK connaît également les points d’intérêt *Dernière entrée* et *Dernière sortie*, ce qui vous permet de contrôler entièrement la manière dont vous souhaitez que vos règles se déclenchent en fonction de l’interaction de l’utilisateur avec vos points d’intérêt. |

## créer une bibliothèque ;

1. Connectez-vous à Places avec votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur **[!UICONTROL ...]** > **[!UICONTROL Gérer les bibliothèques]**.
1. Cliquez sur **[!UICONTROL Nouveau]**.
1. Saisissez le nom.
1. Cliquez sur **[!UICONTROL Confirmer]**.

## Modification du classement d’une bibliothèque dans l’interface utilisateur Emplacements

1. Connectez-vous à Places avec votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur **[!UICONTROL ...]** > **[!UICONTROL Gérer les bibliothèques]**.
1. Cliquez sur l’icône à gauche du nom de la bibliothèque et faites glisser la bibliothèque vers le nouveau classement.

## Renommer une bibliothèque

1. Connectez-vous à Places avec votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur **[!UICONTROL ...]** > **[!UICONTROL Gérer les bibliothèques]**.
1. Recherchez la bibliothèque à supprimer.
1. Cliquez sur **[!UICONTROL ...]** et sélectionnez **[!UICONTROL Renommer]**.
1. Mettez à jour le nom et cliquez sur **[!UICONTROL Enregistrer]**.

## Suppression d’une bibliothèque

1. Connectez-vous à Places avec votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur **[!UICONTROL ...]** > **[!UICONTROL Gérer les bibliothèques]**.
1. Recherchez la bibliothèque à supprimer.
1. Cliquez sur **[!UICONTROL ...]** et sélectionnez **[!UICONTROL Supprimer]**.
