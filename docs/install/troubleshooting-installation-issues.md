---
title: Risoluzione dei problemi relativi all&quot;installazione | Microsoft Docs
description: "Non sempre tutto funziona correttamente. Se l&quot;installazione o l&quot;aggiornamento di Visual Studio ha esito negativo, questa pagina può risultare utile."
ms.date: 04/14/2017
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
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: d9de84bed187c62962a76424aabdc5f355dff4dc
ms.openlocfilehash: e6c301a7b784c5966d4f7216e67067ef6ce3ed70
ms.contentlocale: it-it
ms.lasthandoff: 05/15/2017

---
# <a name="troubleshooting-visual-studio-2017-installation-and-upgrade-issues"></a>Risoluzione dei problemi di installazione e aggiornamento di Visual Studio 2017

## <a name="symptoms"></a>Sintomi
Quando si tenta di installare o aggiornare Microsoft Visual Studio 2017, l'operazione ha esito negativo.

## <a name="workaround"></a>Soluzione alternativa
Per risolvere il problema, seguire questa procedura.

### <a name="step-1---check-whether-this-problem-is-a-known-issue"></a>Passaggio 1: Verificare se il problema è noto
Esistono alcuni problemi noti relativi al programma di installazione di Visual Studio che Microsoft sta cercando di risolvere. Consultare la [sezione Problemi noti delle note sulla versione](https://www.visualstudio.com/en-us/news/releasenotes/vs2017-relnotes#KIinstall) per scoprire se esiste una soluzione alternativa al problema.

### <a name="step-2---check-with-the-developer-community"></a>Passaggio 2: Verificare con la community degli sviluppatori
Cercare il messaggio di errore nella [community degli sviluppatori di Visual Studio](https://developercommunity.visualstudio.com/spaces/8/index.html. È possibile che altri membri della community abbiano documentato una soluzione per il problema.

### <a name="step-3---delete-the-visual-studio-installer-directory-to-fix-upgrade-problems"></a>Passaggio 3: Eliminare la directory del programma di installazione di Visual Studio per correggere i problemi di aggiornamento
Il programma di bootstrap dell'installazione di Visual Studio è un file eseguibile di piccole dimensioni che consente di installare gli elementi restanti del programma di installazione di Visual Studio. Eliminando i file del programma di installazione di Visual Studio ed eseguendo nuovamente il programma di bootstrap, è possibile risolvere alcuni problemi di aggiornamento. A tale scopo, attenersi alla seguente procedura:

1. Chiudere il programma di installazione di Visual Studio.
2. Eliminare la directory del programma di installazione di Visual Studio. In genere, la directory è C:\Program Files (x86)\Microsoft Visual Studio\Installer.
3. Eseguire il programma di bootstrap dell'installazione di Visual Studio. Il programma di bootstrap è disponibile nella cartella Download con un nome file che segue il modello ```vs_[Visual Studio edition]__*.exe```. Se non si trova l'applicazione, è possibile scaricare il programma di bootstrap accedendo alla [pagina dei download di Visual Studio](https://www.visualstudio.com/downloads/) e facendo clic su **Download** per l'edizione di Visual Studio in uso. Eseguire il file eseguibile per reimpostare i metadati di installazione.
4. Provare di nuovo a installare o ad aggiornare Visual Studio. Se i problemi di installazione persistono, procedere al passaggio 4 di seguito.
<br/>**Nota:** con questo passaggio verranno reinstallati i file del programma di installazione di Visual Studio e ripristinati i metadati di installazione.

### <a name="step-4---report-a-problem"></a>Passaggio 4: Segnalare un problema
In alcune situazioni, ad esempio quando sono presenti file danneggiati, può essere necessario esaminare i problemi singolarmente:

1. Scaricare ed eseguire lo [strumento di raccolta dei log di Microsoft Visual Studio e .NET Framework](https://www.microsoft.com/en-us/download/details.aspx?id=12493). Questo strumento raccoglie e compila i log di installazione disponibili per Visual Studio, .NET Framework e SQL Server.
2. Aprire il programma di installazione di Visual Studio e quindi fare clic su **Segnala un problema** per aprire Visual Studio Feedback Tool.
![È possibile usare il pulsante Commenti e suggerimenti per aprire lo strumento di feedback](~/docs/install/media/report-a-problem.png)
3. Specificare un titolo per la segnalazione del problema e fornire i relativi dettagli. Fare clic su **Avanti** per accedere alla sezione **Allegati** e quindi allegare il file di log generato (in genere, è disponibile in %TEMP%\vslogs.zip).
![Premere il pulsante Segnala un nuovo problema e seguire la procedura necessaria](~/docs/install/media/problem-report-details.png)
4. Fare clic su **Avanti** per controllare la segnalazione del problema e quindi fare clic su **Invia**.

### <a name="step-5---run-installcleanupexe-to-clean-up-installation-files"></a>Passaggio 5: Eseguire InstallCleanup.exe per pulire i file di installazione
Come ultima risorsa, è possibile eseguire InstallCleanup.exe, un'utilità inclusa nel programma di installazione di Visual Studio ed esegue la pulizia dei file di installazione. Non si tratta di una reinstallazione completa. Questa utilità elimina i dati della cache e delle istanze relative a Visual Studio 2017.

1. Chiudere il programma di installazione di Visual Studio.
2. Aprire un prompt dei comandi dell'amministratore. A tale scopo, attenersi alla seguente procedura:
   * Fare clic sul pulsante **Start** e scegliere **Esegui** (tasto WINDOWS+R).
   * Digitare **cmd**.
   * Fare clic con il pulsante destro del mouse su **Prompt dei comandi** e quindi scegliere **Esegui come amministratore**.
3. Digitare il percorso completo dell'utilità InstallCleanup.exe e quindi passare il seguente parametro della riga di comando: -f. Per impostazione predefinita, il percorso dell'utilità è il seguente:
   ```
   C:\Program Files (x86)\Microsoft Visual Studio\Installer\resources\app\layout\InstallCleanup.exe
   ```
4. Eseguire nuovamente il programma di avvio automatico descritto nel passaggio 3.
5. Provare di nuovo a installare o ad aggiornare Visual Studio.

## <a name="how-to-troubleshoot-an-offline-installer"></a>Come risolvere i problemi di un programma di installazione offline
Ecco una tabella dei problemi noti e di alcune soluzioni che possono essere utili quando si esegue l'installazione da un layout locale.

| Problema       | Elemento                   | Soluzione |
| ----------- | ---------------------- | -------- |
| Gli utenti non anno accesso ai file. | Autorizzazioni (ACL) | Assicurarsi di modificare le autorizzazioni (ACL) in modo da consentire l'accesso in lettura ad altri utenti *prima* di condividere l'installazione offline. |
| Non è possibile installare nuovi carichi di lavoro, componenti o lingue.  | `--layout`  | Assicurarsi di avere accesso a Internet se si esegue l'installazione da un layout parziale e si selezionano carichi di lavoro, componenti o lingue non disponibili nel layout precedente. |

