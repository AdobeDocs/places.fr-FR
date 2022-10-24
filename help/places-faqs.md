---
title: Questions fréquentes
description: Cette rubrique fournit des informations supplémentaires sur certaines questions fréquentes.
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
source-git-commit: 010de286c25c1eeb989fb76e3c2adaa82ac9fd35
workflow-type: tm+mt
source-wordcount: '554'
ht-degree: 1%

---

# Questions fréquentes

Voici des informations et des questions fréquentes sur Places Service.

## Migration depuis trackLocation dans le SDK v4

Si vous effectuez une migration à partir du SDK v4 et que vous recherchez un remplacement de la variable `trackLocation` API, reportez-vous au sujet [Utilisation du service Places sans surveillance de région Principale](use-places-without-active-monitoring.md).

## Taille et fiabilité

Important à noter pour toutes les clôtures virtuelles utilisées dans la surveillance de région à partir d’une application mobile, indépendamment de l’utilisation d’Adobe ou d’un autre service. Les systèmes d’exploitation recommandent certains paramètres à garder à l’esprit lors de la création de clôtures virtuelles. Pour une fiabilité maximale, les clôtures virtuelles doivent avoir un rayon d’au moins 100 mètres. Il est possible de créer des clôtures virtuelles plus petites, mais les événements d’entrée et de sortie peuvent ne pas être générés, ou être générés une fois que l’utilisateur a cessé de se déplacer pendant un certain temps.

En outre, la précision et la fiabilité peuvent être réduites en fonction de conditions matérielles telles que la désactivation ou l’indisponibilité de la connexion Wi-Fi, et en fonction de la position de l’appareil par rapport à la limitation des signaux GPS. Par exemple, les zones montagneuses, les zones urbaines et les zones intérieures peuvent réduire la précision de la localisation à partir des systèmes d’exploitation iOS et Android.

## Comment un événement de sortie se déclenche-t-il ?

Le moniteur de région implémenté doit demander une liste des points ciblés à proximité. Une fois reçue, une région doit être enregistrée auprès du système d’exploitation pour chaque point ciblé. Le système d’exploitation est désormais chargé d’informer le SDK lorsque l’appareil dépasse une limite (entrée ou sortie) pour l’une des régions surveillées. Le SDK déclenche un événement exit uniquement lorsque le système d’exploitation avertit le SDK que l’événement s’est produit. La raison principale de cette notification est le respect de l’heure des données de localisation.

Si le système d’exploitation ne peut pas diffuser d’événement de sortie lorsque l’appareil quitte une région, il est plus sûr que le SDK omette simplement l’événement de sortie. Si le SDK crée un événement de sortie sans que l’événement soit déclenché par le système d’exploitation, il est possible que l’événement de sortie soit traité bien en dehors de la période pendant laquelle l’appareil se trouvait près du point ciblé.

## Nombre de points ciblés

Dans l’interface de gestion des points ciblés du service Places, les clients peuvent ajouter jusqu’à 150 000 points ciblés dans une bibliothèque spécifique. Si vous le souhaitez, les clients peuvent définir plusieurs bibliothèques pour segmenter les groupes de points ciblés.

## Remarques sur le changement de localisation et la surveillance principale des régions

La surveillance d’une région géographique commence immédiatement après l’enregistrement des applications autorisées. Toutefois, ne vous attendez pas à recevoir un événement immédiatement, car seuls les passages aux limites génèrent un événement. En particulier, si l’emplacement de l’utilisateur se trouve déjà dans la région au moment de l’enregistrement, le gestionnaire d’emplacement ne génère pas automatiquement un événement. Au lieu de cela, votre application doit attendre que l’utilisateur franchisse la limite de région avant qu’un événement ne soit généré et envoyé au délégué.

Soyez judicieux lorsque vous spécifiez l’ensemble de régions à surveiller. Les régions sont une ressource de système partagée et le nombre total de régions disponibles à l’échelle du système est limité. Pour cette raison, l’emplacement principal limite à 20 le nombre de régions qui peuvent être surveillées simultanément par une seule application. Pour contourner cette limite, envisagez d’enregistrer uniquement les régions situées dans le voisinage immédiat de l’utilisateur.

[Consultez des informations supplémentaires sur le site des développeurs Apple] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
