---
title: "Distribuire applicazioni Windows Store da Visual Studio | Microsoft Docs"
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
ms.assetid: ef3a0f36-bfc9-4ca0-aa61-18261f619bff
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# Distribuire applicazioni Windows Store da Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

![Si applica solo a Windows](~/docs/debugger/media/windows_only_content.png "windows\_only\_content")  
  
 Usando la funzionalità di distribuzione di Visual Studio, puoi compilare e registrare app Windows Store create con Visual Studio su un dispositivo di destinazione. Il modo in cui viene registrata l'app è determinato dal tipo di dispositivo, ovvero se è locale o remoto:  
  
-   Quando la destinazione è il computer Visual Studio locale, Visual Studio registra l'app dalla cartella della build dell'app stessa.  
  
-   Quando la destinazione è un dispositivo remoto, Visual Studio copia i file necessari nel computer remoto e registra l'app su questo dispositivo.  
  
 La distribuzione avviene automaticamente quando si esegue il debug dell'app da Visual Studio usando l'opzione **Avvia debug** \(tastiera: F5\) oppure l'opzione **Avvia senza eseguire debug** \(tastiera: CTRL\+F5\). Puoi distribuire l'app anche manualmente. Ecco gli scenari in cui la distribuzione manuale può essere utile:  
  
-   Test ad hoc su un computer locale o remoto.  
  
-   Distribuzione di un'app che avvia un'altra app di cui vuoi eseguire il debug.  
  
-   Distribuzione di un'app di cui viene eseguito il debug quando viene avviata da un'altra app o da un altro metodo.  
  
##  <a name="BKMK_In_this_topic"></a> Contenuto dell'argomento  
 Questo argomento contiene informazioni su:  
  
 [Come distribuire un'app Windows Store](#BKMK_How_to_deploy_a_Windows_Store_app)  
  
 [Come specificare un dispositivo remoto](#BKMK_How_to_specify_a_remote_device)  
  
 [Opzioni di distribuzione](#BKMK_Deployment_options)  
  
##  <a name="BKMK_How_to_deploy_a_Windows_Store_app"></a> Come distribuire un'app Windows Store  
 La distribuzione manuale di un'app è un processo facile:  
  
1.  Se esegui la distribuzione in un dispositivo remoto, specifica il nome o l'indirizzo IP del dispositivo nella pagina delle proprietà del progetto di avvio dell'app. I passaggi necessari sono elencati più avanti in questo argomento.  
  
2.  Sulla barra degli strumenti Visual Studio del debugger seleziona la destinazione di distribuzione nell'elenco a discesa accanto al pulsante **Avvia debug**.  
  
     ![Effettuare l'esecuzione nel computer locale](../debugger/media/vsrun_f5_local.png "VSRUN\_F5\_Local")  
  
3.  Scegli **Distribuzione** dal menu **Compilazione**.  
  
##  <a name="BKMK_How_to_specify_a_remote_device"></a> Come specificare un dispositivo remoto  
 **Prerequisiti**  
  
 Per distribuire un'app in un dispositivo remoto:  
  
-   Nel dispositivo remoto deve essere installata una licenza per sviluppatori.  
  
-   Visual Studio Remote Tools deve essere installato nel dispositivo remoto e Remote Debugging Monitor deve essere in esecuzione.  
  
     La distribuzione usa il canale di rete del debugger remoto per inviare i file dell'app al dispositivo remoto.  
  
#### Per specificare un dispositivo remoto  
  
1.  Nella pagina delle proprietà Debug del progetto di avvio specifica il nome o l'indirizzo IP di una destinazione di distribuzione remota.  
  
2.  Per aprire la pagina delle proprietà Debug, seleziona il progetto in Esplora soluzioni e scegli **Proprietà** dal menu di scelta rapida.  
  
3.  Seleziona il nodo **Debug** nella finestra della pagina delle proprietà.  
  
4.  Puoi digitare il nome o l'indirizzo IP del dispositivo remoto oppure selezionare il dispositivo nella finestra di dialogo  **Seleziona connessione debugger remoto**.  
  
     ![Finestra di dialogo per la selezione della connessione del debugger remoto](~/docs/debugger/media/vsrun_selectremotedebuggerdlg.png "VSRUN\_SelectRemoteDebuggerDlg")  
  
     Nella finestra di dialogo **Seleziona connessione debugger remoto** sono visualizzati i dispositivi presenti sulla subnet di rete locale e tutti i dispositivi direttamente collegati al computer Visual Studio tramite un cavo Ethernet.  
  
 **Indicazione del dispositivo remoto nella pagina di un progetto JavaScript o Visual C\+\+**  
  
 ![Proprietà del progetto C&#43;&#43; per il debug remoto](~/docs/debugger/media/vsrun_cpp_projprop_remote.png "VSRUN\_CPP\_ProjProp\_Remote")  
  
1.  Scegli **Debugger remoto** dall'elenco **Debugger da avviare**.  
  
2.  Immetti il nome di rete del dispositivo remoto nella casella **Nome computer**. In alternativa, puoi fare clic sulla freccia in giù della casella per selezionare il dispositivo nella finestra di dialogo Seleziona connessione debugger remoto.  
  
 **Indicazione del dispositivo remoto nella pagina di un progetto Visual C\# o Visual Basic**  
  
 ![Proprietà del progetto gestito per il debug remoto](../debugger/media/vsrun_managed_projprop_remote.png "VSRUN\_Managed\_ProjProp\_Remote")  
  
1.  Scegli **Computer remoto** dall'elenco **Dispositivo di destinazione**.  
  
2.  Immetti il nome di rete del dispositivo remoto nella casella **Computer remoto** o fai clic su **Trova** per scegliere il dispositivo nella finestra di dialogo **Seleziona connessione debugger remoto**.  
  
##  <a name="BKMK_Deployment_options"></a> Opzioni di distribuzione  
 Di seguito sono indicate le opzioni di distribuzione che puoi impostare nella pagina delle proprietà Debug del progetto di avvio.  
  
 **Consenti loopback della rete locale**  
 Per motivi di sicurezza, a un'app [!INCLUDE[win8_appname_long](../debugger/includes/win8_appname_long_md.md)] installata in modalità standard non è consentito effettuare chiamate di rete al dispositivo su cui è installata. Per impostazione predefinita, la distribuzione di Visual Studio crea una esenzione da questa regola per l'app distribuita. Questa esenzione ti consente di verificare le procedure di comunicazione in un singolo computer. Prima di inviare l'app a [!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)], dovrai testarla senza l'esenzione.  
  
 Per rimuovere l'esenzione relativa al loopback della rete:  
  
-   Nella pagina delle proprietà Debug in C\# e Visual Basic, deseleziona la casella di controllo **Consenti loopback della rete locale**.  
  
-   Nella pagina delle proprietà Debug in JavaScript e C\+\+ imposta il valore di **Consenti loopback della rete locale** su **No**.  
  
 **Non eseguire il codice utente, ma eseguine il debug all'avvio \(C\# e Visual Basic\)\/Avvia applicazione \(JavaScript e C\+\+\)**  
 Per configurare la distribuzione in modo da avviare automaticamente una sessione di debug all'avvio dell'app:  
  
-   Nella pagina delle proprietà Debug in C\# e Visual Basic seleziona la casella di controllo **Non eseguire il codice utente, ma eseguine il debug all'avvio**.  
  
-   Nella pagina delle proprietà Debug in JavaScript e C\+\+ imposta il valore di **Avvia applicazione** su **Sì**.  
  
## Vedere anche  
 [Eseguire app da Visual Studio](../debugger/run-store-apps-from-visual-studio.md)