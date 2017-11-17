---
title: Debug Interface Access SDK | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- debugging [DIA SDK]
- debugger [DIA SDK]
- DIA SDK
ms.assetid: 4c0abe53-11d3-4b7a-bdc7-b054f85aaf40
caps.latest.revision: "12"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e404f0b893453fa319d5c4df97319f8e77720805
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="debug-interface-access-sdk"></a>Debug Interface Access SDK
Il Microsoft Debug interfaccia Access Software Development Kit (DIA SDK) fornisce l'accesso alle informazioni archiviate nei file di programma del database (con estensione pdb) generati dagli strumenti di post-compilazione Microsoft di debug. Poiché il formato del file PDB generato dagli strumenti di post-compilazione sottoposto a revisione costante, esponendo il formato risulta poco pratico. Tramite l'API di DIA, è possibile sviluppare applicazioni in cui cercare e visualizzare le informazioni di debug archiviate in un file con estensione pdb. Tali applicazioni, ad esempio, potrebbero segnalare informazioni sullo stack di traccia-back e analizzare i dati sulle prestazioni.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Introduzione](../../debugger/debug-interface-access/getting-started-debug-interface-access-sdk.md)  
 Offre una panoramica di DIA SDK e specifica in cui è installato il DIA SDK nonché l'intestazione obbligatoria e i file di libreria.  
  
 [Esecuzione di query nel file PDB](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Vengono fornite istruzioni su come utilizzare l'API di DIA per eseguire query sul file con estensione pdb.  
  
 [Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)  
 Vengono illustrate le modalità di utilizzo di simboli e relativi tag nell'API di DIA.  
  
 [Riferimento](../../debugger/debug-interface-access/debug-interface-access-sdk-reference.md)  
 Contiene le interfacce, metodi, enumerazioni e strutture dell'API di DIA.  
  
 [Esempio Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md)  
 Viene illustrato come utilizzare l'API di DIA per cercare e visualizzare le informazioni di debug.  
  
 [File di origine Dia2dump.cpp](../../debugger/debug-interface-access/dia2dump-cpp-source-file.md)  
 Utilizzato dal codice sorgente [esempio Dia2dump](../../debugger/debug-interface-access/dia2dump-sample.md) per illustrare l'API di DIA.