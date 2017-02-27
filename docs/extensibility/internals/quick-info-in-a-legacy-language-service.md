---
title: "Informazioni rapide in un servizio di linguaggio Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Informazioni rapide, supporto in servizi di linguaggio [framework pacchetto gestito]"
  - "IntelliSense, informazioni rapide"
  - "servizi di linguaggio [framework gestito pacchetto], informazioni rapide di IntelliSense"
ms.assetid: 159ccb0b-f5d6-4912-b88b-e9612924ed5e
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Informazioni rapide in un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Informazioni rapide di IntelliSense vengono visualizzate informazioni su un identificatore dell'origine quando l'utente posiziona il punto di inserimento dell'identificatore e seleziona **informazioni rapide** dal **IntelliSense** menu o contiene il cursore del mouse sull'identificatore. In questo modo vengono visualizzati con informazioni sull'identificatore di una descrizione comando. Tali informazioni comprendono in genere il tipo di identificatore. Quando il motore di debug è attivo, le informazioni potrebbero includere il valore corrente. Il motore di debug fornisce i valori dell'espressione, mentre il servizio di linguaggio gestisce solo identificatori.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un package VS, ma il modo più recente per implementare le funzionalità del servizio del linguaggio è l'utilizzo delle estensioni MEF. Per ulteriori informazioni, vedere [Procedura dettagliata: Visualizzazione delle descrizioni comandi informazioni rapide](../Topic/Walkthrough:%20Displaying%20QuickInfo%20Tooltips.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a utilizzare il nuovo editor API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
 Le classi del servizio gestito pacchetto language framework \(MPF\) forniscono il supporto completo per visualizzare la descrizione comando informazioni rapide di IntelliSense. È necessario effettuare è fornire il testo per visualizzare e abilitare la funzionalità informazioni rapide.  
  
 Il testo da visualizzare viene ottenuto chiamando il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> parser di metodo con un valore di motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason>. Questo motivo indica al parser di ottenere le informazioni sul tipo \(o le informazioni appropriate da visualizzare nella descrizione comando informazioni rapide\) per l'identificatore nella posizione specificata nel <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto. Il <xref:Microsoft.VisualStudio.Package.ParseRequest> oggetto è ciò che è stato passato per il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> \(metodo\).  
  
 Il parser deve analizzare tutto fino alla posizione nel <xref:Microsoft.VisualStudio.Package.ParseRequest> per determinare i tipi di tutti gli identificatori di oggetto. Il parser deve quindi ottenere l'identificatore in corrispondenza della posizione di richiesta di analisi. Infine, il parser deve passare i dati di suggerimento strumento associati a tale identificatore per il <xref:Microsoft.VisualStudio.Package.AuthoringScope> dell'oggetto in modo che tale oggetto può restituire il testo dal <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> metodo.  
  
## Abilitare la funzionalità informazioni rapide  
 Per abilitare la funzionalità informazioni rapide, è necessario impostare il `CodeSense` e `QuickInfo` di parametri denominati di <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute>. Impostare questi attributi di <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> e <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableQuickInfo%2A> proprietà.  
  
## Implementa la funzionalità informazioni rapide  
 La <xref:Microsoft.VisualStudio.Package.ViewFilter> classe gestisce l'operazione di informazioni rapide di IntelliSense. Quando la <xref:Microsoft.VisualStudio.Package.ViewFilter> classe riceve il <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando, la classe chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo con il motivo analisi <xref:Microsoft.VisualStudio.Package.ParseReason> e il percorso del punto di inserimento al momento il <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando è stato inviato. Il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> metodo parser deve quindi analizzare l'origine nella posizione specificata e quindi analizzare l'identificatore nella posizione specificata per determinare quali elementi visualizzare nella descrizione comando informazioni rapide.  
  
 La maggior parte dei parser eseguire un'analisi iniziale dell'intero file di origine e archiviare i risultati in un albero di analisi. L'analisi completa viene effettuata quando <xref:Microsoft.VisualStudio.Package.ParseReason> viene passato a <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> \(metodo\). Altri tipi di analisi possono quindi utilizzare l'albero di analisi per ottenere le informazioni desiderate.  
  
 Ad esempio, il valore di motivo di analisi di <xref:Microsoft.VisualStudio.Package.ParseReason> possibile trovare l'identificatore nel percorso di origine e cercare nell'albero di analisi per ottenere le informazioni sul tipo. Questo tipo di informazioni viene quindi passato alla <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe e viene restituito per il <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDataTipText%2A> \(metodo\).