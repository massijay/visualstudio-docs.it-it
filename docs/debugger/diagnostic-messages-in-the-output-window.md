---
title: "Messaggi diagnostici nella finestra di output | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.output"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debug (classe)"
  - "Debug.Print (sostituzioni)"
  - "debugger, Output (finestra)"
  - "debug [Visual Studio], messaggi di diagnostica nella finestra di output"
  - "diagnosi"
  - "messaggi di diagnostica [C#]"
  - "diagnostica"
  - "messaggi, diagnostici"
  - "Output (finestra), messaggi di diagnostica"
  - "System.Diagnostics.Debug (classe), Output (finestra)"
  - "System.Diagnostics.Trace (classe), Output (finestra)"
  - "Trace (classe), messaggi di diagnostica"
ms.assetid: 386e9524-be17-4573-83fb-4f7c5cae0be0
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Messaggi diagnostici nella finestra di output
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile scrivere messaggi di runtime nella finestra di output utilizzando la classe Debug o la classe Trace, che fanno entrambe parte della libreria di classi <xref:System.Diagnostics>.  Utilizzare la classe Debug se si desidera generare l'output solo nella versione di debug del programma  e la classe Trace se si desidera generare l'output sia nella versione di debug che in quella di rilascio del programma.  
  
## Metodi di output  
 Le classi <xref:System.Diagnostics.Trace> e <xref:System.Diagnostics.Debug> forniscono i seguenti metodi di output:  
  
-   Diversi metodi `Write`, che generano informazioni senza interrompere l'esecuzione.  Questi metodi sostituiscono il metodo `Debug.Print` utilizzato nelle versioni precedenti di Visual Basic.  
  
-   I metodi <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=fullName> and <xref:System.Diagnostics.Trace.Assert%2A?displayProperty=fullName>, che interrompono l'esecuzione e generano informazioni se si verifica un errore relativo a una condizione specificata.  Per impostazione predefinita, il metodo `Assert` visualizza le informazioni in una finestra di dialogo.  Per ulteriori informazioni, vedere [Asserzioni nel metodo gestito](../debugger/assertions-in-managed-code.md).  
  
-   I metodi <xref:System.Diagnostics.Debug.Fail%2A?displayProperty=fullName> and <xref:System.Diagnostics.Trace.Fail%2A?displayProperty=fullName>, che interrompono sempre l'esecuzione e generano informazioni.  Per impostazione predefinita, i metodi `Fail` visualizzano le informazioni in una finestra di dialogo.  
  
 Oltre all'output del programma, nella finestra di output possono essere visualizzate informazioni riguardanti:  
  
-   I moduli caricati o scaricati dal debugger.  
  
-   Le eccezioni generate.  
  
-   I processi chiusi.  
  
-   I thread chiusi.  
  
## Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Finestra di output](../ide/reference/output-window.md)   
 [Tracing and Instrumenting Applications](../Topic/Tracing%20and%20Instrumenting%20Applications.md)   
 [Introduction to Instrumentation and Tracing](http://msdn.microsoft.com/it-it/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)   
 [Tipi di progetto C\#, F\# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Debug del codice gestito](../debugger/debugging-managed-code.md)