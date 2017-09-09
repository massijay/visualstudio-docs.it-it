---
title: Risoluzione dei problemi relativi all'installazione | Microsoft Docs
description: "Non sempre tutto funziona correttamente. Se l'installazione o l'aggiornamento di Visual Studio ha esito negativo, questa pagina può risultare utile."
ms.date: 08/28/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 556EDD3F-E365-43EE-B3DD-03AA4353F75B
author: timsneath
ms.author: tims
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6f0fe07b55ae0eeb57c0cc11fed047f31966cb6e
ms.openlocfilehash: 15e3b7cf051d26b6784df13f57794f6057e4c91c
ms.contentlocale: it-it
ms.lasthandoff: 09/06/2017

---
# <a name="troubleshooting-visual-studio-2017-installation-and-upgrade-issues"></a>Risoluzione dei problemi di installazione e aggiornamento di Visual Studio 2017

## <a name="symptoms"></a>Sintomi
Quando si prova a installare o aggiornare Visual Studio 2017, l'operazione ha esito negativo.

## <a name="workaround"></a>Soluzione alternativa
Per risolvere il problema, seguire questa procedura.

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Passaggio 1: Verificare se il problema è noto
Esistono alcuni problemi noti relativi al programma di installazione di Visual Studio che Microsoft sta cercando di risolvere. Consultare la [sezione Problemi noti delle note sulla versione](https://www.visualstudio.com/news/releasenotes/vs2017-knownissues) per scoprire se esiste una soluzione alternativa al problema.

### <a name="step-2---check-with-the-developer-community"></a>Passaggio 2: Verificare con la community degli sviluppatori
Cercare il messaggio di errore nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html). È possibile che altri membri della community abbiano documentato una soluzione per il problema.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Passaggio 3: Eliminare la directory del programma di installazione di Visual Studio per correggere i problemi di aggiornamento
Il programma di bootstrap dell'installazione di Visual Studio è un file eseguibile di piccole dimensioni che consente di installare gli elementi restanti del programma di installazione di Visual Studio. Eliminando i file del programma di installazione di Visual Studio ed eseguendo nuovamente il programma di bootstrap, è possibile risolvere alcuni problemi di aggiornamento.

**Nota:** eseguendo le azioni seguenti vengono reinstallati i file del programma di installazione di Visual Studio e vengono reimpostati i metadati di installazione.

