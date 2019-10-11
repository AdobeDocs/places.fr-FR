---
title: Gestion des bibliothèques dans l’interface utilisateur Lieux
seo-title: Gestion des bibliothèques dans l’interface utilisateur Lieux
description: Gérez vos bibliothèques à l’aide de l’interface utilisateur Lieux.
seo-description: Gérez vos bibliothèques à l’aide de l’interface utilisateur Lieux.
translation-type: tm+mt
source-git-commit: ef3d77eba407013e1f701ed001ef9ab7b3818e07

---


# Gestion des bibliothèques dans l’interface utilisateur Lieux {#manage-libraries-places-ui}

Une bibliothèque est une collection d’objets d’intérêt. Vous pouvez avoir jusqu’à 150 000 points d’intérêt dans une bibliothèque et jusqu’à 100 bibliothèques par organisation Experience Cloud.

Il existe différentes manières d’organiser vos points d’intérêt en bibliothèques selon ce qui est le plus utile pour votre entreprise. Certains clients peuvent préférer créer une bibliothèque distincte pour chaque application mobile, tandis que d’autres utilisateurs peuvent utiliser des bibliothèques pour regrouper des types spécifiques d’API, tels que des cafés, des parcs, des hôtels, etc. Par exemple, une grande entreprise de divertissement peut avoir une bibliothèque qui comprend ses espaces extérieurs dans une bibliothèque et ses magasins de détail dans une autre. Une municipalité pourrait avoir une bibliothèque qui comprend tous les bâtiments de la ville et une autre bibliothèque qui comprend tous les parcs de la ville.

Les bibliothèques sont définies par les éléments suivants :

| Clés: | Description: |
| :--- | :--- |
| ID | un identifiant unique affecté à la bibliothèque lors de sa création |
| Nom | un nom convivial donné à une bibliothèque |
| Classement | Ces classements peuvent être ignorés s’il n’y a aucune superposition de géofences dans votre organisation. S’il y a des points d’intérêt qui se chevauchent, nous vous recommandons de placer chacune des géofinitions dans des bibliothèques distinctes afin qu’elles puissent être pondérées les unes par rapport aux autres. Un utilisateur ne peut se trouver qu’une seule géofence à la fois. <br><br>Le plus haut rang des références géographiques dans lesquelles se trouve un utilisateur détermine son appartenance actuelle à la géofence. S’il y a des graffitis qui ont le même classement de bibliothèque, la plus petite de ces graffitis est la géofence actuelle de l’utilisateur. <br><br>Le kit SDK est également conscient des points d’intérêt *Dernière entrée* et *Dernière sortie* . Vous avez donc le contrôle total de la manière dont vous souhaitez que vos règles se déclenchent en fonction de l’interaction de l’utilisateur avec vos points d’intérêt. |

## Créer une bibliothèque

1. Connectez-vous à Adobe Places avec votre Adobe ID.
2. Dans le coin supérieur droit, cliquez sur **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
3. Cliquez sur **[!UICONTROL New]** (Nouvelle propriété).
4. Entrez le nom.
5. Cliquez sur **[!UICONTROL Confirm]** (Nouvelle propriété).

## Modification du classement d’une bibliothèque dans l’interface utilisateur Lieux

1. Connectez-vous à Adobe Places avec votre Adobe ID.
2. Dans le coin supérieur droit, cliquez sur **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
3. Cliquez sur l’icône à gauche du nom de la bibliothèque et faites glisser la bibliothèque vers le nouveau rang.

## Modification du nom d’une bibliothèque

1. Connectez-vous à Adobe Places avec votre Adobe ID.
2. Dans le coin supérieur droit, cliquez sur **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
3. Localisez la bibliothèque à supprimer.
4. Cliquez sur **[!UICONTROL ...]** puis sélectionnez **[!UICONTROL Rename]**.
5. Mettez à jour le nom et cliquez sur **[!UICONTROL Save]**.

## Suppression d’une bibliothèque

1. Connectez-vous à Adobe Places avec votre Adobe ID.
2. Dans le coin supérieur droit, cliquez sur **[!UICONTROL ...]** &gt; **[!UICONTROL Manage Libraries]**.
3. Localisez la bibliothèque à supprimer.
4. Cliquez sur **[!UICONTROL ...]** puis sélectionnez **[!UICONTROL Delete]**.

