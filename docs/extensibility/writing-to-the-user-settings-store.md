---
title: La scrittura nell&quot;archivio di impostazioni utente | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: efd27f00-7fe5-45f8-9b97-371af732be97
caps.latest.revision: 3
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 35ca397d57906a6316543325a08b118613fc2035
ms.lasthandoff: 02/22/2017

---
# <a name="writing-to-the-user-settings-store"></a>La scrittura nell'archivio di impostazioni utente
Le impostazioni utente sono scrivibile impostazioni simili a quelle nel **Strumenti / opzioni** finestra di dialogo, finestre delle proprietà e altre finestre di dialogo. Estensioni di Visual Studio possono utilizzarli per archiviare piccole quantità di dati. Questa procedura dettagliata viene illustrato come aggiungere il blocco note di Visual Studio come uno strumento esterno per la lettura e scrittura all'archivio di impostazioni dell'utente.  
  
### <a name="backing-up-your-user-settings"></a>Backup delle impostazioni utente  
  
1.  È necessario essere in grado di reimpostare le impostazioni di strumenti esterni in modo che è possibile eseguire il debug e ripetere la procedura. A tale scopo, è necessario salvare le impostazioni originali in modo che sia possibile ripristinarle in base alle esigenze.  
  
2.  Aprire Regedit.exe.  
  
3.  Passare a strumenti HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External\\.  
  
    > [!NOTE]
    >  Assicurarsi che si sta analizzando la chiave contenente \14.0Exp\ e non \14.0\\. Quando si esegue l'istanza sperimentale di Visual Studio, le impostazioni utente sono nell'hive del Registro di sistema "14.0Exp".  
  
4.  Pulsante destro del mouse sulla sottochiave \External Tools\ e quindi fare clic su **esportare**. Assicurarsi che **selezione** è selezionata.  
  
5.  Salvare il file esterno Tools.reg risulta.  
  
6.  Successivamente, quando si desidera ripristinare le impostazioni di strumenti esterni, selezionare la chiave del Registro di sistema HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\14.0Exp\External strumenti e fare clic su **eliminare** menu di scelta rapida.  
  
7.  Quando il **conferma eliminazione chiave** viene visualizzata la finestra di dialogo, fare clic su **Sì**.  
  
8.  Il file esterno Tools.reg salvato in precedenza, fare clic su **Apri con**, quindi fare clic su **Editor del Registro di sistema**.  
  
## <a name="writing-to-the-user-settings-store"></a>La scrittura nell'archivio di impostazioni utente  
  
1.  Creare un progetto VSIX denominato UserSettingsStoreExtension e quindi aggiungere un comando personalizzato denominato UserSettingsStoreCommand. Per ulteriori informazioni su come creare un comando personalizzato, vedere [creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
2.  In UserSettingsStoreCommand.cs, aggiungere le seguenti istruzioni using:  
  
    ```c#  
    using System.Collections.Generic;  
    using Microsoft.VisualStudio.Settings;  
    using Microsoft.VisualStudio.Shell.Settings;  
    ```  
  
3.  In MenuItemCallback, eliminare il corpo del metodo e ottiene l'utente archiviano le impostazioni, come indicato di seguito:  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
    }  
    ```  
  
4.  Ora Scopri se il blocco note è già impostato come uno strumento esterno. È necessario scorrere tutti gli strumenti esterni per determinare se l'impostazione ToolCmd è "Notepad", come indicato di seguito:  
  
    ```c#  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already an External Tool.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
    }  
  
    ```  
  
5.  Se il blocco note non è stato impostato come uno strumento esterno, impostarlo come segue:  
  
    ```vb  
    private void MenuItemCallback(object sender, EventArgs e)  
    {  
        SettingsManager settingsManager = new ShellSettingsManager(ServiceProvider);  
        WritableSettingsStore userSettingsStore = settingsManager.GetWritableSettingsStore(SettingsScope.UserSettings);  
  
        // Find out whether Notepad is already installed.  
        int toolCount = userSettingsStore.GetInt32("External Tools", "ToolNumKeys");  
        bool hasNotepad = false;  
        CompareInfo Compare = CultureInfo.InvariantCulture.CompareInfo;  
        for (int i = 0; i < toolCount; i++)  
        {  
            if (Compare.IndexOf(userSettingsStore.GetString("External Tools", "ToolCmd" + i), "Notepad", CompareOptions.IgnoreCase) >= 0)  
            {  
                hasNotepad = true;  
                break;  
            }  
        }  
  
        string message = (hasNotepad) ? "Notepad already installed" : "Installing Notepad";  
         if (!hasNotepad)  
        {  
            userSettingsStore.SetString("External Tools", "ToolTitle" + toolCount, "&Notepad");  
            userSettingsStore.SetString("External Tools", "ToolCmd" + toolCount, "C:\\Windows\\notepad.exe");  
            userSettingsStore.SetString("External Tools", "ToolArg" + toolCount, "");  
            userSettingsStore.SetString("External Tools", "ToolDir" + toolCount, "$(ProjectDir)");  
            userSettingsStore.SetString("External Tools", "ToolSourceKey" + toolCount, "");  
            userSettingsStore.SetUInt32("External Tools", "ToolOpt" + toolCount, 0x00000011);  
  
            userSettingsStore.SetInt32("External Tools", "ToolNumKeys", toolCount + 1);  
        }  
    }  
    ```  
  
6.  Test del codice. Tenere presente che aggiunge il blocco note come uno strumento esterno, pertanto è necessario ripristinare il Registro di sistema prima dell'esecuzione di una seconda volta.  
  
7.  Compilare il codice e avviare il debug.  
  
8.  Nel **strumenti** menu, fare clic su **UserSettingsStoreCommand richiamare**. Verrà aggiunto il blocco note per la **strumenti** menu.  
  
9. Ora verrà visualizzato il blocco note dal menu Strumenti / opzioni di menu e fare clic su **il blocco note** dovrebbe richiamare un'istanza del blocco note.