1. Chiudere il programma di installazione di Visual Studio.
2. Eliminare la directory del programma di installazione di Visual Studio. In genere, la directory è C:\Program Files (x86)\Microsoft Visual Studio\Installer.
3. Eseguire il programma di bootstrap dell'installazione di Visual Studio. Il programma di bootstrap è disponibile nella cartella Download con un nome file che segue il modello ```vs_[Visual Studio edition]__*.exe```. Se non si trova l'applicazione, è possibile scaricare il programma di avvio automatico accedendo alla [pagina dei download di Visual Studio](https://www.visualstudio.com/downloads/) e facendo clic su **Download** per l'edizione di Visual Studio in uso. Eseguire il file eseguibile per reimpostare i metadati di installazione.
4. Provare di nuovo a installare o ad aggiornare Visual Studio. Se i problemi di installazione persistono, andare al passaggio successivo.

### <a name="step-4---report-a-problem"></a>Passaggio 4: Segnalare un problema
In alcune situazioni, ad esempio quando sono presenti file danneggiati, può essere necessario esaminare i problemi singolarmente:

1. Raccogliere i log di installazione. Per informazioni dettagliate, vedere [Come ottenere i log di installazione di Visual Studio](#how-to-get-the-visual-studio-installation-logs) più avanti.
2. Aprire il programma di installazione di Visual Studio e quindi fare clic su **Segnala un problema** per aprire Visual Studio Feedback Tool.
![È possibile usare il pulsante Commenti e suggerimenti per aprire lo strumento di feedback](media/report-a-problem.png)
3. Specificare un titolo per la segnalazione del problema e fornire i relativi dettagli. Fare clic su **Avanti** per accedere alla sezione **Allegati** e quindi allegare il file di log generato (in genere, è disponibile in %TEMP%\vslogs.zip).
![Premere il pulsante Segnala un nuovo problema e seguire la procedura necessaria](media/problem-report-details.png)
4. Fare clic su **Avanti** per controllare la segnalazione del problema e quindi fare clic su **Invia**.

### <a name="step-5---run-installcleanupexe-to-clean-up-installation-files"></a>Passaggio 5: Eseguire InstallCleanup.exe per pulire i file di installazione
Come ultima risorsa, è possibile eseguire InstallCleanup.exe, uno strumento incluso nel programma di installazione di Visual Studio che esegue la pulizia dei file di installazione. Questo strumento non esegue una reinstallazione completa, ma elimina i dati della cache e delle istanze relative a Visual Studio 2017.

1. Chiudere il programma di installazione di Visual Studio.
2. Aprire un prompt dei comandi dell'amministratore. A tale scopo, attenersi alla seguente procedura:
   * Fare clic sul pulsante **Start** e scegliere **Esegui** (tasto WINDOWS+R).
   * Digitare **cmd**.
   * Fare clic con il pulsante destro del mouse su **Prompt dei comandi** e quindi scegliere **Esegui come amministratore**.
3. Digitare il percorso completo dell'utilità InstallCleanup.exe e quindi passare il seguente parametro della riga di comando: -f. Per impostazione predefinita, il percorso dell'utilità è il seguente:
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```
4. Eseguire nuovamente il programma di avvio automatico descritto in [Passaggio 3: Eliminare la directory del programma di installazione di Visual Studio per correggere i problemi di aggiornamento](#step-3--delete-the-visual-studio-installer-directory-to-fix-upgrade-problems).
5. Provare di nuovo a installare o ad aggiornare Visual Studio.

## <a name="how-to-troubleshoot-an-offline-installer"></a>Come risolvere i problemi di un programma di installazione offline
Ecco una tabella dei problemi noti e di alcune soluzioni che possono essere utili quando si esegue l'installazione da un layout locale.

| Problema       | Elemento                   | Soluzione |
| ----------- | ---------------------- | -------- |
| Gli utenti non anno accesso ai file. | Autorizzazioni (ACL) | Assicurarsi di modificare le autorizzazioni (ACL) in modo da consentire l'accesso in lettura ad altri utenti *prima* di condividere l'installazione offline. |
| Non è possibile installare nuovi carichi di lavoro, componenti o lingue.  | `--layout`  | Assicurarsi che sia disponibile l'accesso a Internet se si esegue l'installazione da un layout parziale e si selezionano carichi di lavoro, componenti o lingue non scaricati precedentemente nel layout parziale. |

## <a name="how-to-get-the-visual-studio-installation-logs"></a>Come ottenere i log di installazione di Visual Studio
I log di installazione sono necessari per risolvere la maggior parte dei problemi di installazione. Quando si invia un problema mediante l'opzione [Segnala un problema](../ide/how-to-report-a-problem-with-visual-studio-2017.md) del programma di installazione di Visual Studio, questi log vengono automaticamente inclusi nel report.

Se si contatta il supporto tecnico Microsoft, è possibile che sia necessario fornire questi log di installazione usando [Microsoft Visual Studio e lo strumento di raccolta dei log di .NET Framework](https://aka.ms/vscollect). Lo strumento di raccolta dei log raccoglie i log di installazione da tutti i componenti installati da Visual Studio 2017, tra cui .NET Framework, Windows SDK e SQL Server. Raccoglie anche informazioni sul computer, oltre a un inventario di Windows Installer e a informazioni sul registro eventi di Windows per il programma di installazione di Visual Studio, Windows Installer e Ripristino configurazione di sistema.

Per raccogliere i log

1. [Scaricare lo strumento](https://aka.ms/vscollect).
2. Aprire un prompt dei comandi amministrativo.
3. Eseguire Collect.exe dalla directory in cui è stato salvato lo strumento.
4. Trovare il file Vslogs.zip risultante nella directory %TEMP%, ad esempio C:\Utenti\NomeUtente\AppData\Local\Temp\vslogs.zip.

> [!NOTE]
> Lo strumento deve essere eseguito usando lo stesso account utente con cui è stata eseguita l'installazione che ha avuto esito negativo. Se si esegue lo strumento da un account utente diverso, impostare l'opzione – user:\<nome\> in modo da specificare l'account utente con cui è stata eseguita l'installazione che ha avuto esito negativo. Per altre informazioni sull'utilizzo e sulle opzioni disponibili, eseguire `Collect.exe -?` da un prompt dei comandi amministrativo.

