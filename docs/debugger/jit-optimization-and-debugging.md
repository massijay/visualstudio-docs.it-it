---
title: "Debug e ottimizzazione JIT | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
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
  - "debug [Visual Studio], codice ottimizzato"
  - "codice ottimizzato, debug"
ms.assetid: 19bfabf3-1a2e-49dc-8819-a813982e86fd
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debug e ottimizzazione JIT
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si esegue il debug di un'applicazione gestita, per impostazione predefinita in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] viene disattivata l'ottimizzazione del codice JIT \(Just\-In\-Time\).  Viene pertanto eseguito il debug di codice non ottimizzato.  L'esecuzione di codice non ottimizzato è più lenta, ma il debug è più completo.  Il debug di codice ottimizzato è più complesso ed è consigliabile eseguirlo solo se un problema si verifica nel codice ottimizzato ma non può essere riprodotto nella versione non ottimizzata.  
  
 L'ottimizzazione JIT è controllata in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dall'opzione **Disattiva l'ottimizzazione JIT al caricamento del modulo**.  Questa opzione è disponibile nella pagina **Generale**, nodo **Debug**, della finestra di dialogo **Opzioni**.  
  
 Se si deseleziona l'opzione **Disattivare l'ottimizzazione JIT al caricamento del modulo**, è possibile eseguire il debug del codice JIT ottimizzato, ma questa operazione può risultare limitata poiché il codice ottimizzato non corrisponde al codice sorgente.  Di conseguenza, in alcune finestre del debugger, ad esempio **Variabili locali** e **Auto**, è possibile che non vengano visualizzate tutte le informazioni presenti quando si esegue il debug di codice non ottimizzato.  
  
 Un'altra differenza importante riguarda il debug con Just My Code.  Se si esegue il debug con Just My Code, il codice ottimizzato è ritenuto dal debugger codice non utente, che non deve essere visualizzato durante il debug.  Se viene eseguito il debug di codice ottimizzato JIT, pertanto, è utile disattivare Just My Code.  Per ulteriori informazioni, vedere [Limitare l'accesso a Just My Code](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).  
  
 Tenere presente che l'opzione **Disattivare l'ottimizzazione JIT al caricamento del modulo** comporta la disattivazione dell'ottimizzazione del codice durante il caricamento dei moduli.  Se ci si connette a un processo già in esecuzione, è possibile che contenga codice già caricato, compilato tramite JIT e ottimizzato.  L'opzione **Disattivare l'ottimizzazione JIT al caricamento del modulo** non influisce su tale codice, ma ha effetto sui moduli caricati dopo la connessione.  Questa opzione, inoltre, non ha effetto su moduli, ad esempio WinForms.dll, creati con NGEN.  
  
## Vedere anche  
 [Debug del codice gestito](../debugger/debugging-managed-code.md)   
 [Spostarsi nel codice con il Debugger](../debugger/navigating-through-code-with-the-debugger.md)   
 [Connessione a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md)   
 [Processo di esecuzione gestita](../Topic/Managed%20Execution%20Process.md)