---
title: Questions fréquentes
description: Cette rubrique fournit des informations supplémentaires sur certaines questions fréquentes.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b

---


# Questions fréquentes

Voici quelques informations et des questions fréquentes sur le service Places.

## Taille et fiabilité

Important à noter pour toutes les géofinitions utilisées dans la surveillance de région à partir d’une application mobile, indépendamment de l’utilisation d’Adobe ou d’un autre service. Les systèmes d’exploitation recommandent certains paramètres à garder à l’esprit lors de la création de géoofences. Pour une fiabilité maximale, les clôtures doivent avoir un rayon d’au moins 100 mètres. Il est possible de créer de petites grilles, mais les événements d’entrée et de sortie peuvent ne pas être générés ou être générés une fois que l’utilisateur a cessé de se déplacer pendant une période donnée.

En outre, la précision et la fiabilité peuvent être réduites en fonction de conditions matérielles telles que l&#39;arrêt ou l&#39;indisponibilité du Wi-Fi, et en fonction de l&#39;emplacement de l&#39;appareil par rapport à l&#39;obstacle des signaux GPS. Par exemple, les zones montagneuses, les zones urbaines et les zones intérieures peuvent réduire la précision de l’emplacement à partir des systèmes d’exploitation iOS et Android.

## Comment se déclenche un événement de sortie ?

Lorsque le moniteur de lieux (SDK) obtient une nouvelle liste des points d’intérêt proches, il enregistre une région avec le système d’exploitation pour chaque point d’intérêt. Le système d’exploitation est maintenant chargé d’avertir le SDK lorsque le périphérique franchit une limite (entrée ou sortie) pour l’une des régions surveillées. Le SDK déclenche uniquement un événement de sortie lorsque le système d’exploitation avertit le SDK que l’événement s’est produit. La raison principale de cette notification est la sensibilité temporelle des données d’emplacement.

Si le système d’exploitation ne peut pas diffuser d’événement de sortie lorsque le périphérique quitte une région, il est plus sûr que le SDK omette simplement l’événement de sortie. Si le SDK fabrique un événement de sortie sans que l’événement ne soit déclenché par le système d’exploitation, il est possible que l’événement de sortie soit traité bien en dehors de la période pendant laquelle le périphérique se trouvait près de l’API.
