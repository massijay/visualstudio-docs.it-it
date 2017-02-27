---
title: "Interfacce di servizio di linguaggio legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaccia IVsLanguageInfo"
  - "servizi di linguaggio, oggetti"
ms.assetid: 03b2d507-f463-417e-bc22-bdac68eeda52
caps.latest.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 24
---
# Interfacce di servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Per qualsiasi linguaggio di programmazione particolare, può esistere un'unica istanza di un servizio di linguaggio per volta.  Tuttavia, un singolo servizio di linguaggio possibile utilizzare più di un editor.  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] non viene associato un servizio di linguaggio ad alcun editor particolare.  Di conseguenza, quando si chiama un'operazione del servizio di linguaggio, è necessario identificareeditor appropriato come parametro.  
  
## Interfacce comuni relative ai servizi di linguaggio  
 L'editor ottiene il servizio di linguaggio chiamando <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A> nel package VS appropriato.  Il servizio l'ID \(SID\) passato nella chiamata identifica il servizio di linguaggio richiesto.  
  
 È possibile implementare interfacce principali del servizio di linguaggio su qualsiasi numero di classi separate.  Tuttavia, un approccio più comune consiste nell'implementazione delle interfacce seguenti in una singola classe:  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageDebugInfo>  
  
-   <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageBlock> \(facoltativo\)  
  
 L'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> deve essere distribuita in tutti i servizi di linguaggio.  Vengono fornite informazioni sul servizio di linguaggio, ad esempio il nome localizzato del linguaggio, le estensioni di file associato al servizio di linguaggio e come recuperare un colorizer.  
  
## Interfacce aggiuntive del servizio di linguaggio  
 Altre interfacce possono essere forniti del servizio di linguaggio.  [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] richiede un'istanza separata di queste interfacce per ogni istanza del buffer di testo.  Pertanto, è necessario implementare ciascuna di queste interfacce nel relativo oggetto.  Nella tabella seguente sono elencate le interfacce che richiedono un'istanza per istanza del buffer di testo.  
  
|Interfaccia|Descrizione|  
|-----------------|-----------------|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager>|Gestisce le aree di controllo della finestra del codice, come la barra a discesa.  È possibile ottenere questa interfaccia tramite il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetCodeWindowManager%2A> .  Esiste un <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCodeWindowManager> per finestra del codice.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>|Colore delle parole chiave e i delimitatori del linguaggio.  È possibile ottenere questa interfaccia tramite il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo.GetColorizer%2A> .  <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> viene chiamato in fase di disegno.  Evitare lavoro calcolo\-intensivo in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> o le prestazioni potrebbero che.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData>|Fornisce le descrizioni comandi di parametro di IntelliSense.  Quando il servizio di linguaggio riconosce un carattere che indica che i dati del metodo deve essere visualizzato, ad esempio una parentesi di apertura, chiama il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodTipWindow.SetMethodData%2A> per notificare alla visualizzazione di testo che il servizio di linguaggio è pronto per visualizzare una descrizione comando di informazioni sul parametro.  Le chiamate della visualizzazione di testo quindi nuovamente al servizio di linguaggio tramite i metodi di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsMethodData> interfaccia per ottenere le informazioni necessarie per visualizzare la descrizione comando.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet>|Consente il completamento di istruzioni in IntelliSense.  Quando il servizio di linguaggio è pronto per visualizzare un elenco di completamento, chiama il metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.UpdateCompletionStatus%2A> nella visualizzazione di testo.  Le chiamate della visualizzazione di testo quindi nuovamente al servizio di linguaggio utilizzare i metodi in <xref:Microsoft.VisualStudio.TextManager.Interop.IVsCompletionSet> oggetto.|  
|<xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter>|Consente la modifica della visualizzazione di testo utilizzando il gestore comando.  La classe in cui si implementa l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> necessario implementare anche l'interfaccia di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  La visualizzazione di testo recupera l'oggetto di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> eseguire una query l'oggetto di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> passato al metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A> .  Deve essere un oggetto di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextViewFilter> per ogni visualizzazione.|  
|<xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>|Rileva i controlli i tipi di utenti nella finestra del codice.  Monitorare l'output dall'implementazione di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> per fornire informazioni di completamento personalizzate e visualizzare la modifica<br /><br /> Per passare l'oggetto di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> la visualizzazione di testo, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextView.AddCommandFilter%2A>di chiamata.|  
  
## Vedere anche  
 [Lo sviluppo di un servizio di linguaggio](../../extensibility/internals/developing-a-legacy-language-service.md)   
 [Elenco di controllo: Creazione di un servizio di linguaggio Legacy](../../extensibility/internals/checklist-creating-a-legacy-language-service.md)