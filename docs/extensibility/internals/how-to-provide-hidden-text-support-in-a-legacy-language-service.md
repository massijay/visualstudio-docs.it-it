---
title: "Procedura: fornire supporto per il testo nascosto in un servizio di linguaggio Legacy | Microsoft Docs"
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
  - "testo, nascosto supporto"
  - "testo nascosto editor [Visual Studio SDK]"
  - "servizi di linguaggio, che implementa le aree di testo nascosto"
ms.assetid: 1c1dce9f-bbe2-4fc3-a736-5f78a237f4cc
caps.latest.revision: 21
caps.handback.revision: 21
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura: fornire supporto per il testo nascosto in un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

È possibile creare aree del testo nascosto oltre alle aree della struttura.  Le aree di testo nascosto possono essere controllate a client o archiviato dall'editor e vengono utilizzate per nascondere un'area di testo completamente.  L'editor viene visualizzata un'area nascosta come righe orizzontali.  Un esempio è la visualizzazione solo script editor HTML.  
  
## Procedura  
  
#### Per distribuire un'area di testo nascosto  
  
1.  chiamata `QueryService` per <xref:Microsoft.VisualStudio.TextManager.Interop.SVsTextManager>.  
  
     Viene restituito un puntatore a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager>.  
  
2.  Call <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.GetHiddenTextSession%2A>, passing in a pointer for a given text buffer.  Questa impostazione determina se una sessione di testo nascosto esiste già del buffer.  
  
3.  Se presente, non è necessario creare uno e un puntatore a un oggetto esistente di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> viene restituito.  Utilizzare questo puntatore per enumerare e creare aree del testo nascosto.  In caso contrario, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextManager.CreateHiddenTextSession%2A> di chiamata per creare una sessione di testo nascosto per il buffer.  
  
     Un puntatore all'oggetto di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession> viene restituito.  
  
    > [!NOTE]
    >  Quando si chiama `CreateHiddenTextSession`, è possibile specificare un client di testo nascosto \(ovvero <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextClient>\).  Il client di testo nascosto avvisa quando il testo nascosto o struttura viene espanso o compresso dall'utente.  
  
4.  Call <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiddenTextSession.AddHiddenRegions%2A> to add one or more new outline regions at a time, specifying the following information in the `reHidReg` \(<xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion>\) parameter:  
  
    1.  Specificare un valore di `hrtConcealed` nel membro di `iType` della struttura di <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> per indicare che si crea un'area nascosta, anziché un'area della struttura.  
  
        > [!NOTE]
        >  Una volta celate le aree vengono nascoste, le righe di visualizzazioni dell'editor automaticamente intorno alle aree nascoste per indicare la presenza.  
  
    2.  Specificare se l'area viene controllata su client o controllata dall'editor nei membri di `dwBehavior` della struttura di <xref:Microsoft.VisualStudio.TextManager.Interop.NewHiddenRegion> .  Implementazione intelligente della struttura può contenere una combinazione di regioni controllate ai client di testo nascosto e della struttura e dell'editore.