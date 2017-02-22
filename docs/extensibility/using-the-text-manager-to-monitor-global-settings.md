---
title: "Mediante la gestione di testo per monitorare le impostazioni globali | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - controllare le impostazioni globali"
  - "editor [Visual Studio SDK], legacy - gestore di testo"
ms.assetid: 023e7671-cf65-419c-9bc1-3c4ee92aa436
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Mediante la gestione di testo per monitorare le impostazioni globali
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Se si implementa un editor principale, è necessario monitorare le modifiche apportate alle impostazioni globali, poiché tali modifiche possono influire sull'istanza dell'editor.  È possibile tenere traccia delle modifiche attendendo gli eventi generati dall'amministratore del testo.  Ad esempio, quando si specifica una preferenza generale per l'aspetto o il comportamento di un componente nell'editor principale, ad esempio il relativo oggetto dati del documento, gli archivi di gestione del testo queste informazioni e la comunicazione a tutti i client interessati.  
  
## Funzioni di gestione del testo  
 L'amministratore di testo genera eventi sia una serie di impostazioni, incluse le seguenti:  
  
-   Se un buffer è incluso nel controllo del codice sorgente  
  
-   La registrazione per le notifiche delle modifiche ai file  
  
-   Come tenere traccia delle visualizzazioni sono associate a determinati buffer  
  
-   Preferenze di colorazione del testo  
  
-   Scheda in base alle preferenze dello spazio  
  
 Le esigenze specifiche relative a un linguaggio specificato non vengono gestite dall'amministratore del testo.  queste impostazioni devono essere gestite da ogni servizio di linguaggio.  
  
 La notifica degli eventi per la gestione del testo è fornita dall'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextManagerEvents> .  Implementare questa interfaccia sull'oggetto client per gestire gli eventi ha generato la gestione del testo.  Si effettua la registrazione per questi eventi tramite l'interfaccia di <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> sull'amministratore del testo.  
  
## Vedere anche  
 [Nell'Editor di componenti di base](../extensibility/inside-the-core-editor.md)   
 [Editor Features](http://msdn.microsoft.com/it-it/bdac940d-1f14-4019-a01f-fd0bb3dc7198)