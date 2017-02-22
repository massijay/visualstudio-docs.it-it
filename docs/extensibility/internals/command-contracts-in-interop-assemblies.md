---
title: "Contratti di comando nell&#39;assembly di interoperabilit&#224; | Microsoft Docs"
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
  - "comandi (gestione) con gli assembly di interoperabilità, contratti di comando"
  - "assembly di interoperabilità, contratti di comando"
ms.assetid: 57245708-f539-42dc-8963-2754a48f0189
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Contratti di comando nell&#39;assembly di interoperabilit&#224;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il contratto di base per la gestione dei comandi tramite il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia è che l'ambiente chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo per determinare se il comando è supportato e, se supportato, per determinare il relativo stato e testo. Quindi, l'ambiente chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo per eseguire il comando.  
  
 Il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> \(metodo\) viene gestita in modo identico per tutti i comandi. Continuare la comunicazione, se necessario \(ad esempio, con elenchi a discesa\), viene gestita mediante la chiamata di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.Exec%2A> metodo con i parametri appropriati. L'interpretazione di questi parametri dipende dal comando specificato.  
  
 Se la destinazione del comando restituisce i valori nel parametro di output, il chiamante è sempre responsabile liberando le risorse che sono state allocate. Poiché questo parametro è una variante, deselezionando la variante libera le risorse.  
  
 Nei casi in cui i comandi devono funzionare all'interno di una finestra gerarchia, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> necessario utilizzare l'interfaccia. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy> interfaccia dispone di un contratto simile con metodi simili: <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.QueryStatusCommand%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIHierarchy.ExecCommand%2A>.  
  
## Vedere anche  
 [Come package VS aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Routing dei comandi in VS](../../extensibility/internals/command-routing-in-vspackages.md)   
 [Implementazione](../../extensibility/internals/command-implementation.md)