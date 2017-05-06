---
title: "Debugging Extensions for the SharePoint Tools in Visual Studio"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, debugging extensions"
ms.assetid: 7cee8ce0-d07b-41f6-8ce1-b18e4be3b50c
caps.latest.revision: 26
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Debugging Extensions for the SharePoint Tools in Visual Studio
  È possibile eseguire il debug delle estensioni per gli strumenti di SharePoint nell'istanza sperimentale o nell'istanza regolare di Visual Studio.  Se è necessario risolvere problemi relativi al comportamento di un'estensione, è anche possibile modificare i valori del Registro di sistema per visualizzare ulteriori informazioni sull'errore e per configurare la modalità di esecuzione dei comandi di SharePoint in Visual Studio.  
  
## Debug delle estensioni nell'istanza sperimentale di Visual Studio  
 Per proteggere l'ambiente di sviluppo di Visual Studio da danni fortuiti causati da estensioni non testate, Visual Studio SDK offre un'istanza di Visual Studio alternativa, denominata *istanza sperimentale*, che è possibile utilizzare per installare e testare le estensioni.  Per sviluppare nuove estensioni viene utilizzata l'istanza regolare di Visual Studio, mentre per il debug e l'esecuzione viene utilizzata l'istanza sperimentale.  Per ulteriori informazioni, vedere [L'istanza sperimentale](../extensibility/the-experimental-instance.md).  
  
 Se si utilizza un progetto VSIX per distribuire l'estensione e tale progetto è il progetto di avvio nella soluzione, l'estensione viene installata ed eseguita automaticamente nell'istanza sperimentale di Visual Studio quando si esegue il debug della soluzione.  Il progetto di avvio è il progetto che viene avviato quando si esegue il debug di una soluzione contenente più progetti.  Per ulteriori informazioni sull'utilizzo di un progetto VSIX per la distribuzione dell'estensione, vedere [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md).  Per ulteriori informazioni sui progetti di avvio, vedere [Procedura: impostare progetti di avvio](http://msdn.microsoft.com/it-it/31465836-0911-48db-a5d9-e456b635e970).  
  
 Per esempi che illustrano come eseguire il debug di vari tipi di estensioni nell'istanza sperimentale di Visual Studio, vedere le procedure dettagliate seguenti:  
  
-   [Walkthrough: Extending a SharePoint Project Item Type](../sharepoint/walkthrough-extending-a-sharepoint-project-item-type.md)  
  
-   [Walkthrough: Creating a Custom Action Project Item with an Item Template, Part 1](../sharepoint/walkthrough-creating-a-custom-action-project-item-with-an-item-template-part-1.md)  
  
-   [Walkthrough: Creating a Custom Deployment Step for SharePoint Projects](../sharepoint/walkthrough-creating-a-custom-deployment-step-for-sharepoint-projects.md)  
  
-   [Walkthrough: Extending Server Explorer to Display Web Parts](../sharepoint/walkthrough-extending-server-explorer-to-display-web-parts.md)  
  
-   [Walkthrough: Calling into the SharePoint Client Object Model in a Server Explorer Extension](../sharepoint/walkthrough-calling-into-the-sharepoint-client-object-model-in-a-server-explorer-extension.md)  
  
## Debug delle estensioni nell'istanza regolare di Visual Studio  
 Se si desidera eseguire il debug del progetto di estensione nell'istanza regolare di Visual Studio, installare innanzitutto l'estensione nell'istanza regolare.  Associare quindi il debugger a un secondo processo di Visual Studio.  Al termine, è possibile rimuovere l'estensione in modo che non venga più caricata nel computer di sviluppo.  
  
#### Per installare l'estensione  
  
1.  Chiudere tutte le istanze di Visual Studio.  
  
2.  Nella cartella di output di compilazione per il progetto di estensione, aprire il file .vsix facendovi doppio clic o aprendo il menu di scelta rapida e scegliendo **Apri**:  
  
3.  Nella finestra di dialogo **Visual Studio Extension Installer**, scegliere la versione di Visual Studio in cui si desidera installare l'estensione, quindi scegliere il pulsante **Installa**.  
  
     I file di estensione vengono installati nel percorso %UserProfile%\\AppData\\Local\\Microsoft\\VisualStudio\\11.0\\Extensions\\*author name*\\*extension name*\\*version*.  Le ultime tre cartelle di questo percorso vengono costruite mediante gli elementi `Author`, `Name` e `Version` del file extension.vsixmanifest dell'estensione.  
  
