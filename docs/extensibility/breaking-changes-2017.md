---
title: Modifiche di rilievo di extensibility di Visual Studio 2017 | Documenti di Microsoft
ms.custom: 
ms.date: 11/09/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 54d5af60-0b44-4ae1-aa57-45aa03f89f3d
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
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 2e6e4b3d9d1528d57fe181b3765e1ce3624bebad
ms.lasthandoff: 03/07/2017

---
# <a name="changes-in-visual-studio-2017-extensibility"></a>Modifiche in Visual Studio 2017 extensibility

Con Visual Studio 2017, offriamo un [veloce e leggero, esperienza di installazione di Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/04/01/faster-leaner-visual-studio-installer) che riduce l'impatto di Visual Studio nei sistemi di utente, e offre agli utenti più ampia di carichi di lavoro e le funzionalità installate. Per supportare questi miglioramenti, abbiamo apportato modifiche al modello di estendibilità e apportate alcune modifiche di rilievo di extensibility di Visual Studio. Questo documento vengono illustrati i dettagli tecnici di queste modifiche, e ciò che può essere eseguita per risolverli. Si noti che alcune informazioni rappresentano i dettagli di implementazione point-in-time e possono essere modificati in un secondo momento.

## <a name="changes-affecting-vsix-format-and-installation"></a>Modifiche che influiscono sul formato VSIX e installazione

È stato introdotto il v3 VSIX formato (versione 3) per supportare l'esperienza di installazione leggera.

Modifiche al formato VSIX includono:

* Dichiarazione dei prerequisiti di installazione. Per le promesse di un tipo semplice, veloce o l'installazione di Visual Studio, il programma di installazione offre ulteriori opzioni di configurazione per gli utenti. Di conseguenza, per assicurarsi che siano installati le funzionalità e componenti richiesti da un'estensione, le estensioni dovranno dichiarare le relative dipendenze.
  * Il programma di installazione di Visual Studio 2017 offrirà automaticamente acquisire e installare i componenti necessari per l'utente come parte dell'installazione dell'estensione.
  * Gli utenti verranno inoltre visualizzato l'avviso quando si tenta di installare un'estensione che non è stata creata utilizzando il nuovo formato v3 VSIX, anche se che sono stati contrassegnati nel relativo manifesto come destinate alla versione 15.0.
