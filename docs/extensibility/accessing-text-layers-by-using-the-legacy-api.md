---
title: "L&#39;accesso ai livelli di testo tramite l&#39;API Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - livelli testo"
ms.assetid: 2258fcdd-38d1-479d-b8f8-1d4e6525f72c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# L&#39;accesso ai livelli di testo tramite l&#39;API Legacy
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un livello di testo in genere incapsula un determinato aspetto di layout di testo.  Ad esempio, nasconde di un livello di “funzione doppia„ di testi prima e dopo una funzione contenente il cursore \(punto di inserimento del testo\).  
  
 Un livello di testo si trova tra un buffer e una visualizzazione e la modifica della modalità in cui la visualizzazione del contenuto del buffer.  
  
## Il testo alle informazioni del livello  
 Nell'elenco descritto il funzionamento dei livelli di testo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]:  
  
-   Il testo in un livello di testo può essere decoratoe con colorazione della sintassi e i marcatori.  
  
-   Attualmente non è possibile implementare per contenere i livelli.  
  
-   Un livello espone <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, derivato da <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLines>.  Il buffer di testo stesso viene implementato come livello, che consente a una visualizzazione per gestire polymorphically dei livelli sottostanti.  
  
-   Un numero qualsiasi di livelli possono rientrare tra la visualizzazione e il buffer.  Ogni livello consente solo del livello in e la visualizzazione vengono elaborate in gran parte del livello in primo piano.  \(Nella visualizzazione sono presenti alcune informazioni sul buffer.\)  
  
-   Un livello può influire soltanto sui livelli inclusi in.  Non può influire sui livelli oltre che appartenga gli eventi standard.  
  
-   Nell'editor, il testo nascosto, il testo sintetico e il ritorno a capo automatico vengono distribuiti come livelli.  È possibile implementare il testo nascosto e sintetico senza interagire direttamente con i livelli.  Per ulteriori informazioni, vedere [La struttura in un servizio di linguaggio Legacy](../extensibility/internals/outlining-in-a-legacy-language-service.md) e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsSyntheticTextSession>.  
  
-   Ogni livello di testo dispone di un proprio sistema di coordinate locale che viene esposto tramite l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer> .  Il livello di sovrapposizione delle righe, ad esempio, potrebbe contenere due righe mentre il buffer di testo sottostante potrebbe contenere solo una riga.  
  
-   La visualizzazione comunica ai livelli tramite l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLayeredTextView> .  Utilizzare questa interfaccia per risolvere le differenze tra le coordinate di visualizzazione con le coordinate del buffer.  
  
-   Qualsiasi livello come il livello sintetico di testo che genera il testo deve fornire un'implementazione locale dell'entity\_M:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer.CreateTrackingPoint\(System.Int32, System.Int32, Microsoft.VisualStudio.TextManager  
  
-   Oltre a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLayer>, un livello di testo deve implementare <xref:Microsoft.VisualStudio.OLE.Interop.IConnectionPointContainer> e generare eventi in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLinesEvents> collegare.  
  
## Vedere anche  
 [Colorazione in editor personalizzati della sintassi](../extensibility/syntax-coloring-in-custom-editors.md)   
 [Utilizzando gli indicatori di testo con l'API Legacy](../extensibility/using-text-markers-with-the-legacy-api.md)   
 [Personalizzazione di menu e controlli di Editor utilizzando l'API Legacy](../extensibility/customizing-editor-controls-and-menus-by-using-the-legacy-api.md)