---
title: "Enumeratore di codice di stato file | Microsoft Docs"
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
  - "costanti denominate, SccStatus enumeratore"
  - "enumerazione dello stato di file di origine controllo plug-in,"
  - "Enumeratore SccStatus"
  - "enumeratore di codice di stato file"
ms.assetid: 5c37876b-c83c-4ca1-837b-57cd465a879a
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Enumeratore di codice di stato file
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il `SccStatus` enumeratore contiene valori costanti denominati che specificano lo stato di un file nel sistema di controllo di origine. Questa enumerazione viene utilizzata per la [SccQueryInfo](../extensibility/sccqueryinfo-function.md) e `POPLISTFUNC` funzione di callback \(vedere [POPLISTFUNC](../extensibility/poplistfunc.md) per informazioni dettagliate\).  
  
## Sintassi  
  
```  
enum SccStatus {  
   SCC_STATUS_INVALID          = -1L,  
   SCC_STATUS_NOTCONTROLLED    = 0x0000L,  
   SCC_STATUS_CONTROLLED       = 0x0001L,  
   SCC_STATUS_CHECKEDOUT       = 0x0002L,  
   SCC_STATUS_OUTOTHER         = 0x0004L,  
   SCC_STATUS_OUTEXCLUSIVE     = 0x0008L,  
   SCC_STATUS_OUTMULTIPLE      = 0x0010L,  
   SCC_STATUS_OUTOFDATE        = 0x0020L,  
   SCC_STATUS_DELETED          = 0x0040L,  
   SCC_STATUS_LOCKED           = 0x0080L,  
   SCC_STATUS_MERGED           = 0x0100L,  
   SCC_STATUS_SHARED           = 0x0200L,  
   SCC_STATUS_PINNED           = 0x0400L,  
   SCC_STATUS_MODIFIED         = 0x0800L,  
   SCC_STATUS_OUTBYUSER        = 0x1000L  
   SCC_STATUS_NOMERGE          = 0x2000L  
   SCC_STATUS_RESERVED_1       = 0x4000L  
   SCC_STATUS_RESERVED_2       = 0x8000L  
};  
```  
  
## Membri  
 SCC\_STATUS\_INVALID  
 Non è stato possibile ottenere lo stato; non fare affidamento su di esso.  
  
 SCC\_STATUS\_NOTCONTROLLED  
 File non è incluso nel controllo del codice sorgente.  
  
 SCC\_STATUS\_CONTROLLED  
 File incluso nel controllo del codice sorgente.  
  
 SCC\_STATUS\_CHECKEDOUT  
 Estratto dall'utente corrente nel disco locale.  
  
 SCC\_STATUS\_OUTOTHER  
 File viene estratto da un altro utente.  
  
 SCC\_STATUS\_OUTEXCLUSIVE  
 File è estratto in esclusiva.  
  
 SCC\_STATUS\_OUTMULTIPLE  
 File viene estratto da più di un utente.  
  
 SCC\_STATUS\_OUTOFDATE  
 Il file non è più recente.  
  
 SCC\_STATUS\_DELETED  
 File è stato eliminato dal progetto.  
  
 SCC\_STATUS\_LOCKED  
 Il file è bloccato; senza ulteriori versioni consentite.  
  
 SCC\_STATUS\_MERGED  
 File è stato unito ma non ancora risolto\/verificato.  
  
 SCC\_STATUS\_SHARED  
 File è condiviso tra progetti.  
  
 SCC\_STATUS\_PINNED  
 File è condiviso a una versione specifica.  
  
 SCC\_STATUS\_MODIFIED  
 File è stato modificato, interrotti\/violata.  
  
 SCC\_STATUS\_OUTBYUSER  
 File viene estratto dall'utente corrente.  
  
 SCC\_STATUS\_NOMERGE  
 File non può essere unite e non deve essere salvato prima di un'operazione GET.  
  
 SCC\_STATUS\_RESERVED\_1  
 Riservato per uso interno.  
  
 SCC\_STATUS\_RESERVED\_2  
 Riservato per uso interno.  
  
## Vedere anche  
 [Plug\-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [SccQueryInfo](../extensibility/sccqueryinfo-function.md)   
 [POPLISTFUNC](../extensibility/poplistfunc.md)