---
title: "Utilizzo dell&#39;archivio impostazioni | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Archivio impostazioni, utilizzo"
ms.assetid: 447ec08a-eca5-40b8-89b0-f98fdf3d39a4
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# Utilizzo dell&#39;archivio impostazioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Esistono due tipi di archivi di impostazioni:  
  
-   Impostazioni di configurazione, sono impostazioni di Visual Studio e VSPackage di sola lettura. Visual Studio unisce le impostazioni da tutti i file. pkgdef noti in questo archivio.  
  
-   Impostazioni utente, che sono le impostazioni modificabili, ad esempio quelli che vengono visualizzati nelle pagine di **Opzioni** la finestra di dialogo Pagine delle proprietà e altre finestre di dialogo. Estensioni di Visual Studio possono utilizzare per l'archiviazione locale di piccole quantità di dati.  
  
 Questa procedura dettagliata viene illustrato come leggere dati dall'archivio di impostazione di configurazione. Vedere [La scrittura nell'archivio di impostazioni utente](../extensibility/writing-to-the-user-settings-store.md) per una spiegazione della modalità di scrittura nell'archivio di impostazioni utente.  
  
## Creazione del progetto di esempio  
 In questa sezione viene illustrato come creare un progetto di estensione semplice con un comando di menu per la dimostrazione.  
  
1.  Ogni estensione di Visual Studio inizia con un progetto di distribuzione VSIX che contiene le risorse di estensione. Creare un [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] progetto VSIX denominato `SettingsStoreExtension`. È possibile trovare il modello di progetto VSIX nel **Nuovo progetto** nella finestra di dialogo **Visual c\# \/ Extensibility**.  
  
2.  A questo punto aggiungere un modello di elemento di comando personalizzato denominato **SettingsStoreCommand**. Nel **Aggiungi nuovo elemento** finestra di dialogo, andare a **Visual c\# \/ Extensibility** e selezionare **comando personalizzato**. Nel **nome** campo nella parte inferiore della finestra, modificare il nome del file di comando in **SettingsStoreCommand.cs**. Per ulteriori informazioni su come creare un comando personalizzato, vedere [Creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
## Usa l'archivio di impostazioni di configurazione  
 In questa sezione viene illustrato come rilevare e visualizzare le impostazioni di configurazione.  
  
1.  Nel file SettingsStorageCommand.cs, aggiungere le seguenti istruzioni using:  
  
    ```  
    using System.Collections.Generic; using Microsoft.VisualStudio.Settings; using Microsoft.VisualStudio.Shell.Settings; using System.Windows.Forms;  
    ```  
  
2.  In `MenuItemCallback`, rimuovere il corpo del metodo e aggiungere queste righe ottenere l'archivio di impostazioni di configurazione:  
  
    ```  
    SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration);  
    ```  
  
     Il <xref:Microsoft.VisualStudio.Shell.Settings.ShellSettingsManager> è una classe helper gestita tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> servizio.  
  
3.  Ora Scopri se vengono installati gli strumenti di Windows Phone. Il codice dovrebbe essere simile al seguente:  
  
    ```  
    private void MenuItemCallback(object sender, EventArgs e) { SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider); SettingsStore configurationSettingsStore = settingsManager.GetReadOnlySettingsStore(SettingsScope.Configuration); bool arePhoneToolsInstalled = configurationSettingsStore.CollectionExists(@"InstalledProducts\Microsoft Windows Phone Developer Tools"); string message = "Microsoft Windows Phone Developer Tools: " + arePhoneToolsInstalled; MessageBox.Show(message); }  
    ```  
  
4.  Test del codice. Compilare il progetto e avviare il debug.  
  
5.  Nell'istanza sperimentale, nel **strumenti** menu, fare clic su **richiamare SettingsStoreCommand**.  
  
     Verrà visualizzato un messaggio **Microsoft Windows Phone Developer Tools:**  seguito da **True** o **False**.  
  
 Visual Studio consente di mantenere l'archivio delle impostazioni del Registro di sistema.  
  
#### Per utilizzare un editor del Registro di sistema per verificare le impostazioni di configurazione  
  
1.  Aprire Regedit.exe.  
  
2.  Passare a HKEY\_CURRENT\_USER\\Software\\Microsoft\\VisualStudio\\14.0Exp\_Config\\InstalledProducts\\.  
  
    > [!NOTE]
    >  Assicurarsi che si sta analizzando la chiave contenente \\14.0Exp\_Config\\ e non \\14.0\_Config\\. Quando si esegue l'istanza sperimentale di Visual Studio, le impostazioni di configurazione sono nell'hive del Registro di sistema "14.0Exp\_Config".  
  
3.  Espandere il nodo \\Installed Products\\. Se il messaggio nei passaggi precedenti è **Microsoft Windows Phone Developer Tools installato: True**, quindi \\Installed Products\\ deve contenere un nodo di Microsoft Windows Phone Developer Tools. Se il messaggio è **Microsoft Windows Phone Developer Tools installato: False**, quindi \\Installed Products\\ non deve contenere un nodo di Microsoft Windows Phone Developer Tools.