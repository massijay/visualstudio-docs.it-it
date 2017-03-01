---
title: "Procedura: eseguire la migrazione di progetti di estendibilità di Visual Studio 2017 | Documenti di Microsoft"
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ca07b00-a3ff-40ab-b647-c0a93b55e86a
caps.latest.revision: 1
author: gregvanl
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
ms.sourcegitcommit: 09f14e5b28a506d4f2112f82ee4fd6b0855a8f93
ms.openlocfilehash: 67e143e1b95a0e4d881d7d6bccae0d7445897aa2
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-migrate-extensibility-projects-to-visual-studio-2017"></a>Procedura: eseguire la migrazione di progetti di estendibilità di Visual Studio 2017

>**Nota:** questa documentazione è preliminare e in base alla versione di Visual Studio 2017 RC.

In questo documento viene illustrato come aggiornare i progetti di estendibilità di Visual Studio 2017. Oltre a descrivere come aggiornare i file di progetto, viene inoltre descritto come eseguire l'aggiornamento dalla versione del manifesto dell'estensione 2 (VSIX v2) per il nuova versione 3 del manifesto formato VSIX (VSIX v3).

## <a name="install-visual-studio-2017-rc-with-required-workloads"></a>Installare Visual Studio 2017 RC con carichi di lavoro richiesti

Verificare che l'installazione include carichi di lavoro seguenti:

* Sviluppo di applicazioni desktop
* Sviluppo di estensioni di Visual Studio

## <a name="open-vsix-solution-in-visual-studio-2017"></a>Aprire la soluzione VSIX in Visual Studio 2017

Tutti i progetti VSIX richiederanno un aggiornamento unidirezionale di versione principale di Visual Studio 2017.

Il file di progetto (ad esempio *. csproj) verrà aggiornato:

* MinimumVisualStudioVersion - ora impostato su 15.0
* OldToolsVersion (se esiste già)-ora impostato su 14.0

## <a name="update-the-microsoftvssdkbuildtools-nuget-package"></a>Aggiornare il pacchetto Microsoft.VSSDK.BuildTools NuGet

>**Nota:** se la soluzione non fa riferimento il pacchetto Microsoft.VSSDK.BuildTools NuGet, è possibile ignorare questo passaggio.

Per compilare l'estensione nella nuova v3 VSIX formato (versione 3), è necessario compilare con i nuovi strumenti di compilazione VSSDK la soluzione. Verrà installata con Visual Studio RC 2017, ma l'estensione v2 VSIX potrebbe contenere un riferimento a una versione precedente tramite NuGet. In questo caso, è necessario installare manualmente un aggiornamento del pacchetto Microsoft.VSSDK.BuildTools NuGet per la soluzione. Al momento della versione RC, questo pacchetto sarà in stato "Versione preliminare".

Per aggiornare i riferimenti NuGet Microsoft.VSSDK.BuildTools:

* Fare clic sulla soluzione e scegliere **Manage NuGet Packages for Solution...**
* Individuare il **aggiornamenti** scheda.
* Selezionare la casella per **Includi versione preliminare**.
* Selezionare Microsoft.VSSDK.BuildTools (versione più recente).
* Premere **aggiornamento**.

![Strumenti di compilazione VSSDK](media/vssdk-build-tools.png)

>**Nota:** la schermata mostra una versione diversa di BuildTools. Selezionare la versione RC.

## <a name="make-changes-to-the-vsix-extension-manifest"></a>Apportare le modifiche al manifesto dell'estensione VSIX

Per garantire che l'installazione dell'utente di Visual Studio ha tutti gli assembly necessari per eseguire l'estensione, specificare tutti i componenti dei prerequisiti o i pacchetti nel file manifesto dell'estensione. Quando un utente tenta di installare l'estensione, il VSIXInstaller controllerà per verificare se tutti i prerequisiti sono installati. Se mancano alcuni nodi, l'utente verrà richiesto di installare i componenti mancanti come parte del processo di installazione di estensione.

