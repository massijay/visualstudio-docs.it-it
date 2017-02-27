---
title: "Helper SDK per il debug | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "dbgmetric.lib"
  - "Registro di sistema, Debugging SDK"
  - "Debug SDK, i percorsi del Registro di sistema"
  - "dbgmetric.h"
  - "metriche [Debugging SDK]"
ms.assetid: 80a52e93-4a04-4ab2-8adc-a7847c2dc20b
caps.latest.revision: 28
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 28
---
# Helper SDK per il debug
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Queste funzioni e dichiarazioni sono funzioni di supporto globali per implementare i motori di debug, analizzatori di espressioni e i provider dei simboli in C\+\+.  
  
> [!NOTE]
>  Non sono disponibili versioni gestite di queste funzioni e dichiarazioni attualmente.  
  
## Panoramica  
 In modo che i motori di debug, analizzatori di espressioni e i provider del simbolo da utilizzare in Visual Studio, devono essere registrati.  Questa operazione viene eseguita impostando le sottochiavi del Registro di sistema e le voci in caso contrario, è nota come “metriche dell'impostazione.„ Le seguenti funzioni globali sono progettate per semplificare il processo di aggiornamento di queste metriche.  Vedere la sezione sul percorso del Registro Di Sistema per ottenere il layout di ciascuna sottochiave del Registro di sistema che viene aggiornata da queste funzioni.  
  
## Funzioni metrica generali  
 Queste funzioni vengono generali utilizzate dai motori di debug.  Le funzioni specializzate per gli analizzatori di espressioni e i provider dei simboli sono successivi dettagliato.  
  
### metodo di GetMetric  
 Recupera un valore metrica dal Registro di sistema.  
  
