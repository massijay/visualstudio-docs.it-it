---
title: Considerazioni speciali per l'installazione di Visual Studio in un ambiente offline | Microsoft Docs
description: '{{PLACEHOLDER}}'
ms.date: 06/05/2017
ms.reviewer: tims
ms.suite: 
ms.technology:
- vs-ide-install
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- '{{PLACEHOLDER}}'
- '{{PLACEHOLDER}}'
ms.assetid: 9750A3F3-89C7-4A8F-BA75-B0B06BD772C2
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
ms.sourcegitcommit: 8ce85525f6af336682f6f8547c2f6c13dde73c8c
ms.openlocfilehash: 1ce2f854d1c8e4a184446fb07c66a6fad9ca9ae1
ms.contentlocale: it-it
ms.lasthandoff: 06/23/2017

---
# <a name="special-considerations-for-installing-visual-studio-in-an-offline-environment"></a>Considerazioni speciali per l'installazione di Visual Studio in un ambiente offline

Visual Studio è progettato per essere installato da un computer connesso a Internet, poiché molti componenti vengono aggiornati regolarmente. Con alcuni passaggi aggiuntivi, tuttavia, è possibile distribuire Visual Studio anche in un ambiente in cui non è disponibile una connessione Internet.

## <a name="install-certificates-needed-for-visual-studio-offline-installation"></a>Installare i certificati necessari per l'installazione offline di Visual Studio
Il motore di installazione di Visual Studio installa solo contenuti attendibili. Per eseguire questa operazione, verificare le firme Authenticode dei contenuti scaricati e, prima di installarli, controllare l'attendibilità di tutti i contenuti. In questo modo l'ambiente rimane protetto dagli attacchi caratterizzati dalla compromissione del percorso di download. L'installazione di Visual Studio richiede pertanto l'installazione e l'aggiornamento nel computer dell'utente di diversi certificati Microsoft radice e intermedi standard. Se l'aggiornamento del computer è affidato a Windows Update, i certificati di firma vengono aggiornati automaticamente e durante l'installazione Visual Studio aggiorna i certificati in modo da essere in grado di verificare le firme dei file. 

