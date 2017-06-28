---
title: "Debug e processo di hosting | Microsoft Docs"
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
helpviewer_keywords: 
  - "debug [Visual Studio], processo di hosting"
  - "processo di hosting"
ms.assetid: d0f0b9a6-2a6e-463d-b6ea-9518ee727933
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Debug e processo di hosting
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il processo di hosting di Visual Studio migliora le prestazioni del debugger e offre ulteriori funzionalità, ad esempio il debug in contesti di attendibilità parziale e la valutazione delle espressioni per la fase di progettazione. Se necessario, è possibile disabilitare il processo di hosting. Per altre informazioni, vedere [Procedura: disabilitare il processo di hosting](../ide/how-to-disable-the-hosting-process.md). Nelle sezioni riportate di seguito vengono descritte alcune differenze tra l'esecuzione del debug con e senza processo di hosting.  
  
## Debug in contesti di attendibilità parziale e sicurezza ClickOnce  
 Il debug in contesti di attendibilità parziale richiede il processo di hosting. Se il processo di hosting viene disabilitato, questo tipo di debug non potrà funzionare anche se la sicurezza con attendibilità parziale è attivata nella pagina **Sicurezza** di **Proprietà progetto**. Per altre informazioni, vedere [Procedura: disabilitare il processo di hosting](../ide/how-to-disable-the-hosting-process.md) e [Procedura: eseguire il debug di un'applicazione parzialmente attendibile](../debugger/how-to-debug-a-partial-trust-application.md).  
  
## Valutazione delle espressioni per la fase di progettazione  
 Le espressioni per la fase di progettazione usano sempre il processo di hosting. La disattivazione del processo di hosting in **Proprietà progetto** comporta la disattivazione della valutazione delle espressioni per la fase di progettazione per i progetti Libreria di classi. Per altri tipi di progetto la valutazione delle espressioni per la fase di progettazione non viene disabilitata. In Visual Studio viene invece avviato l'eseguibile usato per la valutazione per la fase di progettazione senza il processo di hosting. Questa differenza potrebbe produrre risultati diversi.  
  
## Differenze in AppDomain.CurrentDomain.FriendlyName  
 Nell'oggetto `AppDomain.CurrentDomain.FriendlyName` vengono restituiti risultati diversi a seconda che il processo di hosting sia attivato o meno. Se si chiama `AppDomain.CurrentDomain.FriendlyName` con il processo di hosting abilitato, viene restituito *nome\_app*`.vhost.exe`. Se lo si chiama con il processo di hosting disabilitato, viene restituito *nome\_app*`.exe`.  
  
## Differenze in Assembly.GetCallingAssembly\(\).FullName  
 Nell'oggetto `Assembly.GetCallingAssembly().FullName` vengono restituiti risultati diversi a seconda che il processo di hosting sia attivato o meno. Se si chiama `Assembly.GetCallingAssembly().FullName` con il processo di hosting abilitato, viene restituito `mscorlib`. Se l'oggetto `Assembly.GetCallingAssembly().FullName` viene chiamato con il processo di hosting disabilitato, viene restituito il nome dell'applicazione.  
  
## Vedere anche  
 [Processo di hosting \(vshost.exe\)](../ide/hosting-process-vshost-exe.md)   
 [Procedura: eseguire il debug di un'applicazione parzialmente attendibile](../debugger/how-to-debug-a-partial-trust-application.md)   
 [Procedura: disabilitare il processo di hosting](../ide/how-to-disable-the-hosting-process.md)