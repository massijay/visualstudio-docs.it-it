---
title: "MSSCCPRJ. File SCC | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "plug-in, MSSCCPRJ controllo del codice sorgente. File SCC"
  - "MSSCCPRJ. File SCC"
ms.assetid: 6f2e39d6-b79d-407e-976f-b62a3cedd378
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# MSSCCPRJ. File SCC
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando un progetto o soluzione di Visual Studio viene inserito nel controllo del codice sorgente utilizzando l'IDE, l'IDE riceve due tipi principali di informazioni dal plug\-in forma di stringhe di controllo del codice sorgente. Queste stringhe, "AuxPath" e "Nomeprogetto", sono opache all'IDE, ma il plug\-in vengono utilizzati per individuare la soluzione o progetto nel controllo della versione. L'IDE ottiene in genere queste stringhe la prima volta tramite la chiamata di [SccGetProjPath](../extensibility/sccgetprojpath-function.md), e quindi li salva nel file di soluzione o un progetto per le chiamate successive al [SccOpenProject](../extensibility/sccopenproject-function.md). Quando incorporati nei file di soluzione e progetto, le stringhe "AuxPath" e "Nomeprogetto" non vengono aggiornate automaticamente quando un utente crea un ramo, fork, o copia i file di progetto e soluzione nel controllo della versione. Per assicurarsi che i file di soluzione e progetto puntino nella posizione corretta nel controllo della versione, gli utenti devono aggiornare manualmente le stringhe. Poiché le stringhe devono essere opaco, potrebbe non sempre essere chiaro come deve essere aggiornati.  
  
 Il plug\-in del controllo del codice sorgente è possibile evitare questo problema archiviando le stringhe "AuxPath" e "Nomeprogetto" in un file speciale denominato il MSSCCPRJ. File SCC. È un file locale, sul lato client che è di proprietà e gestito dal plug\-in. Questo file non viene mai inserito nel controllo del codice sorgente, ma non viene generato il plug\-in per ogni directory che contiene i file di controllo del codice sorgente. Per determinare quali file sono file di soluzione e progetto di Visual Studio, un plug\-in del controllo del codice sorgente possibile confrontare le estensioni di file rispetto a un elenco standard o fornito dall'utente. Una volta l'IDE rileva che un plug\-in supporta il MSSCCPRJ. File SCC, cessa di incorporare "AuxPath" e "Nomeprogetto" stringhe nella soluzione e file di progetto, quindi legge le stringhe da di MSSCCPRJ. File SCC.  
  
 Un controllo del codice sorgente del plug\-in che supporta il MSSCCPRJ. File SCC deve rispettare le linee guida seguenti:  
  
-   Può essere presente solo uno MSSCCPRJ. File di controllo del codice sorgente per ogni directory.  
  
-   Un MSSCCPRJ. File SCC può contenere le "AuxPath" e "Nomeprogetto" per più file sottoposti al controllo del codice sorgente all'interno di una determinata directory.  
  
-   La stringa "AuxPath" non deve avere le virgolette all'interno. È consentito avere virgolette come delimitatori \(ad esempio, una coppia di virgolette doppie può essere utilizzata per indicare una stringa vuota\). L'IDE rimuoverà tutte le offerte dalla stringa "AuxPath" quando viene letto da di MSSCCPRJ. File SCC.  
  
-   La stringa "Nomeprogetto" nel MSSCCPRJ. File SCC deve corrispondere esattamente alla stringa restituita dal `SccGetProjPath` \(funzione\). Se la stringa restituita dalla funzione contiene virgolette, la stringa di MSSCCPRJ. File SCC deve contenere virgolette intorno a esso e viceversa.  
  
-   Un MSSCCPRJ. File SCC viene creato o aggiornato ogni volta che viene inserito un file di controllo del codice sorgente.  
  
-   Se un MSSCCPRJ. File SCC viene eliminato, un provider deve rigenerare, la volta successiva che viene eseguita un'operazione di controllo di origine relativi a tale directory.  
  
-   Un MSSCCPRJ. File SCC deve seguire il formato definito.  
  
## Un'illustrazione di MSSCCPRJ. Formato di File SCC  
 Di seguito è un esempio di MSSCCPRJ. Formato di file di controllo del codice sorgente \(i numeri di riga vengono forniti solo come guida e non devono essere incluse nel corpo del file\):  
  
 \[Riga 1\] `SCC = This is a Source Code Control file`  
  
 \[Riga 2\]  
  
 \[Riga 3\] `[TestApp.sln]`  
  
 \[Riga 4\] `SCC_Aux_Path = "\\server\vss\"`  
  
 \[Riga 5\] `SCC_Project_Name = "$/TestApp"`  
  
 \[Riga 6\]  
  
 \[Riga 7\] `[TestApp.csproj]`  
  
 \[Riga 8\] `SCC_Aux_Path = "\\server\vss\"`  
  
 \[Riga 9\] `SCC_Project_Name = "$/TestApp"`  
  
 La prima riga indica lo scopo del file e come la firma per tutti i file di questo tipo. Questa riga dovrebbe essere visualizzato esattamente come in MSSCCPRJ tutti. File SCC:  
  
 `SCC = This is a Source Code Control file`  
  
 Di seguito è disponibile una sezione di impostazioni per ogni file, contrassegnati con il nome del file racchiusa tra parentesi quadre. In questa sezione viene ripetuta per ogni file viene tenuta traccia. Questa riga è un esempio di un nome file, vale a dire, `[TestApp.csproj]`. L'IDE prevede che le due righe seguenti. Non, tuttavia, definisce lo stile dei valori definiti. Le variabili sono `SCC_Aux_Path` e `SCC_Project_Name`.  
  
 `SCC_Aux_Path = "\\server\vss\"`  
  
 `SCC_Project_Name = "$/TestApp"`  
  
 Non è disponibile alcun delimitatore di fine a questa sezione. Il nome del file, nonché tutti i valori letterali che vengono visualizzati nel file sono definiti nel file di intestazione scc.h. Per altre informazioni, vedere [Stringhe utilizzate come chiavi per la ricerca di un controllo del codice sorgente del plug\-in](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md).  
  
## Vedere anche  
 [Plug\-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [Stringhe utilizzate come chiavi per la ricerca di un controllo del codice sorgente del plug\-in](../extensibility/strings-used-as-keys-for-finding-a-source-control-plug-in.md)