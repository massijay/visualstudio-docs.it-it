---
title: "Rimozione delle informazioni di controllo di origine da. Proj e. Sln (file) | Microsoft Docs"
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
  - "plug-in del controllo codice sorgente, i file con estensione sln e proj"
ms.assetid: 7b06883f-35de-41e2-9a9e-d3edba236f17
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Rimozione delle informazioni di controllo di origine da. Proj e. Sln (file)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Nella versione 1,2 del plug\-in controllo del codice sorgente API le informazioni di SCC vengono archiviate in un file di MSSCCPRJ.SCC.  Il vantaggio del file di MSSCCPRJ.SCC è che le informazioni di SCC non sono inclusi nel controllo del codice sorgente, come avviene in file sln e di proj.  
  
## Modifiche della versione 1,2  
 Nei collegamenti del controllo del codice sorgente basati sulla versione 1,1 di plug\-in controllo del codice sorgente API, le informazioni sul controllo del codice sorgente vengono archiviate nel progetto \(proj\) e la soluzione \(sln\) viene memorizzato.  La posizione del database delle informazioni di controllo del codice sorgente è specificata da AuxPath e la posizione specifica all'interno del database è specificata da ProjName.  Questo comportamento può causare problemi dopo branch, la fork, o operazioni di copia poiché il ProjName è in genere non valido dopo una di queste operazioni.  
  
 Nella versione 1,1 di plug\-in controllo del codice sorgente API, l'ide utilizza i file di ~SAK per rilevare se un plug\-in supporta la stampa fronte il metodo di MSSCCPRJ.SCC di archiviare le informazioni di controllo del codice sorgente.  La versione 1,2 di plug\-in controllo del codice sorgente API fornisce una nuova funzionalità per rilevare il supporto per il file di MSSCCPRJ.SCC senza utilizzare un file di ~SAK.  Per ulteriori informazioni, vedere [Eliminazione di ~ SAK file](../../extensibility/internals/elimination-of-tilde-sak-files.md).  
  
## Vedere anche  
 [Novità di origine controllo plug\-in API versione 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)