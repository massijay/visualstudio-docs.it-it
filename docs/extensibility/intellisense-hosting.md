---
title: "Hosting di IntelliSense | Microsoft Docs"
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
  - "editor [Visual Studio SDK], legacy - hosting di IntelliSense"
ms.assetid: 20c61f8a-d32d-47e2-9c67-bf721e2cbead
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Hosting di IntelliSense
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio consente l'hosting di IntelliSense.  L'hosting di IntellSense consente di fornire IntelliSense per il codice non ospitato dall'editor di testo Visual Studio.  
  
## IntelliSense che ospita utilizzo  
 In Visual Studio, qualsiasi codice che abbia accesso al completamento impostato e un buffer di testo possono ottenere le finestre di IntelliSense qualsiasi punto dell'interfaccia \(UI\) utente.  Alcuni scenari di esempio riportato di seguito vengono di completamento nella finestra di **espressione di controllo** il campo o della condizione di una finestra delle proprietà.  
  
### interfacce di implementazione  
  
#### IVsIntellisenseHost  
 Qualsiasi componente dell'interfaccia utente che ospita le finestre popup IntelliSense deve supportare l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> .  La visualizzazione di testo principale predefinita dell'editor include un'implementazione dell'interfaccia predefinita di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> per mantenere la funzionalità corrente di IntelliSense.  In genere, i metodi di interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> rappresentano un sottoinsieme di ciò che viene distribuito sull'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> .  Il sottoinsieme include la gestione dell'interfaccia utente di IntelliSense, la modifica di selezione e del cursore e semplice funzionalità di sostituzione del testo.  Inoltre, l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> attiva IntelliSense separato “oggetto„ e “contesto„ in modo da consentire a IntelliSense per gli oggetti che direttamente non esistono nel buffer di testo utilizzato per il contesto.  
  
#### IVsIntellisenseHost.GetHostFlags  
 Un provider dell'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> deve implementare il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost.GetHostFlags%2A> per consentire a un client di determinare il tipo di IntelliSense include i contenuti multimediali host.  
  
 I flag host, definiti in [IntelliSenseHostFlags](../extensibility/intellisensehostflags.md), vengono esposti in.  
  
|Flag di host di IntelliSense|Descrizione|  
|----------------------------------|-----------------|  
|IHF\_READONLYCONTEXT|Impostare questo flag significa che il buffer del contesto è di sola lettura e la modifica viene eseguito solo all'interno del testo tematico.|  
|IHF\_NOSEPERATESUBJECT|Impostare questo flag indica che non è presente alcun oggetto separato IntelliSense.  L'oggetto esiste nel buffer del contesto, come nel sistema tradizionale di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView> IntelliSense.|  
|IHF\_SINGLELINESUBJECT|Impostare questo flag significa che l'oggetto non è in grado di più righe, ad esempio una modifica a riga singola nella finestra di **espressione di controllo** .|  
|IHF\_FORCECOMMITTOCONTEXT|Se questo flag è impostato e il buffer del contesto deve essere aggiornato, l'host attiva il contrassegno di sola lettura nel buffer del contesto da ignorare e modifiche per continuare.|  
|IHF\_OVERTYPE|Modificare \(nell'oggetto o nel contesto\) deve essere eseguita in modalità di overtype.|  
  
#### IVsIntellisenseHost.BeforeCompletorCommit e IVsIntellisenseHost.AfterCompletorCommit  
 Questi metodi di callback vengono chiamati dalla finestra di completamento prima e dopo il testo viene eseguito il commit, per consentire l'esecuzione effettiva e la post\-elaborazione.  
  
#### IVsIntellisenseCompletor  
 L'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseCompletor> è una versione co\-generabile della finestra di completamento standard utilizzata dall'ambiente di sviluppo integrato \(IDE\).  Qualsiasi interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsIntellisenseHost> possibile distribuire rapidamente IntelliSense utilizzando questa interfaccia di completor.  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.TextManager.Interop>