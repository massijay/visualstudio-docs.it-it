---
title: "Formattazione in un servizio di linguaggio Legacy automatica | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "formattazione di servizi di linguaggio, automatico"
ms.assetid: c210fc94-77bd-4694-b312-045087d8a549
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Formattazione in un servizio di linguaggio Legacy automatica
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Con la formattazione automatica, un servizio di linguaggio viene automaticamente inserito un frammento di codice quando l'utente inizia a digitare un costrutto di codice noto.  
  
## Comportamento di formattazione automatica  
 Ad esempio, quando si digita `if`, il servizio di linguaggio inserisce automaticamente le parentesi graffe corrispondenti, o se si preme il tasto INVIO, il servizio di linguaggio forza il punto di inserimento nella nuova riga al livello di rientro appropriato, come se la riga precedente viene aperto un nuovo ambito.  
  
 Il filtro del comando utilizzato per il resto del servizio di linguaggio anche essere utilizzato per la formattazione automatica.  È inoltre possibile evidenziare le parentesi graffe corrispondenti dall'entity\_M:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.HighlightMatchingBrace\(System.UInt32, System.UInt32, Microsoft.VisualStudio.TextManager.Interop.TextSpan\[\]\) chiamante.  
  
## Vedere anche  
 [Lo sviluppo di un servizio di linguaggio](../../extensibility/internals/developing-a-legacy-language-service.md)