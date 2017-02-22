---
title: "Determinazione dello stato del comando tramite gli assembly di interoperabilit&#224; | Microsoft Docs"
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
  - "assembly di interoperabilità, determinare lo stato del comando"
  - "comandi (gestione) con gli assembly di interoperabilità, stato"
ms.assetid: 2f5104d1-7b4c-4ca0-a626-50530a8f7f5c
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Determinazione dello stato del comando tramite gli assembly di interoperabilit&#224;
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un VSPackage deve tenere traccia dello stato dei comandi che è possibile gestire. L'ambiente non può determinare se un comando gestito all'interno del package VS diventa abilitato o disabilitato. È responsabilità del package VS per informare l'ambiente sugli stati di comando, ad esempio, lo stato di generale comandi, ad esempio **Taglia**, **Copia**, e **Incolla**.  
  
## Origini di notifica di stato  
 L'ambiente riceve informazioni sui comandi tramite VSPackage <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo, che fa parte dell'implementazione del VSPackage del <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> interfaccia. L'ambiente chiama il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo di VSPackage in due condizioni:  
  
-   Quando un utente apre un menu principale o un menu di scelta rapida \(pulsante destro del mouse\), l'ambiente viene eseguito il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> metodo su tutti i comandi di menu per determinare il proprio stato.  
  
-   Quando il package VS richiede che l'ambiente di aggiornare l'interfaccia utente \(UI\). Questo avviene quando i comandi che sono attualmente visibili all'utente, ad esempio il **Taglia**, **Copia**, e **Incolla** raggruppamento sulla barra degli strumenti standard, diventano abilitate e disabilitate in risposta alle azioni dell'utente e di contesto.  
  
 Poiché la shell ospita più package VS, se sono stati richiesti per eseguire il polling ogni VSPackage per determinare lo stato del comando eccessivamente sarebbero peggiorare le prestazioni della shell. Al contrario, il VSPackage attivamente necessario informare l'ambiente quando cambia la relativa interfaccia utente al momento della modifica. Per ulteriori informazioni sulla notifica di aggiornamento, vedere [Aggiornamento dell'interfaccia utente](../../extensibility/updating-the-user-interface.md).  
  
## Errore di notifica di stato  
 Errore di notifica di una modifica dello stato di comando nell'ambiente del pacchetto Visual Studio è possibile inserire l'interfaccia utente in uno stato incoerente. Tenere presente che qualsiasi i menu o nel contesto dei comandi di menu può trovarsi su una barra degli strumenti dall'utente. Pertanto, l'aggiornamento dell'interfaccia utente solo quando si apre un menu dal menu o nel contesto non è sufficiente.  
  
## Vedere anche  
 [Come package VS aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [Implementazione](../../extensibility/internals/command-implementation.md)