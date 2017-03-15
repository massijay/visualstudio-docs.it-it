---
title: "Preparazione al debug: progetti di console | Microsoft Docs"
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
  - "applicazioni console, debug"
  - "debug [Visual Studio], applicazioni console"
  - "debug di applicazioni console"
ms.assetid: 9641f1d9-2d5a-48b1-8731-6525e8f67892
caps.latest.revision: 26
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 26
---
# Preparazione al debug: progetti di console
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La preparazione per il debug di un progetto console è simile a quella di un progetto Windows, ma è necessario tenere presente alcune ulteriori considerazioni.  Per ulteriori informazioni, vedere [Applicazioni Windows Form](../debugger/debugging-preparation-windows-forms-applications.md) e [Debugging Preparation: Windows Forms Applications \(.NET\)](http://msdn.microsoft.com/it-it/a8bc54de-41a3-464d-9a12-db9bdcbc1ad5).  A causa delle similitudini esistenti tra tutte le applicazioni console, in questo argomento vengono trattati i seguenti tipi di progetto:  
  
-   Applicazione console C\#  
  
-   Applicazione console Visual Basic  
  
-   Applicazione console C\+\+ \(.NET\)  
  
-   Applicazione console C\+\+ \(Win32\)  
  
 Potrebbe essere necessario specificare gli argomenti della riga di comando per l'applicazione console.  Per ulteriori informazioni, vedere [Impostazioni di progetto per una configurazione di debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md) [Impostazioni di progetto per una configurazione di debug Visual Basic](../debugger/project-settings-for-a-visual-basic-debug-configuration.md) o [Impostazioni di progetto per le configurazioni di debug C\#](../debugger/project-settings-for-csharp-debug-configurations.md).  
  
 Come tutte le proprietà di progetto, questi argomenti sono persistenti tra le sessioni di debug e tra le sessioni di Visual Studio.  Se in precedenza si è eseguito il debug dell'applicazione console, si tenga quindi presente che alcuni argomenti nella finestra di dialogo **Pagine delle proprietà di \<Progetto\>** potrebbero essere stati ricavati dalle sessioni precedenti.  
  
 Un'applicazione console utilizza la finestra della console per accettare l'input e visualizzare i messaggi di output.  Per scrivere nella finestra della **console**, l'applicazione deve utilizzare l'oggetto **Console** anziché l'oggetto Debug.  Per scrivere nella finestra di **output di Visual Studio**, utilizzare l'oggetto Debug come di consueto.  Assicurarsi di conoscere la posizione di scrittura dell'applicazione per evitare di cercare i messaggi nella finestra errata.  Per ulteriori informazioni, vedere [Classe Console](https://msdn.microsoft.com/en-us/library/system.console.aspx), [Classe Debug](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.aspx) e [Finestra di output](../ide/reference/output-window.md).  
  
## Avvio dell'applicazione  
 Quando vengono avviate, alcune applicazioni console vengono eseguite fino al completamento, quindi si chiudono.  Questo comportamento potrebbe non lasciare tempo sufficiente per interrompere l'esecuzione e per il debug.  Per eseguire il debug di un'applicazione, utilizzare una delle procedure riportate di seguito per avviare l'applicazione:  
  
-   L'applicazione viene avviata ed eseguita fino al raggiungimento del punto di interruzione.  
  
-   L'applicazione viene avviata e immediatamente interrotta alla prima riga di codice sorgente.  
  
-   In una finestra di codice sorgente, fare clic con il pulsante destro del mouse su una riga e scegliere **Esegui fino al cursore**.  
  
     L'applicazione viene avviata ed eseguita fino alla riga selezionata o a un punto di interruzione, se questo viene raggiunto prima della riga.  
  
 Durante il debug di un'applicazione console, può essere necessario avviare l'applicazione dal prompt dei comandi anziché da Visual Studio.  In tal caso, è possibile avviare l'applicazione dal prompt dei comandi e connettervi il debugger di Visual Studio.  Per ulteriori informazioni, vedere [Connessione a processi in esecuzione](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md).  
  
 Quando si avvia un'applicazione console da Visual Studio, la finestra della console viene visualizzata in secondo piano rispetto alla finestra di Visual Studio.  Se si tenta di avviare l'applicazione console da Visual Studio senza alcun apparente risultato, provare a spostare la finestra di Visual Studio.  
  
## Vedere anche  
 [Debug del codice nativo](../debugger/debugging-native-code.md)   
 [Debug del codice gestito](../debugger/debugging-managed-code.md)   
 [Tipi di progetto Visual C\+\+](../debugger/debugging-preparation-visual-cpp-project-types.md)   
 [Tipi di progetto C\#, F\# e Visual Basic](../debugger/debugging-preparation-csharp-f-hash-and-visual-basic-project-types.md)   
 [Impostazioni di progetto per una configurazione di debug C\+\+](../debugger/project-settings-for-a-cpp-debug-configuration.md)   
 [Sicurezza del debugger](../debugger/debugger-security.md)