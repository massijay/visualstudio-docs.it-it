---
title: "Modelli XSLT predefiniti | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 773dd34e-67d3-4997-8df9-b71e7f880d88
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Modelli XSLT predefiniti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se il foglio di stile non contiene corrispondenti regole di modello esplicite, nel corso dell'elaborazione XSLT viene utilizzato un modello predefinito.Il modello predefinito, noto anche come regola di modello incorporata, è definito nella sezione 5.8 della raccomandazione W3C XSLT 1.0 \(informazioni in lingua inglese\).Il modello predefinito consente al processore XSLT di elaborare un nodo anche in assenza di corrispondenti regole di modello esplicite.Tuttavia, poiché la regola di modello incorporata non è definita in modo esplicito nel foglio di stile, possono verificarsi trasformazioni XSLT impreviste o ambigue.  
  
 Il debugger XSLT visualizza il codice dei modelli XSLT predefiniti.Nel corso di una trasformazione XSLT il modello predefinito eventualmente utilizzato viene visualizzato in una finestra del debugger.Ciò consente di eseguire il codice del modello e di impostare punti di interruzione nelle relative istruzioni.  
  
## Vedere anche  
 [Debug di XSLT](../xml-tools/debugging-xslt.md)