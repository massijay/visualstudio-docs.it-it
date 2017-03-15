---
title: "Introduzione (Debug Interface Access SDK) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "file dbg"
  - "DBG (file)"
ms.assetid: cb3d040a-2846-40d7-bdbc-8a5beb5dd2f6
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Introduzione (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il Debug \(DIA\) Interface Access SDK offre documentazione esplicativo e un esempio che illustra come utilizzare il diametro API.  Utilizzare le interfacce e metodi nel DIA SDK per lo sviluppo di applicazioni personalizzate che aprono i file di estensione dbg e PDB e individuare il contenuto dei simboli, i valori, gli attributi, gli indirizzi e altre informazioni di debug.  Il presente SDK fornisce inoltre le tabelle di riferimento per le proprietà associate ai simboli presenti nelle applicazioni C\+\+.  
  
 Un utilizzo ottimale del DIA SDK, è necessario conoscere le operazioni seguenti:  
  
-   linguaggio di programmazione in C\+\+  
  
-   Programmazione COM  
  
-   ambiente di sviluppo integrato di Visual Studio \(IDE\) per compilare gli esempi  
  
 Il DIA SDK in genere installato con Visual Studio e la relativa posizione predefinita è *\[unità\]*\\Program Files\\Microsoft Visual Studio 9.0\\DIA SDK.  Durante l'installazione, il msdia90.dll, che implementa il DIA SDK, viene automaticamente registrato quindi tutti quello che è necessario eseguire per utilizzare anziché incorporare `dia2.h` nel programma e collegarsi a  `diaguids.lib`.  
  
 intestazione: include \\ dia2.h  
  
 raccolta: lib \\ diaguids.lib  
  
 DLL: bin \\ msdia80.dll  
  
 IDL: IDL \\ dia2.idl  
  
## Argomenti della sezione  
 [Panoramica](../../debugger/debug-interface-access/overview-debug-interface-access-sdk.md)  
 Esaminare l'architettura di base di diametro.  
  
 [Ricerche nel file PDB](../../debugger/debug-interface-access/querying-the-dot-pdb-file.md)  
 Vengono fornite istruzioni dettagliate su come utilizzare il diametro API per eseguire una query su un file con estensione pdb.  
  
## Vedere anche  
 [Debug Interface Access SDK](../../debugger/debug-interface-access/debug-interface-access-sdk.md)