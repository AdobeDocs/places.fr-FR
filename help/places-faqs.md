---
title: Questions fréquentes
description: Cette rubrique fournit des informations supplémentaires sur certaines questions fréquentes.
translation-type: tm+mt
source-git-commit: 5846577f10eb1d570465ad7f888feba6dd958ec9

---


# Questions fréquentes

Voici quelques informations et des questions fréquentes sur le service Places.

## Migration depuis trackLocation dans le SDK v4

Si vous effectuez une migration depuis le SDK v4 et recherchez un remplacement de l’ `trackLocation` API, reportez-vous à la rubrique [Utiliser le service Places sans surveillance](use-places-without-active-monitoring.md)de région active.

## Taille et fiabilité

Important à noter pour toutes les géofinitions utilisées dans la surveillance de région à partir d’une application mobile, indépendamment de l’utilisation d’Adobe ou d’un autre service. Les systèmes d’exploitation recommandent certains paramètres à garder à l’esprit lors de la création de géoofences. Pour une fiabilité maximale, les clôtures doivent avoir un rayon d’au moins 100 mètres. Il est possible de créer des grilles plus petites, mais les  d’entrée et de sortie peuvent ne pas être générées ou être générées une fois que l’utilisateur a cessé de se déplacer pendant une période donnée.

En outre, la précision et la fiabilité peuvent être réduites en fonction de conditions matérielles telles que l&#39;arrêt ou l&#39;indisponibilité du Wi-Fi, et en fonction de l&#39;emplacement de l&#39;appareil par rapport à l&#39;obstacle des signaux GPS. Par exemple, les zones montagneuses, les zones urbaines et les zones intérieures peuvent réduire la précision de l’emplacement à partir des systèmes d’exploitation iOS et Android.

## Comment un de sortie -il déclencher ?

Lorsque le SDK (Places Monitor) obtient un nouveau  des points d’intérêt voisins, il enregistre une région avec le système d’exploitation pour chaque point d’intérêt. Le système d’exploitation est maintenant chargé d’avertir le SDK lorsque le périphérique franchit une limite (entrée ou sortie) pour l’une des régions surveillées. Le SDK déclenche un de sortie uniquement lorsque le système d’exploitation avertit le SDK que le  s’est produit. La raison principale de cette notification est la sensibilité temporelle des données d’emplacement.

Si le système d’exploitation ne parvient pas à fournir un de sortie lorsque le périphérique quitte une région, il est plus sûr pour le SDK de simplement omettre le  de sortie. Si le kit SDK fabrique un de sortie sans que le ne soit déclenché par le système d’exploitation, il existe un risque que le  de sortie soit traité bien en dehors de la période pendant laquelle le périphérique se trouvait près du point d’accès.

## Nombre de points d’intérêt

Dans l’interface de gestion des points d’intérêt du service Places, les clients peuvent ajouter jusqu’à 150 000 points d’intérêt dans une bibliothèque spécifique. Si vous le souhaitez, les clients peuvent définir plusieurs bibliothèques pour segmenter des groupes d’objets de valeur.

## Quelques remarques sur le changement d&#39;emplacement et la surveillance active de la région

La surveillance d’une région géographique commence immédiatement après l’enregistrement des applications autorisées. Toutefois, ne vous attendez pas à recevoir un  immédiatement, car seuls les passages à la frontière génèrent un  de. En particulier, si l’emplacement de l’utilisateur se trouve déjà dans la région au moment de l’enregistrement, le gestionnaire d’emplacements ne génère pas automatiquement un  de l’utilisateur. Au lieu de cela, votre application doit attendre que l’utilisateur franchisse la limite de la région avant qu’un ne soit généré et envoyé au délégué.

Soyez judicieux lorsque vous spécifiez l’ensemble de régions à surveiller. Les régions sont une ressource système partagée, et le nombre total de régions disponibles à l’échelle du système est limité. Pour cette raison, l’emplacement principal limite à 20 le nombre de régions qui peuvent être surveillées simultanément par une seule application. Pour contourner cette limite, pensez à n’enregistrer que les régions situées dans le voisinage immédiat de l’utilisateur.

[Voir des informations supplémentaires sur le site] des développeurs Apple (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
