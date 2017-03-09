---
title: "Procedura: creare uno schema XML da un documento XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d6700a9-fd67-4794-8997-399589e99bec
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: creare uno schema XML da un documento XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'editor XML consente di creare uno schema XSD \(XML Schema Definition Language\) da un documento XML.Il documento di istanza XML determina come viene generato lo schema nel seguente modo:  
  
-   Se al documento XML non è associato alcuno schema o DTD \(Document Type Definition\), i dati del documento XML vengono utilizzati per inferire un nuovo schema XML.  
  
-   Se al documento XML è associata una DTD, la DTD esterna e il subset interno vengono convertiti in uno schema XML corrispondente.  
  
-   Se il documento XML contiene uno schema XDR \(XML\-Data Reduced\) inline, lo schema XDR viene convertito in uno schema XML corrispondente.  
  
 Gli schemi creati vengono quindi utilizzati per fornire IntelliSense al documento XML.  
  
 Per ulteriori informazioni sul motore di inferenza dello schema, vedere [Inferenza di uno schema XML](../Topic/Inferring%20an%20XML%20Schema.md).  
  
### Per creare uno schema XML  
  
1.  Caricare un documento di istanza XML nell'editor XML.  
  
2.  Fare clic sul pulsante **Crea schema** sulla **barra degli strumenti**.  
  
     Viene creato e aperto un documento di schema XML per ogni spazio dei nomi rilevato nel documento di istanza XML.Ogni schema viene aperto come file esterno temporaneo.  
  
     Gli schemi possono essere salvati su disco, aggiunti al progetto oppure eliminati.  
  
    > [!NOTE]
    >  Il comando **Crea schema** è disponibile anche nel menu di scelta rapida dell'editor XML e nel menu **XML**.  
  
## Vedere anche  
 [Editor XML](../xml-tools/xml-editor.md)