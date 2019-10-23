---
title: Extension du moniteur des lieux
seo-title: Extension du moniteur des lieux
description: L’extension Places Monitor gère les interactions avec le système d’exploitation afin d’enregistrer et de surveiller les points d’intérêt les plus proches de l’utilisateur.
seo-description: 'L’extension Places Monitor gère les interactions avec le système d’exploitation afin d’enregistrer et de surveiller les points d’intérêt les plus proches de l’utilisateur. '
translation-type: tm+mt
source-git-commit: ef720c112bc0de386e070094629c5bab69938e76

---


# Extension du moniteur des lieux {#places-monitor-extension}

L’extension Places Monitor gère les interactions avec le système d’exploitation afin d’enregistrer et de surveiller les points d’intérêt les plus proches de l’utilisateur. Cette extension récupère les points d’intérêt qui doivent être enregistrés à partir de l’extension Places et transmet les notifications d’entrée et de sortie à l’extension Places. Ces notifications seront disponibles en tant qu’événements dans les règles de lancement de plateforme d’expérience.

L’extension Monitor est facultative, car certains clients peuvent déjà surveiller des régions avec le système d’exploitation. Si tel est le cas, veillez à ajouter les API d’extension Places pour recevoir les points d’intérêt les plus proches de la base de données Places et pour transmettre les événements d’entrée et de sortie afin que les actions appropriées puissent être entreprises.