Per le aziende con computer offline che non hanno i certificati radice più recenti, un amministratore può usare [queste istruzioni](https://technet.microsoft.com/en-us/library/dn265983.aspx) per eseguire l'aggiornamento. In alternativa, è possibile scaricare i certificati durante la creazione di un layout di rete per la cartella `certificates` Tali certificati possono essere installati manualmente facendo doppio clic sul file di certificato e quindi eseguendo la gestione guidata certificati. Se viene richiesto di immettere una password, lasciare il campo vuoto.

Se si sta eseguendo lo scripting di distribuzione di Visual Studio in un ambiente offline per le workstation client, è necessario seguire questa procedura:

1. Copiare lo [strumento gestore di certificati](https://msdn.microsoft.com/en-us/library/e78byta0.aspx) (`certmgr.exe`) nella condivisione di installazione, ad esempio `\\server\share\vs2017`. `certmgr.exe`non è incluso all'interno di Windows, ma è disponibile all'interno di [Windows SDK](https://developer.microsoft.com/en-US/windows/downloads/windows-10-sdk). 

2. Creare un file batch con i comandi seguenti:

   ```cmd
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Code Signing PCA 2011" -s -r LocalMachine CA
   
   certmgr.exe -add -c certificates\manifestSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   
   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Time-Stamp PCA 2010" -s -r LocalMachine CA
   
   certmgr.exe -add -c certificates\manifestCounterSignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   
   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Code Signing PCA" -s -r LocalMachine CA
   
   certmgr.exe -add -c certificates\vs_installer_opc.SignCertificates.p12 -n "Microsoft Root Certificate Authority" -s -r LocalMachine root
   ```

3. Distribuire il file batch al client. Questo comando deve essere eseguito da un processo con privilegi elevati.

### <a name="what-are-the-certificates-files-in-the-certificates-folder"></a>Quali sono i file dei certificati nella cartella `certificates`?
I tre file `.p12` in questa cartella contengono ognuno un certificato intermedio e un certificato radice. La maggior parte dei sistemi mantenuti aggiornati con Windows Update avrà già installato questi certificati.

1. `ManifestSignCertificates.p12` contiene:
    * Certificato intermedio: **Microsoft Code Signing PCA 2011**
        * Non richiesto Se presente, migliora le prestazioni in alcuni scenari.
    * Certificato radice: **Microsoft Root Certificate Authority 2011**
        * Obbligatorio per i sistemi Windows 7 Service Pack 1 in cui non sono installati gli ultimi aggiornamenti di Windows Updates.
2. `ManifestCounterSignCertificates.p12`
    * Certificato intermedio: **Microsoft Time-Stamp PCA 2010**
        * Non richiesto Se presente, migliora le prestazioni in alcuni scenari.
    * Certificato radice: **Microsoft Root Certificate Authority 2010**
        * Obbligatorio per i sistemi Windows 7 Service Pack 1 in cui non sono installati gli ultimi aggiornamenti di Windows Updates.
3. `vs_installer_opc.SignCertificates.p12`
    * Certificato intermedio: **Microsoft Code Signing PCA**
        * Obbligatorio per tutti i sistemi. Si noti che i sistemi in tutti gli aggiornamenti sono stati applicati da Windows Update potrebbero non avere questo certificato.
    * Certificato radice: **Microsoft Root Certificate Authority**
        * Obbligatorio. Questo certificato viene fornito con i sistemi che eseguono Windows 7 o versione successiva.

### <a name="why-are-the-certificates-from-the-certificates-folder-not-installed-automatically"></a>Perché i certificati della cartella `certificates` non vengono installati automaticamente?
Se una firma viene verificata in un ambiente online, per scaricare e aggiungere i certificati al sistema vengono usate le API di Windows. È nel corso di questo processo che, tramite impostazioni amministrative, si verifica se il certificato è attendibile e consentito. Questo processo di verifica, tuttavia, non può aver luogo nella maggior parte degli ambienti offline. Con l'installazione manuale dei certificati, gli amministratori all'interno delle aziende possono verificare che i certificati siano attendibili e soddisfino i criteri di sicurezza dell'organizzazione.

### <a name="checking-if-certificates-are-already-installed"></a>Verifica della presenza dei certificati
Un modo per eseguire questa verifica nel sistema di installazione corrisponde all'esecuzione di questa procedura:
* Eseguire mmc.exe
* Fare clic su File e scegliere Aggiungi/Rimuovi snap-in
  * Fare doppio clic su **Certificati**, selezionare l'**account computer** e fare clic su **Avanti**.
  * Selezionare **Computer locale**, fare clic su **Fine** e fare clic su **Ok**.
  * Espandere **Certificati (computer locale)**.
  * Espandere **Autorità di certificazione radice attendibili** e selezionare **Certificati**
    * Controllare in questo elenco i certificati radice necessari.
  * Espandere **Autorità di certificazione intermedie** e selezionare **Certificati**
    * Controllare in questo elenco i certificati intermedi obbligatori.
* Fare clic su File e scegliere Aggiungi/Rimuovi snap-in
  * Fare doppio clic su **Certificati**, selezionare **Account utente**, fare clic su **Fine** e su **OK**.
  * Espandere **Certificati - Utente corrente**
  * Espandere **Autorità di certificazione intermedie** e selezionare **Certificati**
    * Controllare in questo elenco i certificati intermedi obbligatori.
    
Se i nomi dei certificati non sono presenti nelle colonne **Rilasciato a**, è necessario installare i certificati.  Se un certificato intermedio è presente solo nell'archivio certificati intermedi **Utente corrente**, è disponibile solo per l'utente connesso e potrebbe essere necessario installarlo per altri utenti.

## <a name="install-visual-studio"></a>Installare Visual Studio
Dopo aver installato i certificati, la distribuzione di Visual Studio può procedere offline senza altri passaggi speciali seguendo [queste istruzioni](create-a-network-installation-of-visual-studio.md#deploying-from-a-network-installation).


## <a name="see-also"></a>Vedere anche
* [Installare Visual Studio](install-visual-studio.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)

