---
title: "Linguaggio legacy servizio Features1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servizi di linguaggio [framework pacchetto gestito]"
ms.assetid: a646e4f0-767d-4cd1-8e1a-9a2aa210a1b7
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Funzionalit&#224; del linguaggio legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un servizio di linguaggio gestito del framework \(MPF\) del pacchetto può supportare uno o più funzionalità di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , come evidenziazione della sintassi, IntelliSense e la convalida del punto di interruzione.  Ogni funzionalità può essere indipendente implementato dagli altri ma richiedono un parser e lo scanner fatta eccezione per l'evidenziazione della sintassi, che richiede solo uno analisi.  
  
## In questa sezione  
 [Corrispondenza di parentesi in un servizio di linguaggio Legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
 Descrive ciò che è necessario supportare la corrispondenza di una coppia di lingua, nota anche come la corrispondenza di parentesi graffe.  
  
 [Commenti di codice in un servizio di linguaggio Legacy](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
 Descrive ciò che è necessario supportare il commento e rimuovere il commento del codice selezionato.  
  
 [Proprietà personalizzate dei documenti in un servizio di linguaggio Legacy](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
 Descrive ciò che è necessario supportare le proprietà del documento incorporate in un file di origine.  
  
 [La struttura in un servizio di linguaggio Legacy](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
 Descrive ciò che è necessario supportare la struttura mediante l'implementazione delle aree nascoste.  
  
 [La formattazione di codice in un servizio di linguaggio Legacy](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
 Descrive ciò che è necessario supportare la formattazione del codice.  
  
 [Supporto per i frammenti di codice in un servizio di linguaggio Legacy](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
 Descrive ciò che è necessario supportare i frammenti di codice, ovvero segmenti di codice che sono memorizzati e possono essere modificati.  
  
 [Informazioni sui parametri in un servizio di linguaggio Legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
 Descrive ciò che è necessario supportare l'operazione di informazioni parametri di IntelliSense per visualizzare la firma del metodo quando il metodo viene digitato.  
  
 [Informazioni rapide in un servizio di linguaggio Legacy](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
 Descrive ciò che è necessario supportare l'operazione di informazioni rapide di IntelliSense per visualizzare informazioni su un identificatore.  
  
 [Completamento di membro in un servizio di linguaggio Legacy](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
 Descrive ciò che è necessario supportare l'operazione di completamento dei membri di IntelliSense per selezionare un membro di uno spazio dei nomi da un elenco.  
  
 [Completamento delle parole in un servizio di linguaggio Legacy](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
 Descrive ciò che è necessario supportare il completamento di IntelliSense Word per il completamento delle parole parzialmente tipizzate.  
  
 [Supporto per la finestra Auto in un servizio di linguaggio Legacy](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
 Viene descritto il servizio di linguaggio possibile eseguire per supportare la finestra di **automobili** durante il debug.  
  
 [Supporto per la barra di spostamento in un servizio di linguaggio Legacy](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
 Viene descritto come utilizzare **barra di navigazione** alla parte superiore della visualizzazione utilizzata per fornire la navigazione rapida a qualsiasi tipo o un membro nel file indicato in tale visualizzazione.  
  
 [Colorazione della sintassi in un servizio di linguaggio Legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
 Descrive ciò che è necessario supportare evidenziazione della sintassi del codice sorgente.  
  
 [Convalida i punti di interruzione in un servizio di linguaggio Legacy](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
 Viene descritto il servizio di linguaggio possibile eseguire per supportare convalidare i punti di interruzione all'esterno del debugger.  
  
## Sezioni correlate  
 [Scanner e Parser servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-parser-and-scanner.md)  
 Viene descritto il parser e lo scanner che sono obbligatori implementare tutte le funzionalità di un servizio di linguaggio che utilizza il framework gestito del pacchetto.  
  
 [Implementazione di un servizio di linguaggio](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
 Descrive ciò che è necessario implementare un servizio di linguaggio tramite il MPF.  
  
 [Registrazione di un servizio di linguaggio](../../extensibility/internals/registering-a-legacy-language-service1.md)  
 Vengono descritti i passaggi che sono obbligatori registrare un servizio di linguaggio basato MPF con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
 [Utilizzo di IntelliSense](../../ide/using-intellisense.md)  
 Viene illustrato come IntelliSense semplifica i riferimenti del linguaggio di facile accesso.  
  
 [Implementazione di un servizio di linguaggio Legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)  
 Vengono fornite informazioni su come utilizzare il framework gestito del pacchetto \(MPF\) per implementare un servizio di linguaggio completo nel codice gestito.