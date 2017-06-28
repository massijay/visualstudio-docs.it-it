---
title: "Procedura: scrivere un visualizzatore | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "debugger, visualizzatori"
  - "visualizzatori, scrittura"
ms.assetid: 625a0d4f-abcc-43f2-9f8c-31c131a4378e
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Procedura: scrivere un visualizzatore
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile scrivere un visualizzatore personalizzato per un oggetto di qualsiasi classe gestita, ad eccezione di <xref:System.Object> o <xref:System.Array>.  
  
> [!NOTE]
>  Nelle app di **Store** sono supportati solo i visualizzatori di testo standard, HTML, XML e JSON.  Non sono supportati i visualizzatori personalizzati \(creati dall'utente\).  
  
 L'architettura di un visualizzatore del debugger è definita da due parti:  
  
-   Il *lato debugger* viene eseguito all'interno del debugger di Visual Studio.  Il codice del lato debugger crea e visualizza l'interfaccia utente del visualizzatore.  
  
-   Il *lato oggetto del debug* viene eseguito all'interno del processo sottoposto a debug in Visual Studio \(l'*oggetto del debug*\).  
  
 L'oggetto dati che si desidera visualizzare, ad esempio un oggetto stringa, esiste nel processo dell'oggetto del debug.  Di conseguenza, il lato oggetto del debug deve inviare l'oggetto dati al lato debugger, che può quindi visualizzarlo in un'interfaccia utente creata dallo sviluppatore.  
  
 Il lato debugger riceve questo oggetto dati da visualizzare da un *provider di oggetti*, che implementa l'interfaccia <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider>.  Il lato oggetto del debug invia l'oggetto dati tramite l'*origine oggetto*, che viene derivata da <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.  Il provider di oggetti può inoltre inviare nuovamente i dati all'origine oggetto consentendo in tal modo di scrivere un visualizzatore che modifica e visualizza i dati.  Il provider di oggetti può essere sottoposto a override per comunicare con l'analizzatore di espressioni e, di conseguenza, con l'origine oggetto.  
  
 L'oggetto del debug e il lato debugger comunicano tra loro tramite la classe <xref:System.IO.Stream>.  Sono disponibili metodi che consentono di serializzare un oggetto dati in un oggetto <xref:System.IO.Stream> e deserializzare l'oggetto <xref:System.IO.Stream> in un oggetto dati.  
  
 Il codice dell'oggetto del debug viene specificato tramite l'attributo DebuggerVisualizer \(<xref:System.Diagnostics.DebuggerVisualizerAttribute>\).  
  
 Per creare l'interfaccia utente del visualizzatore nel lato debugger, è necessario creare una classe che eredita da <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer> ed eseguire l'override del metodo <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> per visualizzare l'interfaccia.  
  
 È possibile usare <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> per visualizzare Windows Forms, finestre di dialogo e controlli nel visualizzatore.  
  
 Il supporto per i tipi generici è limitato.  È possibile scrivere un visualizzatore per una destinazione di tipo generico solo quest'ultimo è di tipo aperto.  Questa limitazione è identica a quella prevista quando si usa l'attributo `DebuggerTypeProxy`.  Per informazioni dettagliate, vedere [Utilizzo dell'attributo DebuggerTypeProxy](../debugger/using-debuggertypeproxy-attribute.md).  
  
 Ai visualizzatori personalizzati possono essere associate considerazioni sulla sicurezza.  Vedere [Considerazioni sulla sicurezza del visualizzatore](../debugger/visualizer-security-considerations.md).  
  
 Nelle procedure riportate di seguito vengono fornite informazioni generali sulle operazioni da effettuare per creare un visualizzatore.  Per altre informazioni, vedere [Procedura dettagliata: scrittura di un visualizzatore in C\#](../debugger/walkthrough-writing-a-visualizer-in-csharp.md).  
  
### Per creare il lato debugger  
  
1.  Usare metodi <xref:Microsoft.VisualStudio.DebuggerVisualizers.IVisualizerObjectProvider> per fornire l'oggetto visualizzato al lato debugger.  
  
2.  Creare una classe che eredita da <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>.  
  
3.  Eseguire l'override del metodo <xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer.Show%2A?displayProperty=fullName> per visualizzare l'interfaccia.  Usare i metodi <xref:Microsoft.VisualStudio.DebuggerVisualizers.IDialogVisualizerService> per visualizzare Windows Forms, finestre di dialogo e controlli all'interno dell'interfaccia.  
  
4.  Applicare <xref:System.Diagnostics.DebuggerVisualizerAttribute> per assegnare un visualizzatore \(<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>\).  
  
### Per creare il lato oggetto del debug  
  
1.  Applicare <xref:System.Diagnostics.DebuggerVisualizerAttribute> per assegnare un visualizzatore \(<xref:Microsoft.VisualStudio.DebuggerVisualizers.DialogDebuggerVisualizer>\) e un'origine oggetto \(<xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>\).  Se si omette l'origine oggetto, verrà usata un'origine predefinita.  
  
2.  Se si desidera che il visualizzatore sia in grado di modificare oggetti dati oltre a visualizzarli, eseguire l'override del metodo `TransferData` o `CreateReplacementObject` della classe <xref:Microsoft.VisualStudio.DebuggerVisualizers.VisualizerObjectSource>.  
  
## Vedere anche  
 [Visualizzatori](../debugger/create-custom-visualizers-of-data.md)   
 [Procedura: installare un visualizzatore](../debugger/how-to-install-a-visualizer.md)   
 [Procedura: testare un visualizzatore ed eseguirne il debug](../debugger/how-to-test-and-debug-a-visualizer.md)   
 [Considerazioni sulla sicurezza del visualizzatore](../debugger/visualizer-security-considerations.md)