4.  Al termine dell'installazione dell'estensione mediante Visual Studio, scegliere il pulsante **Chiudi**.  
  
#### Per eseguire il debug dell'estensione  
  
1.  Avviare Visual Studio con i privilegi di amministratore e aprire il progetto di estensione.  Nei passaggi riportati di seguito verrà fatto riferimento a questa istanza di Visual Studio come *prima istanza*.  
  
2.  Avviare un'altra istanza di Visual Studio con i privilegi di amministratore.  Nei passaggi riportati di seguito verrà fatto riferimento a questa istanza di Visual Studio come *seconda istanza*.  
  
3.  Passare alla prima istanza di Visual Studio.  
  
4.  Nella barra dei menu, scegliere **Debug**, **Connetti a processo**.  
  
5.  Nell'elenco **Processi disponibili**, scegliere devenv.exe.  Questa voce si riferisce alla seconda istanza di Visual Studio, ovvero l'istanza in cui eseguire il debug dell'estensione di progetto.  
  
6.  Fare clic sul pulsante **Connetti**.  
  
     Il progetto di estensione viene eseguito nella modalità di debug di Visual Studio.  
  
7.  Passare alla seconda istanza di Visual Studio.  
  
8.  Creare un nuovo progetto SharePoint che carichi l'estensione.  Se, ad esempio, si esegue il debug di un'estensione per gli elementi del progetto di definizione di elenco, creare un progetto **Definizione di elenco**.  
  
9. Eseguire tutti i passaggi necessari per testare il codice di estensione.  
  
10. Al termine del debug dell'estensione, chiudere la seconda istanza di Visual Studio.  
  
#### Per rimuovere l'estensione  
  
1.  In Visual Studio, sulla barra dei menu, scegliere **Strumenti**, **Estensioni e Aggiornamenti**.  
  
     Verrà visualizzata la finestra di dialogo **Estensioni e aggiornamenti**.  
  
2.  Nell'elenco di estensioni, scegliere il nome dell'estensione, quindi scegliere il pulsante **Disinstalla**.  
  
3.  Nella finestra di dialogo visualizzata, scegliere il pulsante **Sì** per confermare che si desidera disinstallare l'estensione.  
  
4.  Scegliere il pulsante **Riavvia ora** per completare la disinstallazione.  
  
## Debug di comandi di SharePoint  
 Se si desidera eseguire il debug di un comando di SharePoint che fa parte di un'estensione degli strumenti di SharePoint, è necessario connettere il debugger al processo vssphost4.exe.  Tale processo è il processo host a 64 bit che esegue i comandi di SharePoint.  Per ulteriori informazioni sui comandi di SharePoint e su vssphost4.exe, vedere [Calling into the SharePoint Object Models](../sharepoint/calling-into-the-sharepoint-object-models.md).  
  
#### Per connettere il debugger al processo vssphost4.exe  
  
1.  Avviare il debug dell'estensione nell'istanza sperimentale o nell'istanza normale di Visual Studio seguendo le istruzioni riportate in precedenza.  
  
2.  Nell'istanza di Visual Studio in cui è in esecuzione il debugger, nella barra dei menu, scegliere **Debug**, **Connetti a processo**.  
  
