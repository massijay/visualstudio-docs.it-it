---
title: "Completamento delle parole in un servizio di linguaggio Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servizi di linguaggio [framework gestito pacchetto], completa parola di IntelliSense"
  - "IntelliSense, completa parola"
  - "Completa parola"
ms.assetid: 0ace5ac3-f9e1-4e6d-add4-42967b1f96a6
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Completamento delle parole in un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Completa parola inserisce i caratteri mancanti su una parola parziale digitata. Se è presente un solo termine possibili, la parola viene completata quando viene immesso il carattere di completamento. Se la parola parziale corrisponde più possibilità, viene visualizzato un elenco di possibili completamenti. Un carattere di completamento può essere qualsiasi carattere che non viene utilizzato per gli identificatori.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un package VS, ma il modo più recente per implementare le funzionalità del servizio del linguaggio è l'utilizzo delle estensioni MEF. Per ulteriori informazioni, vedere [Estensione dell'Editor e servizi di linguaggio](../../extensibility/extending-the-editor-and-language-services.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a utilizzare il nuovo editor API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## Passaggi di implementazione  
  
1.  Quando l'utente seleziona **Completa parola** dal **IntelliSense** dal menu di <xref:Microsoft.VisualStudio.VSConstants.VSStd2KCmdID> comando viene inviato al servizio di linguaggio.  
  
2.  La <xref:Microsoft.VisualStudio.Package.ViewFilter> classe intercetta le chiamate di <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo con il motivo analisi <xref:Microsoft.VisualStudio.Package.ParseReason>.  
  
3.  La <xref:Microsoft.VisualStudio.Package.Source> classe quindi chiama il <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> per ottenere l'elenco dei completamenti possibili e quindi Visualizza le parole in una descrizione comando elenco tramite la <xref:Microsoft.VisualStudio.Package.CompletionSet> classe.  
  
     Se è presente una sola parola corrispondente, la <xref:Microsoft.VisualStudio.Package.Source> classe completa parola.  
  
 In alternativa, se lo scanner restituisce il valore trigger <xref:Microsoft.VisualStudio.Package.TokenTriggers> quando viene inserito il primo carattere di un identificatore, la <xref:Microsoft.VisualStudio.Package.Source> classe rileva tale situazione e chiama il <xref:Microsoft.VisualStudio.Package.Source.Completion%2A> metodo con il motivo analisi <xref:Microsoft.VisualStudio.Package.ParseReason>. In questo caso il parser deve rilevare la presenza di un carattere di selezione membro e fornire un elenco di membri.  
  
## Abilita il supporto per la parola completa  
 Per abilitare il supporto per set di completamenti di word il `CodeSense` passato al parametro denominato il <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute> attributo utente associato al pacchetto di linguaggio. Consente di impostare il <xref:Microsoft.VisualStudio.Package.LanguagePreferences.EnableCodeSense%2A> proprietà la <xref:Microsoft.VisualStudio.Package.LanguagePreferences> classe.  
  
 Il parser deve restituire un elenco di dichiarazioni in risposta al valore di motivo analisi <xref:Microsoft.VisualStudio.Package.ParseReason>, per il completamento delle parole per il funzionamento.  
  
## Implementazione completa parola nel metodo ParseSource  
 Per il completamento delle parole, la <xref:Microsoft.VisualStudio.Package.Source> classe chiama il <xref:Microsoft.VisualStudio.Package.AuthoringScope.GetDeclarations%2A> metodo la <xref:Microsoft.VisualStudio.Package.AuthoringScope> classe per ottenere un elenco di possibili corrispondenze. È necessario implementare l'elenco in una classe che deriva dalla <xref:Microsoft.VisualStudio.Package.Declarations> classe. Vedere la <xref:Microsoft.VisualStudio.Package.Declarations> classe per informazioni dettagliate sui metodi è necessario implementare.  
  
 Se l'elenco contiene solo una singola parola, la <xref:Microsoft.VisualStudio.Package.Source> classe inserisce automaticamente tale parola anziché la parola parziale. Se l'elenco contiene più parole, la <xref:Microsoft.VisualStudio.Package.Source> classe visualizza un elenco di suggerimenti strumento da cui l'utente può selezionare l'opzione desiderata.  
  
 Inoltre esaminare l'esempio di un <xref:Microsoft.VisualStudio.Package.Declarations> implementazione della classe in [Completamento di membro in un servizio di linguaggio Legacy](../../extensibility/internals/member-completion-in-a-legacy-language-service.md).