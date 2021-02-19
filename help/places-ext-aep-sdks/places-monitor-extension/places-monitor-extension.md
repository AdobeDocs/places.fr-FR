---
title: Extension du moniteur de lieux
description: L’extension Places Monitor gère les interactions avec le système d’exploitation afin d’enregistrer et de surveiller les points d’intérêt les plus proches de l’utilisateur.
translation-type: tm+mt
source-git-commit: 0ca2162f113fba6bfbd54443109068b1a506762b
workflow-type: tm+mt
source-wordcount: '146'
ht-degree: 0%

---


# Place l&#39;extension de moniteur {#places-monitor-extension}

L’extension Places Monitor gère les interactions avec le système d’exploitation afin d’enregistrer et de surveiller les points d’intérêt les plus proches de l’utilisateur. Cette extension récupère les points d&#39;accès qui doivent être enregistrés à partir de l&#39;extension Places et transmet les notifications d&#39;entrée et de sortie à l&#39;extension Places. Ces notifications seront disponibles en événements dans les règles Experience Platform Launch.

L&#39;extension Monitor est facultative, car certains clients peuvent déjà surveiller les régions du système d&#39;exploitation. Si tel est le cas, veillez à ajouter les API d&#39;extension Places pour recevoir les points d&#39;accès les plus proches de la base de données du service Places et pour transmettre les événements d&#39;entrée et de sortie afin que les actions appropriées puissent être entreprises.
