---
title: "IDiaSession::findInlineFramesByVA | Microsoft Docs"
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
ms.assetid: df9e68f6-e0a4-4cf6-b11d-61c40351e0cd
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# IDiaSession::findInlineFramesByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un'enumerazione che consente a un client ripetere da tutti i frame inline in un indirizzo virtuale specificato \(VA\).  
  
## Sintassi  
  
```cpp#  
HRESULT findInlineFramesByVA (   
   IDiaSymbol*       parent,  
   ULONGLONG         va,  
   IDiaEnumSymbols** ppResult  
);  
```  
  
#### Parametri  
 `parent`  
 \[in\] un oggetto `IDiaSymbol` che rappresenta il padre.  
  
 `va`  
 \[in\] specifica l'indirizzo come VA.  
  
 `ppResult`  
 \[out\] utilizza un oggetto `IDiaEnumSymbols` che contiene l'elenco dei frame recuperati.  
  
## Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)