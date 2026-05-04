---
title: Notifications push
description: Cette section vous explique comment utiliser le service Places avec les notifications push.
exl-id: c094fe9c-6148-45ba-850a-f4c520d3362c
TQID: https://experienceleague.adobe.com/aaTMSoOkVUfbPDpPiRm7P3-8d8JSO9N0Ga12Hlmf-go
product_v2: id: d0a3eab4-7b10-4d96-a71e-6c0f8e7b7c87id: e55547f1-a1ff-40c6-8978-026e40ab7fa4id: edbd1a0e-46c8-49da-8c10-dba9ec80bba9
feature_v2: id: e08599ea-8888-4294-ba74-3ba0a7762a46
subfeature_v2: id: d2a6cbf4-df32-480f-909e-b42f66dcb9f0
topic_v2: id: d3cdead0-685a-4489-9250-4bb709942f66
source-git-commit: f962cef761f006c8e7d45b76ba24746e36bdaba6
workflow-type: tm+mt
source-wordcount: 229
ht-degree: 14%

---

# Notifications push

Mobile Services vous permet d’envoyer des notifications push aux segments Adobe Analytics. Dans Places Service, vous pouvez segmenter l’audience de votre message push à l’aide de ses interactions historiques avec vos points d’intérêt. Par exemple, vous pouvez envoyer un message aux utilisateurs qui se sont trouvés dans l’un de vos magasins au cours des 30 derniers jours.

Avant de commencer, vérifiez que vous avez terminé les tâches suivantes :

* Les données du service Places ont été traitées par Adobe Analytics.

  Cela signifie que votre application mobile a envoyé avec succès des données du service Places dans une suite de rapports et que les données sont disponibles pour la segmentation.

* Le canal Notification push dans Mobile Services est configuré.

  Pour plus d’informations, voir [Création d’un message push](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.htmlhtml?lang=fr).

* Découvrez comment envoyer une notification push à un segment Analytics dans Mobile Services.

  Pour plus d’informations, voir [Création d’un message push](https://experienceleague.adobe.com/docs/discontinued/using/mobile-services.htmlhtml?lang=fr).

## Envoyer une notification

Dans l&#39;onglet **[!UICONTROL Audience]** du workflow *Créer une notification push*, vous pouvez créer l&#39;audience de ce message de l&#39;une des manières suivantes :

* Dans la liste déroulante **[!UICONTROL Segments Analytics]**, sélectionnez un segment Adobe Analytics créé précédemment.

* Dans la section **[!UICONTROL Segment personnalisé]**, créez une audience à l’aide des paramètres de segment personnalisés disponibles.

![configuration d&#39;un message push](/help/assets/push-set-up.png)
