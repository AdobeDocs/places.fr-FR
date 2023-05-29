---
title: Gestion des bibliothèques dans l’interface utilisateur du service Places
description: Gérez vos bibliothèques à l’aide de l’interface utilisateur du service Places.
exl-id: 2fb999b4-854a-430f-bb89-4c786d1a89cc
source-git-commit: 4ab15ded930b31e4e06920af31f37fdfe45df8eb
workflow-type: tm+mt
source-wordcount: '432'
ht-degree: 22%

---

# Gestion des bibliothèques {#manage-libraries-places-ui}

Une bibliothèque est une collection de points ciblés. Vous pouvez avoir jusqu’à 150 000 points ciblés dans une bibliothèque et il peut y avoir jusqu’à 100 bibliothèques par organisation Experience Cloud.

Il existe plusieurs façons d’organiser vos points ciblés en bibliothèques en fonction de ce qui est le plus utile à votre entreprise. Certains clients peuvent préférer créer une bibliothèque distincte pour chaque application mobile, tandis que d’autres clients peuvent utiliser des bibliothèques pour regrouper des types spécifiques de points ciblés tels que des cafés, des parcs, des hôtels, etc. Par exemple, une grande entreprise de divertissement peut avoir une bibliothèque qui comprend ses installations en plein air dans une bibliothèque et ses magasins dans une autre bibliothèque. Une municipalité pourrait avoir une bibliothèque qui comprend tous les bâtiments de la ville et une autre bibliothèque qui comprend tous les parcs de la ville.

Les bibliothèques sont définies par ce qui suit :

| Clés: | Description: |
| :--- | :--- |
| Identifiant | un identifiant unique attribué à la bibliothèque lors de sa création ; |
| Nom | un nom convivial donné à une bibliothèque ; |
| Classement | Ces classements peuvent être ignorés s’il n’existe aucun chevauchement de clôtures virtuelles dans votre entreprise. En cas de superposition de POI, nous vous recommandons de placer chacune des clôtures virtuelles dans des bibliothèques distinctes afin qu’elles puissent être pondérées les unes par rapport aux autres. Un utilisateur ne peut se situer que dans une clôture virtuelle à la fois. <br><br>Le ranking le plus élevé de la clôture virtuelle dans laquelle se trouve un utilisateur détermine l’abonnement actuel de cet utilisateur à la clôture. S’il existe des clôtures virtuelles présentant le même classement de bibliothèque, la plus petite clôture est la clôture virtuelle actuelle de l’utilisateur. <br><br>Le SDK est aussi informé du *Dernier POI d’entrée* et du *Dernier POI de sortie*. Vous contrôlez donc intégralement la manière dont vous souhaitez que vos règles se déclenchent en fonction de l’interaction de l’utilisateur avec vos POI. |

## créer une bibliothèque ;

1. Connectez-vous à Places avec votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur **[!UICONTROL ...]**  > **[!UICONTROL Gestion des bibliothèques]**.
1. Cliquez sur **[!UICONTROL Nouveau]**.
1. Saisissez le nom.
1. Cliquez sur **[!UICONTROL Confirmer]**.

## Modification du classement d’une bibliothèque dans l’interface utilisateur de Places

1. Connectez-vous à Places avec votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur **[!UICONTROL ...]**  > **[!UICONTROL Gestion des bibliothèques]**.
1. Cliquez sur l’icône située à gauche du nom de la bibliothèque et faites glisser la bibliothèque vers le nouveau rang.

## Renommer une bibliothèque

1. Connectez-vous à Places avec votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur **[!UICONTROL ...]** > **[!UICONTROL Gestion des bibliothèques]**.
1. Recherchez la bibliothèque que vous souhaitez supprimer.
1. Cliquez sur **[!UICONTROL ...]** et sélectionnez **[!UICONTROL Renommer]**.
1. Mettez à jour le nom et cliquez sur **[!UICONTROL Enregistrer]**.

## Suppression d’une bibliothèque

1. Connectez-vous à Places avec votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur **[!UICONTROL ...]** > **[!UICONTROL Gestion des bibliothèques]**.
1. Recherchez la bibliothèque que vous souhaitez supprimer.
1. Cliquez sur **[!UICONTROL ...]** et sélectionnez **[!UICONTROL Supprimer]**.
