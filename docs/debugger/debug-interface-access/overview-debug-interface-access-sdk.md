---
title: "Panoramica (Debug Interface Access SDK) | Microsoft Docs"
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
  - "tipi definiti dall'utente"
  - "file dbg"
  - "moduli"
  - "interfacce [DIA SDK]"
  - "DBG (file)"
  - "routine [DIA SDK]"
  - "file eseguibili"
  - "oggetti COM, in DIA SDK"
  - "moduli"
  - "immagini eseguibili"
ms.assetid: 720b4479-a8bc-4fec-860e-80c1a0780405
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Panoramica (Debug Interface Access SDK)
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Utilizzare il DIA SDK per accedere alle informazioni di debug Microsoft.  Il DIA SDK fornisce un'api basato su COM che evita di dover riscrivere il codice ogni volta che Microsoft modifica il formato delle informazioni di debug.  Il DIA SDK consente inoltre di leggere da un set più ristretto delle versioni precedenti di informazioni di debug, che si trovano nei file di estensione dbg e pdb generati da [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] versioni 5,0 e successive.  
  
 Ogni interfaccia in DIA SDK rappresenta un oggetto COM diverso, a eccezione di quanto indicato in caso contrario.  Ulteriori interfacce e pertanto oggetti aggiuntivi, vengono creati mediante query esplicite, ad esempio [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md) o  [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md), anziché chiamare  `QueryInterface` i puntatori a interfaccia esistenti.  
  
## Vedere anche  
 [IDiaDataSource::openSession](../../debugger/debug-interface-access/idiadatasource-opensession.md)   
 [IDiaSession::findChildren](../../debugger/debug-interface-access/idiasession-findchildren.md)