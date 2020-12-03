---
title: Gestion des bibliothèques dans l’interface utilisateur du service Lieux
description: Gérez vos bibliothèques à l’aide de l’interface utilisateur du service Lieux.
translation-type: tm+mt
source-git-commit: 5a21e734c0ef56c815389a9f08b445bedaae557a
workflow-type: tm+mt
source-wordcount: '419'
ht-degree: 22%

---


# Gestion des bibliothèques {#manage-libraries-places-ui}

Une bibliothèque est une collection de points d’intérêt. Vous pouvez avoir jusqu’à 150 000 POI dans une bibliothèque, et il peut y avoir jusqu’à 100 bibliothèques par organisation Experience Cloud.

Il existe plusieurs façons d’organiser vos points d’intérêt en bibliothèques en fonction de ce qui est le plus utile pour votre entreprise. Certains clients peuvent préférer créer une bibliothèque distincte pour chaque application mobile, tandis que d’autres peuvent utiliser des bibliothèques pour regrouper des types spécifiques d’API tels que des cafés, des parcs, des hôtels, etc. Par exemple, une grande société de divertissement peut avoir une bibliothèque qui comprend ses espaces extérieurs dans une bibliothèque et ses magasins de détail dans une autre. Une administration municipale pourrait avoir une bibliothèque qui comprend tous les bâtiments de la ville et une autre bibliothèque qui comprend tous les parcs de la ville.

Les bibliothèques sont définies comme suit :

| Keys: | Description: |
| :--- | :--- |
| Identifiant | un identifiant unique attribué à la bibliothèque lors de sa création |
| Nom | un nom convivial attribué à une bibliothèque |
| Classement | Ces classements peuvent être ignorés s’il n’y a pas de chevauchement de données géographiques dans votre organisation. En cas de superposition de POI, nous vous recommandons de placer chacune des clôtures virtuelles dans des bibliothèques distinctes afin qu’elles puissent être pondérées les unes par rapport aux autres. Un utilisateur ne peut se situer que dans une clôture virtuelle à la fois. <br><br>Le ranking le plus élevé de la clôture virtuelle dans laquelle se trouve un utilisateur détermine l’abonnement actuel de cet utilisateur à la clôture. S’il y a des géoofences qui ont le même classement de bibliothèque, la plus petite géoofence est la géofence actuelle de l’utilisateur. <br><br>Le SDK est aussi informé du *Dernier POI d’entrée* et du *Dernier POI de sortie*. Vous contrôlez donc intégralement la manière dont vous souhaitez que vos règles se déclenchent en fonction de l’interaction de l’utilisateur avec vos POI. |

## créer une bibliothèque ;

1. Connectez-vous à Places avec votre Adobe ID.
1. Dans la partie supérieure droite, cliquez sur **[!UICONTROL ...]** > **[!UICONTROL Manage Libraries]**.
1. Cliquez sur **[!UICONTROL New]**.
1. Tapez le nom.
1. Cliquez sur **[!UICONTROL Confirm]**.

## Modification du classement d’une bibliothèque dans l’interface utilisateur Lieux

1. Connectez-vous aux emplacements avec votre Adobe ID.
1. Dans la partie supérieure droite, cliquez sur **[!UICONTROL ...]** > **[!UICONTROL Manage Libraries]**.
1. Cliquez sur l’icône à gauche du nom de la bibliothèque et faites glisser la bibliothèque vers le nouveau classement.

## Renommer une bibliothèque

1. Connectez-vous aux emplacements avec votre Adobe ID.
1. Dans la partie supérieure droite, cliquez sur **[!UICONTROL ...]** > **[!UICONTROL Manage Libraries]**.
1. Localisez la bibliothèque que vous souhaitez supprimer.
1. Cliquez sur **[!UICONTROL ...]** et sélectionnez **[!UICONTROL Rename]**.
1. Mettez à jour le nom et cliquez sur **[!UICONTROL Save]**.

## Suppression d’une bibliothèque

1. Connectez-vous aux emplacements avec votre Adobe ID.
1. Dans la partie supérieure droite, cliquez sur **[!UICONTROL ...]** > **[!UICONTROL Manage Libraries]**.
1. Localisez la bibliothèque que vous souhaitez supprimer.
1. Cliquez sur **[!UICONTROL ...]** et sélectionnez **[!UICONTROL Delete]**.

