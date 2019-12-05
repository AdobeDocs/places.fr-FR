---
title: Gestion des bibliothèques dans l’interface utilisateur Lieux
description: Gérez vos bibliothèques à l’aide de l’interface utilisateur Lieux.
translation-type: tm+mt
source-git-commit: 5a0705f02c8ecd540506b628371aec45107df7b2

---


# Manage libraries {#manage-libraries-places-ui}

Une bibliothèque est une collection d’objets d’intérêt. Vous pouvez avoir jusqu’à 150 000 points d’intérêt dans une bibliothèque et jusqu’à 100 bibliothèques par organisation Experience Cloud.

Il existe différentes manières d’organiser vos points d’intérêt en bibliothèques selon ce qui est le plus utile pour votre entreprise. Certains clients peuvent préférer créer une bibliothèque distincte pour chaque application mobile, tandis que d’autres utilisateurs peuvent utiliser des bibliothèques pour regrouper des types spécifiques d’API, tels que des cafés, des parcs, des hôtels, etc. Par exemple, une grande entreprise de divertissement peut avoir une bibliothèque qui comprend ses espaces extérieurs dans une bibliothèque et ses magasins de détail dans une autre. Une municipalité pourrait avoir une bibliothèque qui comprend tous les bâtiments de la ville et une autre bibliothèque qui comprend tous les parcs de la ville.

Les bibliothèques sont définies par les éléments suivants :

| Clés: | Description: |
| :--- | :--- |
| ID | un identifiant unique affecté à la bibliothèque lors de sa création |
| Nom | un nom convivial donné à une bibliothèque |
| Classement | Ces classements peuvent être ignorés s’il n’y a aucune superposition de géofences dans votre organisation. En cas de superposition de POI, nous vous recommandons de placer chacune des clôtures virtuelles dans des bibliothèques distinctes afin qu’elles puissent être pondérées les unes par rapport aux autres. Un utilisateur ne peut se situer que dans une clôture virtuelle à la fois. <br><br>Le ranking le plus élevé de la clôture virtuelle dans laquelle se trouve un utilisateur détermine l’abonnement actuel de cet utilisateur à la clôture. Si les clôtures virtuelles d’un utilisateur ont le même ranking de bibliothèque, la plus petite clôture est celle dans laquelle cet utilisateur se trouve actuellement. <br><br>Le SDK est aussi informé du *Dernier POI d’entrée* et du *Dernier POI de sortie*. Vous contrôlez donc intégralement la manière dont vous souhaitez que vos règles se déclenchent en fonction de l’interaction de l’utilisateur avec vos POI. |

## Créer une bibliothèque

1. Connectez-vous à Places avec votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
1. Cliquez sur **[!UICONTROL New]** (Nouvelle propriété).
1. Entrez le nom.
1. Cliquez sur **[!UICONTROL Confirm]** (Nouvelle propriété).

## Modification du classement d’une bibliothèque dans l’interface utilisateur Lieux

1. Connectez-vous à Places avec votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
1. Cliquez sur l’icône à gauche du nom de la bibliothèque et faites glisser la bibliothèque vers le nouveau rang.

## Modification du nom d’une bibliothèque

1. Connectez-vous à Places avec votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
1. Localisez la bibliothèque à supprimer.
1. Cliquez sur **[!UICONTROL ...]** puis sélectionnez **[!UICONTROL Rename]**.
1. Mettez à jour le nom et cliquez sur **[!UICONTROL Save]**.

## Suppression d’une bibliothèque

1. Connectez-vous à Places avec votre Adobe ID.
1. Dans le coin supérieur droit, cliquez sur **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
1. Localisez la bibliothèque à supprimer.
1. Cliquez sur **[!UICONTROL ...]** puis sélectionnez **[!UICONTROL Delete]**.