3.  Nell'elenco **Processi disponibili**, scegliere vssphost.exe.  
  
    > [!NOTE]  
    >  Se vssphost.exe non è visualizzato nell'elenco, è necessario avviare il processo vssphost4.exe nell'istanza di Visual Studio in cui è in esecuzione l'estensione.  In genere, a tale scopo è possibile eseguire un'azione che comporta la connessione di Visual Studio al sito di SharePoint nel computer di sviluppo.  Tramite Visual Studio viene ad esempio avviato vssphost4.exe quando si espande un nodo relativo alla connessione al sito \(un nodo in cui è visualizzato l'URL del sito\) sotto il nodo **Connessioni di SharePoint** nella finestra **Esplora server** o quando si aggiungono determinati elementi di progetto SharePoint, ad esempio elementi **Istanza di elenco** o **Ricevitore di eventi**, a un progetto SharePoint.  
  
4.  Fare clic sul pulsante **Connetti**.  
  
5.  Nell'istanza di Visual Studio di cui viene eseguito il debug eseguire i passaggi necessari per l'esecuzione del comando.  
  
## Modifica dei valori del Registro di sistema per agevolare il debug delle estensioni degli strumenti di SharePoint  
 Quando si esegue il debug di un'estensione degli strumenti di SharePoint in Visual Studio, è possibile modificare i valori nel Registro di sistema per risolvere i problemi relativi all'estensione.  I valori si trovano nella chiave HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\11.0 .0\\SharePointTools.  Questi valori non sono presenti per impostazione predefinita.  
  
 Per risolvere i problemi relativi a qualsiasi estensione degli strumenti di SharePoint, è possibile creare ed impostare il valore EnableDiagnostics.  Questo valore è descritto nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|EnableDiagnostics|REG\_DWORD che specifica se i messaggi di diagnostica vengono visualizzati nella finestra **Output**.<br /><br /> Per visualizzare i messaggi di diagnostica, impostare questo valore su 1.  Per interrompere la visualizzazione di messaggi, impostare questo valore su 0 o eliminarlo.<br /><br /> Per scrivere i messaggi nella finestra **Output** da un'estensione degli strumenti di SharePoint, utilizzare il servizio del progetto SharePoint.  Per ulteriori informazioni, vedere [Using the SharePoint Project Service](../sharepoint/using-the-sharepoint-project-service.md).|  
  
 Se l'estensione include un comando di SharePoint, è possibile creare ed impostare valori aggiuntivi per risolvere i problemi relativi al comando.  Questi valori sono descritti nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|AttachDebuggerToHostProcess|REG\_DWORD che specifica se visualizzare una finestra di dialogo che consente di connettere il debugger a vssphost4.exe subito dopo l'avvio.  Questa operazione è utile se il comando di cui si desidera eseguire il debug viene eseguito da vssphost.exe immediatamente dopo l'avvio e non vi è tempo sufficiente per connettere manualmente il debugger prima dell'esecuzione del comando.  Per visualizzare la finestra di dialogo, vssphost4.exe chiama il metodo <xref:System.Diagnostics.Debugger.Break%2A> all'avvio.<br /><br /> Per abilitare questo comportamento, impostare questo valore su 1.  Per disattivare questo comportamento, impostare questo valore su 0 o eliminarlo.<br /><br /> Se si imposta questo valore su 1, potrebbe anche essere necessario aumentare il valore di HostProcessStartupTimeout in modo da consentire un tempo sufficiente per connettere il debugger prima che Visual Studio attenda il segnale di esecuzione corretta dell'avvio da parte di vssphost4.exe.|  
|ChannelOperationTimeout|REG\_DWORD che specifica il tempo di attesa, in secondi, dell'esecuzione di un comando di SharePoint.  Se il comando non viene eseguito in tempo, viene generata un'eccezione <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException>.<br /><br /> Il valore predefinito è 120 secondi.|  
|HostProcessStartupTimeout|REG\_DWORD che specifica il tempo di attesa, in secondi, della segnalazione di avvio riuscito di vssphost4.exe.  Se tale segnalazione non viene visualizzata in tempo, viene generata un'eccezione <xref:Microsoft.VisualStudio.SharePoint.SharePointConnectionException>.<br /><br /> Il valore predefinito è 60 secondi.|  
|MaxReceivedMessageSize|REG\_DWORD che specifica la dimensione massima consentita, in byte, per i messaggi WCF passati tra Visual Studio e vssphost4.exe.<br /><br /> Il valore predefinito è 1.048.576 byte \(1 MB\).|  
|MaxStringContentLength|REG\_DWORD che specifica la dimensione massima consentita, in byte, per le stringhe passate tra Visual Studio e vssphost4.exe.<br /><br /> Il valore predefinito è 1.048.576 byte \(1 MB\).|  
  
## Vedere anche  
 [Extending the SharePoint Tools in Visual Studio](../sharepoint/extending-the-sharepoint-tools-in-visual-studio.md)   
 [Deploying Extensions for the SharePoint Tools in Visual Studio](../sharepoint/deploying-extensions-for-the-sharepoint-tools-in-visual-studio.md)  
  
  