```cpp#  
HRESULT GetMetric(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   DWORD * pdwValue,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|pszMachine|\[in\]  Il nome probabilmente di un computer remoto che il log verrà scritto \(`NULL` indica il computer locale.|  
|pszType|\[in\]  Uno dei tipi metrici.|  
|guidSection|\[in\]  GUID di un modulo, di un analizzatore, di un'eccezione, e così via. specifici.  Consente di specificare una sottosezione in un tipo metrica per un elemento specifico.|  
|pszMetric|\[in\]  La metrica da ottenere.  Corrisponde al nome di un valore specifico.|  
|pdwValue|\[in\]  Il percorso di archiviazione del valore dalla metrica.  Esistono diverse versioni di GetMetric che possono restituire un DWORD \(come in questo esempio, un BSTR, un GUID, o una matrice di GUID.|  
|pszAltRoot|\[in\]  La directory radice del Registro di sistema C\/C\+\+ da utilizzare.  Impostare su `NULL` per utilizzare l'impostazione predefinita.|  
  
### metodo di SetMetric  
 Imposta il valore " specificato nel Registro di sistema.  
  
```cpp#  
HRESULT SetMetric(  
         LPCWSTR pszType,  
         REFGUID guidSection,  
         LPCWSTR pszMetric,  
   const DWORD   dwValue,  
         bool    fUserSpecific,  
         LPCWSTR pszAltRoot  
);  
```  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|pszType|\[in\]  Uno dei tipi metrici.|  
|guidSection|\[in\]  GUID di un modulo, di un analizzatore, di un'eccezione, e così via. specifici.  Consente di specificare una sottosezione in un tipo metrica per un elemento specifico.|  
|pszMetric|\[in\]  La metrica da ottenere.  Corrisponde al nome di un valore specifico.|  
|dwValue|\[in\]  Il percorso di archiviazione del valore in ".  Esistono diverse versioni di SetMetric che possono archiviare un DWORD \(in questo esempio, un BSTR, un GUID, o una matrice di GUID.|  
|fUserSpecific|\[in\]  TRUE se la metrica è specifico dell'utente e se è scritto nell'hive dell'utente anziché dell'hive del computer locale.|  
|pszAltRoot|\[in\]  La directory radice del Registro di sistema C\/C\+\+ da utilizzare.  Impostare su `NULL` per utilizzare l'impostazione predefinita.|  
  
### metodo di RemoveMetric  
 Rimuove la metrica specificato dal Registro di sistema.  
  
```cpp#  
HRESULT RemoveMetric(  
   LPCWSTR pszType,  
   REFGUID guidSection,  
   LPCWSTR pszMetric,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|pszType|\[in\]  Uno dei tipi metrici.|  
|guidSection|\[in\]  GUID di un modulo, di un analizzatore, di un'eccezione, e così via. specifici.  Consente di specificare una sottosezione in un tipo metrica per un elemento specifico.|  
|pszMetric|\[in\]  La metrica da rimuovere.  Corrisponde al nome di un valore specifico.|  
|pszAltRoot|\[in\]  La directory radice del Registro di sistema C\/C\+\+ da utilizzare.  Impostare su `NULL` per utilizzare l'impostazione predefinita.|  
  
### metodo di EnumMetricSections  
 Enumera le diverse sezioni metrica nel Registro di sistema.  
  
```cpp#  
HRESULT EnumMetricSections(  
   LPCWSTR pszMachine,  
   LPCWSTR pszType,  
   GUID *  rgguidSections,  
   DWORD * pdwSize,  
   LPCWSTR pszAltRoot  
);  
```  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|pszMachine|\[in\]  Il nome probabilmente di un computer remoto che il log verrà scritto \(`NULL` indica il computer locale.|  
|pszType|\[in\]  Uno dei tipi metrici.|  
|rgguidSections|\[in, out\]  Matrice preallocata dei GUID da riempire.|  
|pdwSize|\[in\]  Il numero massimo di GUID che possono essere archiviati nella matrice di `rgguidSections` .|  
|pszAltRoot|\[in\]  La directory radice del Registro di sistema C\/C\+\+ da utilizzare.  Impostare su `NULL` per utilizzare l'impostazione predefinita.|  
  
## Funzioni dell'analizzatore di espressioni  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|GetEEMetric|Recupera un valore metrica dal Registro di sistema.|  
|SetEEMetric|Imposta il valore " specificato nel Registro di sistema.|  
|RemoveEEMetric|Rimuove la metrica specificato dal Registro di sistema.|  
|GetEEMetricFile|Ottiene un nome file dalla metrica e dai caricamenti specificati, restituendo il contenuto del file come stringa.|  
  
## funzioni di eccezione  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|GetExceptionMetric|Recupera un valore metrica dal Registro di sistema.|  
|SetExceptionMetric|Imposta il valore " specificato nel Registro di sistema.|  
|RemoveExceptionMetric|Rimuove la metrica specificato dal Registro di sistema.|  
|RemoveAllExceptionMetrics|Rimozione delle metriche di eccezione dal Registro di sistema.|  
  
## Funzioni del provider dei simboli  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|GetSPMetric|Recupera un valore metrica dal Registro di sistema.|  
|SetSPMetric|Imposta il valore " specificato nel Registro di sistema.|  
|RemoveSPMetric|Rimuove la metrica specificato dal Registro di sistema.|  
  
## funzioni di enumerazione  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|EnumMetricSections|Enumera tutte le metriche per un tipo metrica specificato.|  
|EnumDebugEngine|enumera i motori di debug registrati.|  
|EnumEEs|enumera gli analizzatori di espressioni registrati.|  
|EnumExceptionMetrics|Enumera tutte le metriche di eccezione.|  
  
## Definizioni metrica  
 queste definizioni possono essere utilizzate per i nomi metrici predefiniti.  I nomi corrispondono alle varie chiavi del Registro di sistema e nomi di valore e sono tutti definiti come stringhe di caratteri estesi: ad esempio, `extern LPCWSTR metrictypeEngine`.  
  
|tipi metrici predefiniti|descrizione: La chiave di base per la directory….|  
|------------------------------|-------------------------------------------------------|  
|metrictypeEngine|Tutta la metrica del motore di debug.|  
|più metrictypePortSupplier|Tutta la metrica del fornitore di porte.|  
|metrictypeException|tutta la metrica di eccezione.|  
|metricttypeEEExtension|Tutte le estensioni dell'analizzatore di espressioni.|  
  
|Proprietà del motore di debug|Descrizione|  
|-----------------------------------|-----------------|  
|metricAddressBP|Impostare su diverso da zero per indicare supporto per i punti di interruzione di indirizzo.|  
|metricAlwaysLoadLocal|Impostare su diverso da zero per caricare sempre il motore di debug locale.|  
|metricLoadInDebuggeeSession|NOT UTILIZZATO|  
|metricLoadedByDebuggee|Impostare su diverso da zero per indicare che il motore di debug verrà caricata sempre con o dal programma sottoposto a debug.|  
|metricAttach|Impostare su diverso da zero per indicare supporto per associato ai programmi esistenti.|  
|metricCallStackBP|Impostare su diverso da zero per indicare supporto per i punti di interruzione dello stack di chiamate.|  
|metricConditionalBP|Impostare su diverso da zero per indicare supporto per l'impostazione dei punti di interruzione.|  
|metricDataBP|Impostare su diverso da zero per indicare supporto per l'impostazione dei punti di interruzione sulle modifiche apportate ai dati.|  
|metricDisassembly|Impostare su diverso da zero per indicare supporto per l'elaborazione in un elenco di disassembly.|  
|metricDumpWriting|Impostare su diverso da zero per indicare supporto per la scrittura di un dump \(eseguire il dump della memoria in una periferica di output\).|  
|metricENC|Impostare su diverso da zero per indicare supporto per la Modifica e continuazione. **Note:**  Il modulo di debug personalizzato opportuno non impostare mai questo o può impostarlo sempre a 0.|  
|metricExceptions|Impostare su diverso da zero per indicare supporto per le eccezioni.|  
|metricFunctionBP|Impostare su diverso da zero per indicare supporto per i punti di interruzione denominati \(punti di interruzione che interrompono quando un determinato nome di funzione viene chiamato\).|  
|metricHitCountBP|Impostare su diverso da zero per indicare supporto dell'impostazione “punti di interruzione di riga eseguita„ \(punti di interruzione che sono attivati solo dopo sia premuto un determinato numero di volte\).|  
|metricJITDebug|Impostare su diverso da zero per indicare supporto per il debug JIT \(il debugger viene attivato quando si verifica un'eccezione in un processo in esecuzione\).|  
|metricMemory|NOT UTILIZZATO|  
|più metricPortSupplier|Impostare questa opzione sul CLSID del fornitore di porte se si è implementato.|  
|metricRegisters|NOT UTILIZZATO|  
|metricSetNextStatement|Impostare su diverso da zero per indicare il supporto per impostare l'istruzione successiva \(che ignora l'esecuzione di istruzioni intermedi\).|  
|metricSuspendThread|Impostare su diverso da zero per indicare supporto per sospendere l'esecuzione del thread.|  
|metricWarnIfNoSymbols|Impostare su diverso da zero per indicare che l'utente deve essere notificata se non sono presenti simboli.|  
|metricProgramProvider|Impostare questa opzione sul CLSID del provider del programma.|  
|metricAlwaysLoadProgramProviderLocal|Impostare questa opzione su diverso da zero per indicare che il provider del programma deve essere caricato sempre localmente.|  
|metricEngineCanWatchProcess|Impostare questa opzione su diverso da zero per indicare che il motore di debug verificherà per gli eventi gestiti anziché provider del programma.|  
|metricRemoteDebugging|Impostare questa opzione su diverso da zero per indicare il supporto per il debug remoto.|  
|metricEncUseNativeBuilder|Impostare questa opzione su diverso da zero per indicare che l'amministratore di Modifica e continuazione deve utilizzare il encbuild.dll del motore di debug per la compilazione per la Modifica e continuazione. **Note:**  Il modulo di debug personalizzato opportuno non impostare mai questo o può impostarlo sempre a 0.|  
|metricLoadUnderWOW64|Impostare questa opzione su diverso da zero per indicare che il motore di debug deve essere caricato nel processo oggetto del debug nel WOW quando si esegue il debug di un processo a 64 bit; in caso contrario, il motore di debug verrà caricato nel processo di Visual Studio \(in esecuzione in WOW64.|  
|metricLoadProgramProviderUnderWOW64|Impostare questa opzione su diverso da zero per indicare che il provider del programma deve essere caricato nel processo oggetto del debug durante il debug di un processo a 64 bit in l WOW; in caso contrario, verrà caricato nel processo di Visual Studio.|  
|metricStopOnExceptionCrossingManagedBoundary|Impostare questa opzione su diverso da zero per indicare che il processo verrà arrestata se viene generata un'eccezione non gestita attraverso i limiti codice non gestito e gestiti.|  
|metricAutoSelectPriority|Impostare questa proprietà su una priorità per la selezione automatica del motore di debug \(i valori superiori è uguale alla priorità più alta\).|  
|metricAutoSelectIncompatibleList|Chiave del Registro di sistema che contiene le voci che specificano i GUID per i motori di debug vengono ignorate nella selezione automatica.  Queste voci a un numero \(0, 1, 2 e così via, con un GUID espresso come stringa.|  
|metricIncompatibleList|Chiave del Registro di sistema che contiene le voci che specificano i GUID per i motori di debug non compatibili con il motore di debug.|  
|metricDisableJITOptimization|Impostare questa opzione su diverso da zero per indicare che le ottimizzazioni JIT \(per il codice gestito\) devono essere disabilitate durante il debug.|  
  
|Proprietà dell'analizzatore di espressioni|Descrizione|  
|------------------------------------------------|-----------------|  
|metricEngine|Ciò viene utilizzato il numero dei motori di debug che supportano l'analizzatore di espressioni specificato.|  
|metricPreloadModules|Impostare questa opzione su diverso da zero per indicare che i moduli devono essere precaricati quando un analizzatore di espressioni viene avviato con un programma.|  
|metricThisObjectName|Impostare questo parametro su “this„ nome dell'oggetto.|  
  
|Proprietà dell'analizzatore di espressioni|Descrizione|  
|------------------------------------------------|-----------------|  
|metricExtensionDll|Nome della DLL che supporta questa estensione.|  
|metricExtensionRegistersSupported|Elenco dei registri supportati.|  
|metricExtensionRegistersEntryPoint|Punto di ingresso per accedere ai registri.|  
|metricExtensionTypesSupported|Elenco dei tipi supportati.|  
|metricExtensionTypesEntryPoint|Punto di ingresso per accedere ai tipi.|  
  
|Proprietà del fornitore di porte|Descrizione|  
|--------------------------------------|-----------------|  
|metricPortPickerCLSID|Il CLSID della selezione delle porte \(una finestra di dialogo che l'utente può utilizzare per selezionare le porte e aggiungere le porte da utilizzare per eseguire il debug.|  
|metricDisallowUserEnteredPorts|Diverso da zero se le porte utente\-immesse non possono essere aggiunti al fornitore di porte \(questo rende la finestra di dialogo porta\-raccoglitrice essenzialmente di sola lettura\).|  
|metricPidBase|L'ID processo di base utilizzati dal fornitore di porte quando allocano gli ID processo.|  
  
|Tipi predefiniti dell'archivio di SP|Descrizione|  
|------------------------------------------|-----------------|  
|storetypeFile|i simboli sono archiviati in un file separato.|  
|storetypeMetadata|i simboli sono archiviati come metadati in un assembly.|  
  
|Proprietà diverse|Descrizione|  
|-----------------------|-----------------|  
|metricShowNonUserCode|Impostare questa opzione su diverso da zero per visualizzare il codice non di utente.|  
|metricJustMyCodeStepping|Impostare questa opzione su diverso da zero per indicare che avanzare può verificarsi solo nel codice utente.|  
|metricCLSID|CLSID per un oggetto di un tipo metrica specifico.|  
|metricName|Nome descrittivo per un oggetto di un tipo metrica specifico.|  
|metricLanguage|Nome della lingua.|  
  
## Percorsi del Registro Di Sistema  
 Le metriche viene letta da e viene scritto nel Registro di sistema, in particolare nella sottochiave di `VisualStudio` .  
  
> [!NOTE]
>  Per la maggior parte dei casi, la metrica verrà scritta nella chiave HKEY\_LOCAL\_MACHINE.  Talvolta, HKEY\_CURRENT\_USER verrà la chiave di destinazione.  Dbgmetric.lib gestisce entrambe le chiavi.  Recupero metrica, cerca HKEY\_CURRENT\_USER innanzitutto, quindi HKEY\_LOCAL\_MACHINE.  Quando viene impostato metrica, un parametro specifica che chiave di primo livello da utilizzare.  
  
 *\[chiave del Registro di sistema\]*\\  
  
 `Software`\\  
  
 `Microsoft`\\  
  
 `VisualStudio`\\  
  
 *\[radice della versione\]*\\  
  
 *\[radice metriche\]*\\  
  
 *\[tipo "\]*\\  
  
 *\["\] \= \[valore "\]*  
  
 *\["\] \= \[valore "\]*  
  
 *\["\] \= \[valore "\]*  
  
|Placeholder|Descrizione|  
|-----------------|-----------------|  
|*\[chiave del Registro di sistema\]*|`HKEY_CURRENT_USER` o `HKEY_LOCAL_MACHINE`.|  
|*\[radice della versione\]*|La versione di Visual Studio, ad esempio `7.0`, `7.1`, o `8.0`\).  Tuttavia, questa radice può essere modificata utilizzando l'opzione di**\/rootsuffix** a **devenv.exe**.  Per il VSIP, questo modificatore è in genere Esp, in modo dalla radice della versione potrebbe, ad esempio, 8.0Exp.|  
|*\[radice metriche\]*|Si tratta di `AD7Metrics` o `AD7Metrics(Debug)`, a seconda che la versione di debug di dbgmetric.lib viene utilizzata. **Note:**  Indipendentemente dal fatto che dbgmetric.lib viene utilizzato, questa convenzione di denominazione deve essere aderita se si dispone di differenze tra versioni di debug e di rilascio che devono essere riprodotti nel Registro di sistema.|  
|*\[tipo "\]*|Il tipo di metrica da scrivere: `Engine`, `ExpressionEvaluator`, `SymbolProvider`, e così via.  Questi sono tutti definiti come in dbgmetric.h come, dove è il nome del tipo specifico.|  
|*\[\] "*|Il nome di una voce da assegnare un valore per impostare la metrica.  Effettiva organizzazione della metrica dipende dal tipo ".|  
|*\[valore "\]*|Il valore assegnato a ".  Il tipo che il valore deve avere \(stringa, numero, e così via. dipende dalla metrica.|  
  
> [!NOTE]
>  Tutti i GUID vengono archiviati in formato di `{GUID}`.  Ad esempio `{123D150B-FA18-461C-B218-45B3E4589F9B}`.  
  
### I motori di debug  
 Ecco l'organizzazione della metrica dei motori di debug nel Registro di sistema.  `Engine` è il nome del tipo metrica per il modulo di debug e corrisponde a *\[tipo "\]* nel sottoalbero di sopra del Registro di sistema.  
  
 `Engine`\\  
  
 *\[guid del motore\]*\\  
  
 `CLSID` \= *\[guid della classe\]*  
  
 *\["\] \= \[valore "\]*  
  
 *\["\] \= \[valore "\]*  
  
 *\["\] \= \[valore "\]*  
  
 `PortSupplier`\\  
  
 `0` \= *\[guid del fornitore di porte\]*  
  
 `1` \= *\[guid del fornitore di porte\]*  
  
|Placeholder|Descrizione|  
|-----------------|-----------------|  
|*\[guid del motore\]*|Il GUID del motore di debug.|  
|*\[guid della classe\]*|Il GUID della classe che implementa questo motore di debug.|  
|*\[guid del fornitore di porte\]*|Il GUID del fornitore di porte, se disponibile.  Molti motori di debug utilizzano il fornitore della porta predefinita e pertanto non specificano il proprio fornitore.  In questo caso, la sottochiave `PortSupplier` sarà presente.|  
  
### fornitori di porte  
 Ecco l'organizzazione della metrica del fornitore di porte nel Registro di sistema.  `PortSupplier` è il nome del tipo metrica per un fornitore di porte e corrisponde a *\[tipo "\]*.  
  
 `PortSupplier`\\  
  
 *\[guid del fornitore di porte\]*\\  
  
 `CLSID` \= *\[guid della classe\]*  
  
 *\["\] \= \[valore "\]*  
  
 *\["\] \= \[valore "\]*  
  
|Placeholder|Descrizione|  
|-----------------|-----------------|  
|*\[guid del fornitore di porte\]*|Il GUID del fornitore di porte|  
|*\[guid della classe\]*|Il GUID della classe che implementa il fornitore di porte|  
  
### Provider dei simboli  
 Ecco l'organizzazione della metrica del fornitore del simbolo nel Registro di sistema.  `SymbolProvider` è il nome del tipo metrica per il provider del simbolo e corrisponde a *\[tipo "\]*.  
  
 `SymbolProvider`\\  
  
 *\[GUID del provider del simbolo\]*\\  
  
 `file`\\  
  
 `CLSID` \= *\[guid della classe\]*  
  
 *\["\] \= \[valore "\]*  
  
 *\["\] \= \[valore "\]*  
  
 `metadata`\\  
  
 `CLSID` \= *\[guid della classe\]*  
  
 *\["\] \= \[valore "\]*  
  
 *\["\] \= \[valore "\]*  
  
|Placeholder|Descrizione|  
|-----------------|-----------------|  
|*\[GUID del provider del simbolo\]*|Il GUID del provider dei simboli|  
|*\[guid della classe\]*|Il GUID della classe che implementa questo provider dei simboli|  
  
### analizzatori di espressioni  
 Ecco l'organizzazione della metrica dell'analizzatore di espressioni nel Registro di sistema.  `ExpressionEvaluator` è il nome del tipo metrica per l'analizzatore di espressioni e corrisponde a *\[tipo "\]*.  
  
> [!NOTE]
>  Il tipo metrica per `ExpressionEvaluator` non è definito in dbgmetric.h, così come si presuppone che tutte le modifiche metrica per gli analizzatori di espressioni passeranno con le funzioni metrica dell'analizzatore di espressioni appropriato \(il layout della sottochiave di `ExpressionEvaluator` è piuttosto complessa, pertanto i dettagli vengono nascosti in dbgmetric.lib\).  
  
 `ExpressionEvaluator`\\  
  
 *\[guid del linguaggio\]*\\  
  
 *\[guid del fornitore\]*\\  
  
 `CLSID` \= *\[guid della classe\]*  
  
 *\["\] \= \[valore "\]*  
  
 *\["\] \= \[valore "\]*  
  
 `Engine`\\  
  
 `0` \= *\[guid del motore di debug\]*  
  
 `1` \= *\[guid del motore di debug\]*  
  
|Placeholder|Descrizione|  
|-----------------|-----------------|  
|*\[guid del linguaggio\]*|Il GUID di un linguaggio|  
|*\[guid del fornitore\]*|Il GUID di un fornitore|  
|*\[guid della classe\]*|Il GUID della classe che implementa questo analizzatore di espressioni|  
|*\[guid del motore di debug\]*|Il GUID del modulo di debug cui l'analizzatore di espressioni interagisce con|  
  
### Estensioni dell'analizzatore di espressioni  
 Ecco l'organizzazione della metrica dell'analizzatore di espressioni nel Registro di sistema.  `EEExtensions` è il nome del tipo metrica per le estensioni dell'analizzatore di espressioni e corrisponde a *\[tipo "\]*.  
  
 `EEExtensions`\\  
  
 *\[guid\] di estensione*\\  
  
 *\["\] \= \[valore "\]*  
  
 *\["\] \= \[valore "\]*  
  
|Placeholder|Descrizione|  
|-----------------|-----------------|  
|*\[guid\] di estensione*|Il GUID di un'estensione dell'analizzatore di espressioni|  
  
### Eccezioni  
 Ecco l'organizzazione della metrica di eccezioni nel Registro di sistema.  `Exception` è il nome del tipo metrica per le eccezioni e corrisponde a *\[tipo "\]*.  
  
 `Exception`\\  
  
 *\[guid del motore di debug\]*\\  
  
 *\[tipi di eccezione\]*\\  
  
 *\[eccezione\]*\\  
  
 *\["\] \= \[valore "\]*  
  
 *\["\] \= \[valore "\]*  
  
 *\[eccezione\]*\\  
  
 *\["\] \= \[valore "\]*  
  
 *\["\] \= \[valore "\]*  
  
|Placeholder|Descrizione|  
|-----------------|-----------------|  
|*\[guid del motore di debug\]*|Il GUID del modulo di debug che supporta le eccezioni.|  
|*\[tipi di eccezione\]*|un titolo generale per la sottochiave che identifica la classe di eccezioni che possono essere gestite.  I nomi comuni sono **C\+\+ Exceptions**, **Win32 Exceptions**, **Common Language Runtime Exceptions**e **Native Run\-Time Checks**.  Tali nomi vengono inoltre utilizzati per identificare una particolare classe di eccezione all'utente.|  
|*\[eccezione\]*|un nome per un'eccezione: ad esempio, **\_com\_error** o **Control\-Break**.  Tali nomi vengono utilizzati per identificare una particolare eccezione all'utente.|  
  
## Requisiti  
 Questi file si trovano nella directory di installazione di [!INCLUDE[vs_dev10_ext](../../../extensibility/debugger/reference/includes/vs_dev10_ext_md.md)] SDK \(per impostazione predefinita, *\[unità\]*\\Program Files\\Microsoft Visual Studio 2010 SDK \\\).  
  
 intestazione: include \\ dbgmetric.h  
  
 raccolta: librerie \\ ad2de.lib, librerie \\ dbgmetric.lib  
  
## Vedere anche  
 [Riferimento API](../../../extensibility/debugger/reference/api-reference-visual-studio-debugging.md)