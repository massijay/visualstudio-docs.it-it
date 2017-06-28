---
title: "Debug delle applicazioni in modalit&#224; mista | Microsoft Docs"
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
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Stack di chiamate (finestra)"
  - "Stack di chiamate (finestra), debug in modalità mista"
  - "debug [Visual Studio], modalità mista"
  - "debug di codice gestito, codice misto"
  - "debug in modalità mista"
  - "debug in modalità mista, stack di chiamate"
  - "debug in modalità mista, valutazione di proprietà"
ms.assetid: 60e34477-ae4e-48c7-9093-3e37f72e1bc3
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Debug delle applicazioni in modalit&#224; mista
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un'applicazione in modalità mista combina codice nativo \(C\+\+\) con codice gestito, ad esempio Visual Basic, Visual C\# o C\+\+ eseguito in Common Language Runtime.  Il debug di applicazioni in modalità mista è ampiamente trasparente in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e non è molto diverso dal debug di un'applicazione in modalità singola.  È tuttavia necessario fare alcune considerazioni specifiche.  
  
## Abilitare la funzione di modifica e continuazione di C\+\+ nel debug in modalità mista  
  
-   Per utilizzare Modifica e continuazione per C\+\+ in Visual Studio 2013, è necessario ripristinare il motore di debug legacy.  Vedere [Passaggio alla modalità di compatibilità gestita in Visual Studio 2013](http://blogs.msdn.com/b/visualstudioalm/archive/2013/10/16/switching-to-managed-compatibility-mode-in-visual-studio-2013.aspx) nel blog Microsoft Application Lifecycle Management.  
  
## Valutazione delle proprietà nelle applicazioni in modalità mista  
 In un'applicazione in modalità mista la valutazione delle proprietà tramite il debugger è un'operazione complessa.  Di conseguenza, alcune operazioni di debug, ad esempio il debug passo a passo, possono risultare lente.  Per ulteriori informazioni, vedere [Esecuzione di un'istruzione del codice alla volta](http://msdn.microsoft.com/it-it/8791dac9-64d1-4bb9-b59e-8d59af1833f9).  Se nel debug in modalità mista le prestazioni non risultano soddisfacenti, disattivare la valutazione delle proprietà nelle finestre del debugger.  
  
> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere **Importa\/Esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
#### Per disattivare la valutazione delle proprietà  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nella finestra di dialogo **Opzioni** aprire la cartella **Debug** e selezionare la categoria **Generale**.  
  
3.  Deselezionare la casella di controllo **Attiva valutazione delle proprietà e altre chiamate di funzioni implicite**.  
  
 Poiché gli stack di chiamate native sono diversi dagli stack di chiamate gestite, il debugger non può sempre fornire lo stack di chiamate completate per il codice misto.  Quando il codice nativo chiama il codice gestito, possono essere presenti alcune differenze.  Per ulteriori informazioni, vedere [Codice misto e informazioni mancanti nella finestra Stack di chiamate](../debugger/mixed-code-and-missing-information-in-the-call-stack-window.md).  
  
## Vedere anche  
 [Debug del codice gestito](../debugger/debugging-managed-code.md)