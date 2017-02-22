---
title: "Cenni preliminari sul servizio di linguaggio legacy | Microsoft Docs"
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
  - "servizi di linguaggio [framework gestito pacchetto], informazioni sui servizi di linguaggio"
ms.assetid: bb44e27b-d228-463c-b2cf-cd5c24c7c1b5
caps.latest.revision: 17
caps.handback.revision: 17
ms.author: "gregvanl"
manager: "ghogen"
---
# Cenni preliminari sul servizio di linguaggio legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Un servizio di linguaggio fornisce il supporto dell'editor che consente di implementare determinate funzionalità di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .  Le classi gestite del servizio \(MPF\) di linguaggio del Framework del pacchetto forniscono un supporto completo per le funzionalità frequente\-utilizzate e il supporto parziale alle altre funzionalità.  
  
## Funzionalità completamente supportate nel MPF  
 Le classi del servizio di linguaggio di MPF supportano le funzionalità seguenti:  
  
-   Evidenziazione della sintassi  
  
-   Struttura  
  
-   Blocchi di commenti di codice  
  
-   Brace matching  
  
-   Frammenti di codice  
  
-   Proprietà personalizzate del documento  
  
-   Informazioni sui parametri di IntelliSense  
  
-   informazioni rapide di IntelliSense  
  
-   Completamento dei membri di IntelliSense  
  
-   Completamento delle parole di IntelliSense  
  
## Funzionalità parzialmente supportate nel MPF  
 Il MPF fornisce supporto solo parzialmente per le seguenti funzionalità.  Ciò significa che è necessario implementare i metodi chiamati da MPF.  
  
-   Formattazione del codice.  L'utente fornisce il codice che implementa il formattazione.  
  
-   Convalidando i punti di interruzione identificare gli intervalli valide di codice.  L'utente fornisce il codice che identifica gli intervalli di codice.  
  
-   Supporta la finestra di **automobili** del debugger per la visualizzazione delle variabili.  L'utente fornisce il codice che determina quali visualizzare nella finestra.  
  
-   Supporto del **barra di navigazione** per la navigazione rapida tra i tipi e i membri.  Implementate e restituiscono una classe di supporto che popola gli elenchi nelle caselle combinate di **barra di navigazione** .  
  
## Implementazione  
 È necessario completare i passaggi per implementare il servizio di linguaggio stesso e le funzionalità del servizio di linguaggio che si desidera supporto del linguaggio.  Questi passaggi vengono trattati i seguenti argomenti:  
  
-   [Implementazione di un servizio di linguaggio](../../extensibility/internals/implementing-a-legacy-language-service2.md)  
  
-   [Registrazione di un servizio di linguaggio](../../extensibility/internals/registering-a-legacy-language-service1.md)  
  
-   [Colorazione della sintassi in un servizio di linguaggio Legacy](../../extensibility/internals/syntax-colorizing-in-a-legacy-language-service.md)  
  
-   [Corrispondenza di parentesi in un servizio di linguaggio Legacy](../../extensibility/internals/brace-matching-in-a-legacy-language-service.md)  
  
-   [La struttura in un servizio di linguaggio Legacy](../../extensibility/internals/outlining-in-a-legacy-language-service.md)  
  
-   [Commenti di codice in un servizio di linguaggio Legacy](../../extensibility/internals/commenting-code-in-a-legacy-language-service.md)  
  
-   [La formattazione di codice in un servizio di linguaggio Legacy](../../extensibility/internals/reformatting-code-in-a-legacy-language-service.md)  
  
-   [Proprietà personalizzate dei documenti in un servizio di linguaggio Legacy](../../extensibility/internals/custom-document-properties-in-a-legacy-language-service.md)  
  
-   [Supporto per i frammenti di codice in un servizio di linguaggio Legacy](../../extensibility/internals/support-for-code-snippets-in-a-legacy-language-service.md)  
  
-   [Supporto per la barra di spostamento in un servizio di linguaggio Legacy](../../extensibility/internals/support-for-the-navigation-bar-in-a-legacy-language-service.md)  
  
-   [Completamento delle parole in un servizio di linguaggio Legacy](../../extensibility/internals/word-completion-in-a-legacy-language-service.md)  
  
-   [Completamento di membro in un servizio di linguaggio Legacy](../../extensibility/internals/member-completion-in-a-legacy-language-service.md)  
  
-   [Informazioni sui parametri in un servizio di linguaggio Legacy](../../extensibility/internals/parameter-info-in-a-legacy-language-service2.md)  
  
-   [Informazioni rapide in un servizio di linguaggio Legacy](../../extensibility/internals/quick-info-in-a-legacy-language-service.md)  
  
-   [Supporto per la finestra Auto in un servizio di linguaggio Legacy](../../extensibility/internals/support-for-the-autos-window-in-a-legacy-language-service.md)  
  
-   [Convalida i punti di interruzione in un servizio di linguaggio Legacy](../../extensibility/internals/validating-breakpoints-in-a-legacy-language-service.md)  
  
## Vedere anche  
 [Implementazione di un servizio di linguaggio Legacy](../../extensibility/internals/implementing-a-legacy-language-service1.md)   
 [Estensibilità del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-extensibility.md)