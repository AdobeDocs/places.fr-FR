---
title: 'Questions fréquemment posées '
description: Cette rubrique fournit des informations supplémentaires sur certaines questions fréquentes.
translation-type: tm+mt
source-git-commit: 5846577f10eb1d570465ad7f888feba6dd958ec9
workflow-type: tm+mt
source-wordcount: '552'
ht-degree: 1%

---


# Questions fréquemment posées 

Voici quelques informations et des questions fréquentes sur le service Places.

## Migration depuis trackLocation dans le SDK v4

Si vous effectuez une migration à partir du SDK v4 et que vous recherchez un remplacement de l’API `trackLocation`, reportez-vous à la rubrique [Utiliser le service Lieux sans surveillance de région Principale](use-places-without-active-monitoring.md).

## Taille et fiabilité

Important à noter pour toutes les géoinfractions utilisées dans la surveillance de région à partir d’une application mobile, indépendamment de l’utilisation d’Adobe ou d’un autre service. Les systèmes d’exploitation recommandent certains paramètres à garder à l’esprit lors de la création de géoinfractions. Pour une fiabilité maximale, les géoofences doivent avoir un rayon d&#39;au moins 100 mètres. Il est possible de créer des géoinfractions plus petites, mais les événements d’entrée et de sortie peuvent ne pas être générés, ou être générés une fois que l’utilisateur a cessé de se déplacer pendant un certain temps.

En outre, la précision et la fiabilité peuvent être réduites en fonction de conditions matérielles telles que la mise hors tension ou l&#39;indisponibilité du Wi-Fi, et en fonction de l&#39;emplacement du dispositif par rapport à l&#39;obstacle des signaux GPS. Par exemple, les zones montagneuses, les zones urbaines et les zones intérieures peuvent réduire la précision de l’emplacement à partir des systèmes d’exploitation iOS et Android.

## Comment se déclenche un événement de sortie ?

Lorsque le moniteur de lieux (SDK) obtient une nouvelle liste des points d’intérêt voisins, il enregistre une région avec le système d’exploitation pour chaque point d’intérêt. Le système d’exploitation est maintenant chargé d’informer le SDK lorsque le périphérique franchit une limite (entrée ou sortie) pour l’une des régions surveillées. Le SDK déclenche un événement de sortie uniquement lorsque le système d’exploitation avertit le SDK que le événement s’est produit. La raison principale de cette notification est la sensibilité temporelle des données d’emplacement.

Si le système d’exploitation ne parvient pas à fournir un événement de sortie lorsque le périphérique quitte une région, il est plus sûr que le SDK omette simplement le événement de sortie. Si le kit SDK fabrique un événement de sortie sans que le événement ne soit déclenché par le système d’exploitation, il est possible que le événement de sortie soit traité bien en dehors de la période pendant laquelle le périphérique se trouvait près de l’interface de ligne de commande.

## Nombre de points d’intérêt

Dans l’interface de gestion des points d’intérêt du service Places, les clients peuvent ajouter jusqu’à 150 000 points d’intérêt dans une bibliothèque spécifique. Si vous le souhaitez, les clients peuvent définir plusieurs bibliothèques afin de segmenter les groupes d’objets de propriété intellectuelle.

## Quelques remarques sur le changement d&#39;emplacement et la surveillance principale des régions

La surveillance d’une région géographique commence immédiatement après l’enregistrement des applications autorisées. Cependant, ne vous attendez pas à recevoir un événement immédiatement, car seuls les passages frontaliers génèrent un événement. En particulier, si l’emplacement de l’utilisateur se trouve déjà dans la région au moment de l’enregistrement, le gestionnaire d’emplacements ne génère pas automatiquement un événement. Au lieu de cela, votre application doit attendre que l’utilisateur franchisse la limite de la région avant qu’un événement ne soit généré et envoyé au délégué.

Soyez judicieux lorsque vous spécifiez l’ensemble de régions à surveiller. Les régions sont une ressource système partagée et le nombre total de régions disponibles à l&#39;échelle du système est limité. Pour cette raison, l’emplacement principal limite à 20 le nombre de régions qui peuvent être surveillées simultanément par une seule application. Pour contourner cette limite, pensez à n&#39;enregistrer que les régions situées dans le voisinage immédiat de l&#39;utilisateur.

[Consultez des informations supplémentaires sur le site]  des développeurs Apple (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11).