* Funzionalità avanzate per il formato VSIX. Per realizzare un [installazione basso impatto](https://blogs.msdn.microsoft.com/visualstudio/2016/04/25/anatomy-of-a-low-impact-visual-studio-install) di Visual Studio che supporta le installazioni side-by-side, abbiamo non salvare la maggior parte dei dati di configurazione nel Registro di sistema e sono stati spostati gli assembly di Visual Studio specifici dalla Global Assembly Cache. È inoltre migliorate le funzionalità del formato VSIX e motore di installazione di VSIX, che consente di utilizzare, piuttosto che un file MSI o EXE per installare le estensioni per alcuni tipi di installazione.

  Le nuove funzionalità includono:

  * Registrazione nell'istanza di Visual Studio specificato.
  * Installazione di fuori di [cartella extensions](set-install-root.md).
  * Rilevamento dell'architettura del processore.
  * Dipendenza separati language language pack.
  * Installazione con [supporto NGEN](ngen-support.md).

## <a name="building-an-extension-for-visual-studio-2017"></a>Creazione di un'estensione per Visual Studio 2017

Progettazione di strumenti per la creazione del nuovo formato del manifesto di pacchetto VSIX v3 è ora disponibile in Visual Studio 2017. Vedere il documento di accompagnamento [procedura: eseguire la migrazione di progetti di estendibilità di Visual Studio 2017](how-to-migrate-extensibility-projects-to-visual-studio-2017.md) per informazioni dettagliate su utilizzando gli strumenti di progettazione o esecuzione di aggiornamenti manuali per il progetto e il manifesto per lo sviluppo di estensioni VSIX v3.

## <a name="change-visual-studio-user-data-path"></a>Modifica: Percorso dati utente di Visual Studio

In precedenza, una singola installazione di ogni versione principale di Visual Studio può essere presenti in ogni computer. Per supportare le installazioni side-by-side di Visual Studio 2017, possono esistere più percorsi dati utente per Visual Studio sul computer dell'utente.

Il codice in esecuzione il processo di Visual Studio deve essere aggiornato per utilizzare le impostazioni di gestione di Visual Studio. Il codice in esecuzione all'esterno del processo di Visual Studio è possibile trovare il percorso di utente di una specifica installazione di Visual Studio [, seguendo le istruzioni qui](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).

## <a name="change-global-assembly-cache-gac"></a>Modifica: Global Assembly Cache (GAC)

La maggior parte delle assembly principale di Visual Studio non vengono più installati nella GAC. Le seguenti modifiche sono state apportate in modo che il codice in esecuzione nel processo di Visual Studio può ancora trovare assembly necessari in fase di esecuzione.

* Assembly installati nella GAC solo:
  * Questi assembly sono ora installati in %VsFolder%\Common7\IDE\, %VsFolder%\Common7\IDE\PublicAssemblies o % VsFolder%\Common7\IDE\PrivateAssemblies. Queste cartelle fanno parte dei percorsi di probe del processo di Visual Studio.
* Assembly installati in un percorso non sondaggio e nella Global Assembly Cache:
  * La copia nella Global Assembly Cache è stata rimossa dal programma di installazione.
  * Per specificare una voce di base di codice per l'assembly è stato aggiunto un file. pkgdef.

    Ad esempio:
    
    ```xml
    [$RootKey$\RuntimeConfiguration\dependentAssembly\codeBase\{UniqueGUID}]
    "name"="AssemblyName" "codeBase"="$PackageFolder$\AssemblyName.dll"
    "publicKeyToken"="Public Key Token"
    "culture"="neutral"
    "version"=15.0.0.0
    ```
    In fase di esecuzione, il sottosistema di Visual Studio pkgdef unirà queste voci nel file di configurazione di runtime del processo di Visual Studio (in % VsAppDataFolder%\devenv.exe.config) come [ `<codeBase>` ](https://msdn.microsoft.com/en-us/library/efs781xb(v=vs.110).aspx) elementi. Questo è il modo consigliato per consentire il processo di Visual Studio di trovare l'assembly, in quanto evita la ricerca mediante i percorsi di ricerca.

### <a name="reacting-to-this-breaking-change"></a>Reazione a questa modifica di rilievo

* Se l'estensione è in esecuzione all'interno del processo di Visual Studio:
  * Il codice sarà in grado di trovare gli assembly di base di Visual Studio.
  * È consigliabile utilizzare un file. pkgdef per specificare un percorso all'assembly, se necessario.
* Se l'estensione è in esecuzione all'esterno del processo di Visual Studio:
  * È consigliabile cercare l'assembly principale di Visual Studio in %VsFolder%\Common7\IDE\, %VsFolder%\Common7\IDE\PublicAssemblies o %VsFolder%\Common7\IDE\PrivateAssemblies mediante resolver di assembly o file di configurazione.

## <a name="change-reduce-registry-impact"></a>Modifica: Ridurre l'impatto del Registro di sistema

### <a name="global-com-registration"></a>Registrazione COM globale

* Visual Studio installati in precedenza, molte delle chiavi del Registro di sistema nell'hive HKEY_LOCAL_MACHINE e HKEY_CLASSES_ROOT per supportare la registrazione COM nativa. Per eliminare tale impatto, Visual Studio utilizza ora [attivazione senza registrazione per i componenti COM](https://msdn.microsoft.com/en-us/library/ms973913.aspx).
* Di conseguenza, la maggior parte delle TLB / OLB / i file DLL in % ProgramFiles (x86) %\Common Shared\MSEnv comuni\Microsoft non vengono più installati per impostazione predefinita da Visual Studio. Questi file sono ora installati in % VsFolder % con corrispondenti manifesti Registration-Free COM utilizzati dal processo host di Visual Studio.
* Di conseguenza, il codice esterno che si basa su una registrazione COM globale per le interfacce COM di Visual Studio non troveranno più queste registrazioni. Il codice in esecuzione il processo di Visual Studio non verrà visualizzato una differenza.

### <a name="visual-studio-registry"></a>Registro di sistema di Visual Studio

* Visual Studio installato in precedenza, molte chiavi del Registro di sistema nell'hive HKEY_LOCAL_MACHINE e HKEY_CURRENT_USER del sistema, in una chiave specifici di Visual Studio:
  * HKLM\Software\Microsoft\VisualStudio\\**versione**: le chiavi del Registro di sistema create da programmi di installazione MSI ed estensioni per i singoli computer.
  * HKCU\Software\Microsoft\VisualStudio\\**versione**: le chiavi del Registro di sistema create da Visual Studio per archiviare le impostazioni specifiche dell'utente.
  * HKCU\Software\Microsoft\VisualStudio\\**versione**_Config: una copia della chiave di Visual Studio HKLM precedente e le chiavi del Registro di sistema eseguito il merge dal file. pkgdef dalle estensioni.
* Per ridurre l'impatto sul Registro di sistema, Visual Studio utilizza ora il [RegLoadAppKey](https://msdn.microsoft.com/en-us/library/windows/desktop/ms724886(v=vs.85).aspx) funzione per archiviare le chiavi del Registro di sistema in un file binario privato in % VsAppDataFolder%\privateregistry.bin. Solo un numero molto ridotto di chiavi specifici di Visual Studio rimane nel Registro di sistema.
* Il codice esistente in esecuzione il processo di Visual Studio non è interessato. Visual Studio reindirizzerà tutte le operazioni del Registro di sistema nella chiave HKCU Visual Studio specifico nel Registro di sistema privato. Lettura e scrittura in altri percorsi del Registro di sistema continuerà a utilizzare il Registro di sistema.
* Codice esterno sarà necessario caricare e leggere da questo file per le voci del Registro di sistema di Visual Studio.

### <a name="reacting-to-this-breaking-change"></a>Reazione a questa modifica di rilievo

* Codice esterno deve essere convertito per utilizzare l'attivazione senza registrazione per anche i componenti COM.
* Componenti esterni possono individuare il percorso di Visual Studio [, seguendo le istruzioni qui](https://blogs.msdn.microsoft.com/heaths/2016/09/15/changes-to-visual-studio-15-setup).
* Si consiglia di utilizzano i componenti esterni di [esterno Settings Manager](https://msdn.microsoft.com/en-us/library/microsoft.visualstudio.settings.externalsettingsmanager.aspx) invece di lettura/scrittura direttamente alle chiavi del Registro di sistema di Visual Studio.
* Controllare se i componenti che dell'estensione utilizza hanno implementato un'altra tecnica per la registrazione. Ad esempio, le estensioni del debugger possono essere in grado di sfruttare i vantaggi del nuovo [msvsmon registrazione COM file JSON](migrate-debugger-COM-registration.md).

## <a name="change-lightweight-solution-load"></a>Modifica: Carico soluzione leggera

Semplice soluzione caricare (LSL) riduce i tempi di carico soluzione caricando non completamente progetti fino a quando l'utente inizia a lavorare con loro. Questo può influire estensioni che si supponga che un progetto è stato caricato completamente. Vedere [carico soluzione Lightweight](lightweight-solution-load-extension-impact.md) sapere se l'estensione potrebbe avere effetti e ottenere istruzioni sull'aggiornamento dell'estensione.

