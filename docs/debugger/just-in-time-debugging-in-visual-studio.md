---
title: "Debug JIT in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "CSharp"
  - "VB"
helpviewer_keywords: 
  - "debug [Visual Studio], JIT"
  - "debug JIT"
ms.assetid: 14972d5f-69bc-479b-9529-03b8787b118f
caps.latest.revision: 48
caps.handback.revision: 40
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debug JIT in Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il debug JIT avvia Visual Studio automaticamente quando si verifica un'eccezione o un arresto anomalo in un'applicazione in esecuzione all'esterno di Visual Studio.  In questo modo è possibile testare l'applicazione quando Visual Studio non è in esecuzione e avviare il debug con Visual Studio quando si verifica un problema.  
  
 Il debug JIT non è supportato dalle app Windows Store.  Il debug JIT non può essere usato con codice gestito ospitato in un'applicazione nativa, ad esempio visualizzatori.  
  
## Utilizzo del debug JIT  
 Quando si installa Visual Studio, il debug JIT è abilitato per impostazione predefinita.  Se è necessario disabilitare o riabilitare il debug JIT, vedere [Limitare l'accesso a Just My Code](../debugger/navigating-through-code-with-the-debugger.md#BKMK_Restrict_stepping_to_Just_My_Code).  
  
 Quando il debug JIT è abilitato, è possibile testare l'applicazione all'esterno di Visual Studio.  Quando si verifica un arresto anomalo o un'eccezione, verrà visualizzata una finestra di dialogo con un messaggio simile al seguente:  
  
 Eccezione non gestita \('System.TypeInitializationException'\) in terrarium.exe\[3384\]  
  
 Quando viene visualizzata questa finestra di dialogo, è possibile avviare il debug con la procedura seguente.  
  
#### Per avviare il debug JIT quando si verifica un errore  
  
1.  Nell'elenco **Debugger disponibili** della finestra di dialogo Debug JIT fare clic su **Nuova istanza di Visual Studio 2015** oppure fare clic su un'istanza di Visual Studio già in esecuzione.  
  
2.  Per usare automaticamente Visual Studio per tutti gli arresti anomali futuri, fare clic su **Imposta il debugger selezionato come predefinito**.  
  
3.  Se si desidera scegliere i tipi di codice di cui eseguire il debug, selezionare la casella di controllo **Scegli manualmente i moduli di gestione di debug**.  Se non si seleziona questa opzione, verranno automaticamente selezionati i motori di debug appropriati per il tipo di codice nel programma.  
  
4.  Fare clic su **OK**.  
  
5.  Se l'applicazione contiene un assembly con codice non attendibile, viene visualizzata una finestra di dialogo contenente un avviso di sicurezza.  Questa finestra di dialogo consente di decidere se procedere o meno con il debug.  Prima di continuare con il debug, decidere se ritenere attendibile o meno il codice.  Se il codice è stato scritto da altri,  decidere se ritenere attendibile o meno l'autore.  Se l'applicazione è in esecuzione in un computer remoto, assicurarsi di riconoscere il nome del processo.  Anche se l'applicazione è in esecuzione in un computer locale, non significa che possa essere ritenuta attendibile.  È infatti possibile che in Internet Explorer sia in esecuzione un controllo ActiveX dannoso.  Considerare la possibilità che tale codice dannoso sia in esecuzione nel proprio computer.  Se si stabilisce che il codice di cui si intende eseguire il debug è attendibile, fare clic su **Debug**.  In caso contrario, fare clic su **Non eseguire il debug**.  
  
##  <a name="BKMK_Enabling"></a> Abilitazione o disabilitazione del debug Just\-In\-Time  
 È possibile abilitare o disabilitare il debug JIT dalla finestra di dialogo **Opzioni**.  
  
#### Per abilitare o disabilitare il debug JIT  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nella finestra di dialogo **Opzioni** selezionare la cartella **Debug**.  
  
3.  Nella cartella **Debug** scegliere la pagina **JIT**.  
  
4.  Nella casella **Attiva debug JIT per questi tipi di codice** selezionare o deselezionare i tipi di programma relativi: **Gestito**, **Nativo** o **Script**.  
  
     Per disabilitare il debug JIT, è necessario disporre dei privilegi di amministratore.  L'attivazione del debug JIT richiede la modifica di una chiave del Registro di sistema e per eseguire tale operazione sono necessari i privilegi di amministratore.  
  
5.  Fare clic su **OK**.  
  
 Per impostazione predefinita, le applicazioni Windows Form dispongono di un gestore eccezioni di livello superiore che consente al programma di proseguire l'esecuzione quando è possibile un ripristino.  Di conseguenza, è necessario effettuare i passaggi aggiuntivi seguenti per abilitare il debug JIT di un'applicazione Windows Form.  
  
#### Per attivare il debug JIT di Windows Form  
  
1.  Impostare il valore `jitDebugging` su `true` nella sezione `system.windows.form` del file machine.config o del file *application*.exe.config:  
  
    ```  
    <configuration>  
        <system.windows.forms jitDebugging="true" />  
    </configuration>  
    ```  
  
2.  In un'applicazione Windows Form C\+\+ è anche necessario impostare `DebuggableAttribute` in un file con estensione config o nel codice.  Se si esegue la compilazione con [\/Zi](/visual-cpp/build/reference/z7-zi-zi-debug-information-format) e senza [\/Og](/visual-cpp/build/reference/og-global-optimizations), il compilatore imposta automaticamente questo attributo.  Se si desidera eseguire il debug di una build di rilascio non ottimizzata, tuttavia, è necessario procedere alla configurazione.  A tale scopo, è possibile aggiungere la riga seguente al file AssemblyInfo.cpp dell'applicazione:  
  
    ```  
    [assembly:System::Diagnostics::DebuggableAttribute(true, true)];   
    ```  
  
     Per altre informazioni, vedere <xref:System.Diagnostics.DebuggableAttribute>.  
  
 Il debug JIT può comunque essere abilitato anche se Visual Studio non è più presente nel computer.  Se Visual Studio non è installato, non è possibile disabilitare il debug JIT dalla finestra di dialogo **Opzioni** di Visual Studio.  In questo caso, è possibile disabilitare il debug JIT modificando il Registro di sistema di Windows.  
  
#### Per disabilitare il debug JIT modificando il Registro di sistema  
  
1.  Nel menu **Start** cercare ed eseguire `regedit.exe`  
  
2.  Nella finestra dell'**Editor del Registro di sistema** individuare ed eliminare le chiavi del Registro di sistema seguenti:  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\Windows NT\\CurrentVersion\\AeDebug\\Debugger  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\.NETFramework\\DbgManagedDebugger  
  
3.  Se nel computer è in esecuzione un sistema operativo a 64 bit, eliminare anche le chiavi del Registro di sistema seguenti:  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\Windows NT\\CurrentVersion\\AeDebug\\Debugger  
  
    -   HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Wow6432Node\\Microsoft\\.NETFramework\\DbgManagedDebugger  
  
4.  Fare attenzione a non eliminare o modificare altre chiavi del Registro di sistema.  
  
5.  Chiudere la finestra dell'**Editor del Registro di sistema**.  
  
## Errori del debug JIT  
 I messaggi di errore elencati di seguito sono associati al debug JIT.  
  
-   **Impossibile connettersi al processo bloccato.  Il programma specificato non è un programma Windows o MS\-DOS.**  
  
     Questo errore si verifica quando si tenta di connettersi a un processo in esecuzione come un altro utente in Windows 2000.  
  
     Per risolvere il problema, avviare Visual Studio, aprire la finestra di dialogo **Connetti a processo** dal menu **Debug** e trovare il processo di cui si desidera eseguire il debug nell'elenco **Processi disponibili**.  Se non si conosce il nome del processo, osservare la finestra di dialogo **Debugger JIT di Visual Studio** e prendere nota dell'ID del processo.  Selezionare tale processo nell'elenco **Processi disponibili** e fare clic su **Connetti**.  Nella finestra di dialogo **Debugger JIT di Visual Studio** scegliere **No** per chiudere la finestra di dialogo.  
  
-   **Impossibile avviare il debugger perché nessun utente è connesso.**  
  
     Questo errore si verifica quando il debug JIT tenta di avviare Visual Studio in un computer in cui nessun utente è connesso alla console.  Poiché nessun utente è connesso, non esiste una sessione utente nella quale visualizzare la finestra di dialogo del debug JIT.  
  
     Per correggere questo problema, connettersi al computer.  
  
-   **Classe non registrata.**  
  
     Questo errore indica che il debugger ha tentato di creare una classe COM non registrata, probabilmente a causa di un problema di installazione.  
  
     Per risolvere questo problema, usare il disco di installazione per reinstallare o riparare l'installazione di Visual Studio.  
  
## Vedere anche  
 [Sicurezza del debugger](../debugger/debugger-security.md)   
 [Nozioni di base sul debugger](../debugger/debugger-basics.md)   
 [JIT, Debug, Finestra di dialogo Opzioni](../debugger/just-in-time-debugging-options-dialog-box.md)   
 [Avviso di sicurezza: può essere pericoloso connettersi a un processo appartenente a un account utente non attendibile. Se le seguenti sottostanti risultano sospette o non sicure, non stabilire la connessione al processo.](../debugger/security-warning-attaching-to-a-process-owned-by-an-untrusted-user-can-be-dangerous-if-the-following-information-looks-suspicious-or-you-are-unsure-do-not-attach-to-this-process.md)