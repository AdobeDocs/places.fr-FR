---
title: Questions fréquentes
description: Cette rubrique fournit des informations supplémentaires sur certaines questions fréquentes.
exl-id: cee9f447-5e50-4ed8-b37b-baecbc0e9b7b
TQID: https://experienceleague.adobe.com/LL9eLMDJaq8ZmeiZxv28QZoqXL1A0QKZ-DvTDUx4Gnw
product_v2:
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
source-wordcount: 557
ht-degree: 1%

---

# Questions fréquentes

Voici quelques informations et questions fréquentes sur Places Service.

## Migration à partir de trackLocation dans le SDK v4

Si vous migrez depuis le SDK v4 et que vous recherchez un remplacement à l’API `trackLocation`, reportez-vous à la rubrique [Utilisation du service Places sans surveillance active des zones géographiques](use-places-without-active-monitoring.md).

## Taille et fiabilité

Il est important de noter que toutes les barrières géographiques sont utilisées dans la surveillance des zones géographiques à partir d’une application mobile, que vous utilisiez Adobe ou un autre service. Les systèmes d’exploitation recommandent certains paramètres à garder à l’esprit lors de la création de clôtures géographiques. Pour une fiabilité maximale, les clôtures géographiques doivent avoir un rayon d&#39;au moins 100 mètres. Vous pouvez créer des barrières géographiques plus petites, mais les événements d’entrée et de sortie peuvent ne pas être générés, ou peuvent être générés après que l’utilisateur ou l’utilisatrice a cessé de se déplacer pendant un certain temps.

En outre, la précision et la fiabilité peuvent être réduites en fonction de conditions matérielles telles que l&#39;arrêt ou l&#39;indisponibilité du wi-fi, et également en fonction de l&#39;emplacement du dispositif par rapport à l&#39;obstruction des signaux GPS. Par exemple, les zones montagneuses, les zones urbaines et les zones intérieures peuvent réduire la précision de l’emplacement à partir des systèmes d’exploitation iOS et Android.

## Comment déclenche un événement de sortie ?

Le moniteur de région mis en œuvre doit demander une liste des points d’intérêt à proximité. Une fois reçu, une région doit être enregistrée auprès du système d’exploitation pour chaque point d’intérêt. Le système d’exploitation est désormais chargé d’avertir le SDK lorsque l’appareil traverse une limite (entrée ou sortie) pour l’une des régions surveillées. Le SDK ne déclenche un événement de sortie que lorsque le système d’exploitation informe le SDK que l’événement s’est produit. La raison principale de cette notification est la sensibilité temporelle des données de localisation.

Si le système d’exploitation ne peut pas diffuser d’événement de sortie lorsque l’appareil quitte une zone géographique, il est plus sûr pour le SDK d’omettre simplement l’événement de sortie. Si le SDK fabrique un événement de sortie sans que l’événement ne soit déclenché par le système d’exploitation, il y a un risque que l’événement de sortie soit traité bien en dehors de la période pendant laquelle l’appareil était proche du point d’intérêt.

## Nombre de points d’intérêt

Dans l’interface de gestion des points d’intérêt du service Places, les clients peuvent ajouter jusqu’à 150 000 points d’intérêt dans une bibliothèque spécifique. Les clients peuvent définir plusieurs bibliothèques pour segmenter les regroupements de points d’intérêt, si nécessaire.

## Quelques remarques sur le changement d’emplacement et la surveillance active des zones géographiques

La surveillance d&#39;une région géographique commence immédiatement après l&#39;enregistrement des applications autorisées. Toutefois, ne vous attendez pas à recevoir un événement immédiatement, car seuls les franchissements de frontière génèrent un événement. En particulier, si l’emplacement de l’utilisateur se trouve déjà dans la région au moment de l’enregistrement, le gestionnaire d’emplacements ne génère pas automatiquement d’événement. Au lieu de cela, votre application doit attendre que l’utilisateur franchisse la limite régionale avant qu’un événement ne soit généré et envoyé au délégué.

Soyez judicieux lors de la spécification de l’ensemble de régions à surveiller. Les régions sont une ressource système partagée et le nombre total de régions disponibles à l&#39;échelle du système est limité. Pour cette raison, Core Location limite à 20 le nombre de régions pouvant être surveillées simultanément par une seule application. Pour contourner cette limite, envisagez de n’enregistrer que les régions situées à proximité immédiate de l’utilisateur ou de l’utilisatrice.

[Voir les informations supplémentaires sur le site du développeur d’Apple] (https://developer.apple.com/library/archive/documentation/UserExperience/Conceptual/LocationAwarenessPG/RegionMonitoring/RegionMonitoring.html#//apple_ref/doc/uid/TP40009497-CH9-SW11)