* Modificare il file manifesto dell'estensione (in genere chiamato source.extension.vsixmanifest).
* Verificare `InstallationTarget` include 15.0.
* Aggiungere i prerequisiti di installazione richiesti (come illustrato nell'esempio riportato di seguito).
  * È consigliabile che specificare solo gli ID componente dei prerequisiti.
  * Vedere la sezione alla fine di questo documento per [istruzioni su come identificare gli ID componente](#finding-component-ids).

Esempio:

```xml
<PackageManifest>
 ...
    <Prerequisites>
        <Prerequisite Id="Microsoft.VisualStudio.Component.CoreEditor" Version="[15.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Component.DiagnosticTools" Version="[15.0.25814.0,16.0)" />
        <Prerequisite Id="Microsoft.VisualStudio.Shell.12.0" Version="[12.0]" />
    </Prerequisites>
 ...
</PackageManifest>
```

### <a name="option-use-the-designer-to-make-changes-to-the-vsix-extension-manifest"></a>Opzione: Utilizzare la finestra di progettazione per apportare modifiche al manifesto dell'estensione VSIX

Invece di modificare direttamente il XML del manifesto, è possibile utilizzare il nuovo **prerequisiti** scheda nella finestra di progettazione manifesto per selezionare i prerequisiti e il codice XML verrà aggiornata automaticamente.

>**Nota:** progettazione manifesto solo consentirà di selezionare i componenti (non i carichi di lavoro o pacchetti) che vengono installati nell'istanza corrente di Visual Studio. Se è necessario aggiungere un prerequisito per un carico di lavoro, un pacchetto o un componente che non è attualmente installato, è possibile modificare direttamente il manifesto XML.

* Aprire il file source.extension.vsixmanifest [Progettazione].
* Selezionare **prerequisiti** scheda e premere **New** pulsante.

  ![Progettazione manifesto VSIX](media/vsix-manifest-designer.png)

* Il **aggiungere nuovi prerequisiti** aprirà la finestra.

  ![aggiungere il prerequisito vsix](media/add-vsix-prerequisite.png)

* Fare clic sull'elenco a discesa per **nome** e selezionare il prerequisito desiderato.
* Aggiornare la versione, se necessario.

  >Nota: Il campo versione sarà già popolato con la versione del componente attualmente installato, con un intervallo che si estende su fino a (ma non inclusi) la successiva versione principale del componente.

  ![aggiungere il prerequisito di roslyn](media/add-roslyn-prerequisite.png)

* Press **OK**.

## <a name="if-migrating-from-preview-4-or-preview-5"></a>Se la migrazione da Anteprima 4 o 5 Preview

* Sostituire `SetupDependencies` con `Prerequisites` e spostare gli elementi fuori il `Installer` elemento. `Prerequisites`ora risiede direttamente all'interno di `PackageManifest` elemento.
* [Facoltativo] Rimuovere il `GenerateVsixV3` elemento. (Questo è stato richiesto in anteprima 5 solo). Il `GenerateVsixV3` elemento verrà ignorato nelle versioni superiori a 5 di anteprima.

## <a name="update-debug-settings-for-project"></a>Aggiornare le impostazioni di Debug per progetto

Se si desidera eseguire il debug dell'estensione in un'istanza sperimentale di Visual Studio, assicurarsi che le impostazioni di progetto per **Debug** > **azione di avvio** ha il **Avvia programma esterno:** valore impostato per il file devenv.exe dell'installazione di Visual Studio 2017.

Potrebbe essere simile:

```
C:\Program Files (x86)\Microsoft Visual Studio\2017\Enterprise\Common7\IDE\devenv.exe
```

![Avvia programma esterno](media/start-external-program.png)

>**Nota:** l'azione di avviare il Debug è in genere archiviato nel. csproj file. Questo file è in genere inclusa nel file con estensione gitignore e, di conseguenza, non viene in genere salvato con altri file di progetto quando vengono salvate nel controllo del codice sorgente. Di conseguenza, se si è estratti la soluzione aggiornata dal controllo del codice sorgente è probabile che il progetto non sarà necessario alcun valori impostati per l'azione di avvio. I nuovi progetti VSIX creati con Visual Studio 2017 avrà un. csproj file creato con le impostazioni predefinite che punta alla directory di installazione di Visual Studio corrente. Tuttavia se si esegue la migrazione di un'estensione VSIX v2, è probabile che il. csproj file conterrà i riferimenti a directory di installazione della versione di Visual Studio precedente. Impostazione del valore di **Debug** > **azione di avvio** consentirà l'istanza sperimentale di Visual Studio corretto da avviare quando si tenta di eseguire il debug dell'estensione.

## <a name="check-that-the-extension-builds-correctly-as-a-vsix-v3"></a>Verificare che l'estensione venga compilata correttamente (in un progetto VSIX versione&3;)

* Compilare il progetto VSIX.
* Decomprimere il progetto VSIX generato.
  * Per impostazione predefinita, la vita file VSIX in bin/Debug o bin/Release come VSIX [YourCustomExtension].
  * Rinominare VSIX come ZIP visualizzare facilmente il contenuto.
* Verificare l'esistenza di tre file:
  * Extension. vsixmanifest
  * manifest
  * Catalog.JSON

## <a name="check-when-all-required-prerequisites-are-installed"></a>Controllare se sono installati tutti i prerequisiti necessari

Verificare che il progetto VSIX viene installato correttamente in un computer con i prerequisiti necessari.

>**Nota:** prima di installare qualsiasi estensione, chiudere tutte le istanze di Visual Studio.

Tenta di installare l'estensione:

* In Visual Studio 2017 RC

![Programma di installazione VSIX in Visual Studio 2017](media/vsixinstaller-vs-2017.png)

* Facoltativo: Controllare le versioni precedenti di Visual Studio.
  * Prova di compatibilità con le versioni precedenti.
  * Dovrebbe funzionare per Visual Studio 2012, Visual Studio 2013, Visual Studio 2015.
* Facoltativo: Verificare che il controllo di versione programma di installazione di VSIX offre una gamma di versioni.
  * Include le versioni precedenti di Visual Studio (se installato).
  * Include Visual Studio 2017 RC.

Se Visual Studio è stato aperto di recente, è possibile visualizzare una finestra di dialogo simile alla seguente:

![processi in esecuzione Visual Studio](media/vs-running-processes.png)

Attendere l'arresto dei processi o terminare manualmente le attività. È possibile trovare i processi dal nome elencato o con il PID elencati tra parentesi.

>**Nota:** questi processi non verranno automaticamente arrestata durante l'esecuzione di un'istanza di Visual Studio. Assicurarsi di aver chiuso tutte le istanze di Visual Studio nel computer, compresi quelli di altri utenti, quindi continuare a provare.

## <a name="check-when-missing-the-required-prerequisites"></a>Verificare se mancano i prerequisiti necessari

* Tenta di installare l'estensione in un computer con Visual Studio 2017 RC che non contengono tutti i componenti definiti nei prerequisiti (sopra).
* Verificare che l'installazione identifica il componente mancante/s e li elenca come prerequisito nel VSIXInstaller.
* Nota: L'elevazione dei privilegi è richiesto se tutti i prerequisiti devono essere installati con l'estensione.

![Prerequisito mancante vsixinstaller](media/vsixinstaller-missing-prerequisite.png)

## <a name="deciding-on-components"></a>Scelta di componenti

Quando si cercano le dipendenze, si noterà che una dipendenza può eseguire il mapping di più componenti. Per determinare le dipendenze è necessario specificare il prerequisito, è consigliabile che si sceglie un componente che dispone di una funzionalità simile all'estensione e per considerare anche gli utenti e il tipo di componenti sarebbe probabilmente installati o non è presente l'installazione. Si consiglia anche di creazione delle estensioni in un modo in cui i prerequisiti necessari soddisfano solo il valore minimo che consente l'estensione per l'esecuzione e per le funzionalità aggiuntive siano inattivi se alcuni componenti non vengono rilevati.

Per fornire ulteriori indicazioni, abbiamo identificato alcuni tipi di estensione comuni e sui relativi prerequisiti suggeriti:

Tipo di estensione | Nome visualizzato |    Id
--- | --- | ---
Editor | Editor di Visual Studio core    | Microsoft.VisualStudio.CoreEditor
Roslyn | C# e Visual Basic | Microsoft.VisualStudio.Component.Roslyn.LanguageServices
WPF | Componenti di base del carico di lavoro Desktop gestiti | Microsoft.VisualStudio.Component.ManagedDesktop.Core
Debugger | Debugger-In-Time | Microsoft.VisualStudio.Component.Debugger.JustInTime

## <a name="finding-component-ids"></a>Trovare gli ID componente

L'elenco dei componenti ordinati in base al prodotto di Visual Studio è [il carico di lavoro di Visual Studio 2017 e gli ID componente](https://aka.ms/vs2017componentIDs). Utilizzare questi ID componente per gli ID dei prerequisiti nel manifesto.

Se non si conosce il componente contiene un download di file binari, specifico di [componente-> del foglio di calcolo di mapping dei tipi binari](https://aka.ms/vs2017componentid-binaries).

### <a name="vs2017-componentbinarymappingxlsx"></a>vs2017 ComponentBinaryMapping.xlsx

Esistono quattro colonne nel foglio di Excel: **nome componente**, **ComponentId**, **versione**, e **binario o nomi di File**.  È possibile utilizzare i filtri per cercare e trovare i file binari e componenti specifici.

Per tutti i riferimenti, stabilire quali sono nel componente principale editor (Microsoft.VisualStudio.Component.CoreEditor).  Come minimo, è necessario il componente editor principale per specificare come prerequisito per tutte le estensioni. Dei riferimenti vengono lasciato non incluse nell'editor principale, aggiungere i filtri nel **file binari o nomi di file** sezione per trovare i componenti che includono qualsiasi subset di tali riferimenti.

Esempi:

* Se si dispone di un'estensione del debugger e che il progetto ha un riferimento a VSDebugEng.dll e VSDebug.dll, fare clic sul pulsante filtro nel **file binari o nomi di file** intestazione.  Cercare "VSDebugEng.dll" e fare clic su OK.  Fare clic sul pulsante del filtro nel **file binari o nomi di file** intestazione nuovamente e cercare "VSDebug.dll".  Selezionare la casella di controllo "Aggiungi selezione corrente al filtro" e fare clic su OK.  Ora esaminare il **nome componente** per trovare un componente più correlati per il tipo di estensione. In questo esempio, scelto Just-In-Time del debugger e verrà aggiunto il vsixmanifest.
* Se si conosce che gestisce il progetto con gli elementi del debugger, è possibile cercare "debugger" nella casella di ricerca del filtro per vedere quali componenti contengono debugger nel relativo nome.
