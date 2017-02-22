---
title: "Debug Interface Access SDK | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "debug [DIA SDK]"
  - "debugger [DIA SDK]"
  - "DIA SDK"
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Debug Interface Access SDK
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il software development kit di Accesso dell'interfaccia di Microsoft Debug \(DIA SDK\) fornisce l'accesso a informazioni di debug archiviate nei file di database di programma \(PDB\) generati dagli strumenti di postcompiler Microsoft.  Poiché il formato del file .pdb generato dagli strumenti di postcompiler alla revisione costante, esporre il formato risulta poco pratica.  Utilizzo di diametro API, è possibile compilare applicazioni per la ricerca e passare le informazioni di debug archiviate in un file con estensione pdb.  Tali applicazioni possono, ad esempio, la segnalazione delle informazioni di traccia back dello stack e analizzare dati relativi alle prestazioni.  
  
## In questa sezione  
 [Introduzione](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 Viene fornita una panoramica delle funzionalità di DIA SDK e specifica se il DIA SDK è installato nonché l'intestazione e i file di libreria necessari.  
  
 [Ricerche nel file PDB](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Vengono fornite istruzioni su come utilizzare il diametro API per eseguire una query sul file con estensione pdb.  
  
 [Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 Viene illustrato come i simboli e i tag del simbolo vengono utilizzati in diametro API.  
  
 [Riferimento](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 Contiene le interfacce, i metodi, enumerazioni e le strutture di diametro API.  
  
 [Esempio Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md)  
 Viene illustrato come utilizzare il diametro API per trovare e passare le informazioni di debug.  
  
 [File di origine Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 Codice sorgente utilizzato da [Esempio Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md) per illustrare il diametro API.