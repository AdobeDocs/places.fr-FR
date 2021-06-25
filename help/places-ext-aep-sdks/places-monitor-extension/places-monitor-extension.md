---
title: Extension Places Monitor
description: L’extension Surveiller les Places gère les interactions avec le système d’exploitation pour enregistrer et surveiller les points ciblés les plus proches de l’utilisateur.
exl-id: 254b33a0-79c4-4d51-8835-16e60f5c055e
source-git-commit: 8dcd777acf5d578b748afae9aa609c2349ea94a9
workflow-type: tm+mt
source-wordcount: '310'
ht-degree: 0%

---

# Extension Places Monitor {#places-monitor-extension}

L’extension Surveiller les Places gère les interactions avec le système d’exploitation pour enregistrer et surveiller les points ciblés les plus proches de l’utilisateur. Cette extension récupère les points ciblés à enregistrer à partir de l’extension Places et transmet les notifications d’entrée et de sortie à l’extension Places. Ces notifications seront disponibles en tant qu’événements dans les règles Experience Platform Launch.

L’extension Monitor est facultative, car certains clients surveillent peut-être déjà des régions avec le système d’exploitation. Si tel est le cas, veillez à ajouter les API d’extension Places pour recevoir les points ciblés les plus proches de la base de données de Places Service et pour transmettre les événements d’entrée et de sortie afin que les actions appropriées puissent être entreprises.

## Obsolescence du moniteur d’Places

Le 31 août 2021, l’extension Places Monitor pour les SDK mobiles Adobe Experience Platform sera abandonnée. L’extension Places Monitor ne recevra aucune mise à jour ni prise en charge au-delà du 31 août.

Les clients qui utilisent actuellement l’extension Places Monitor peuvent continuer à utiliser cette extension, en sachant qu’aucune mise à jour ou prise en charge supplémentaire ne sera disponible par Adobe.

L’obsolescence de l’extension Surveiller les Places n’a aucun impact négatif ou négatif sur l’extension Places Service qui continuera à être prise en charge avec des améliorations et des mises à jour.

Les clients qui souhaitent passer de l’extension Places Monitor à leur propre solution de surveillance doivent consulter la documentation pour : [Utilisez Places Service avec votre propre solution de surveillance](https://experienceleague.adobe.com/docs/places/using/using-your-own-monitor.html?lang=en). Ce document explique comment interagir avec le service Places en implémentant [Core Location services](https://developer.apple.com/documentation/corelocation) sur iOS ou [Location Services](https://developers.google.com/android/reference/com/google/android/gms/location/package-summary) à partir de Google Play.
