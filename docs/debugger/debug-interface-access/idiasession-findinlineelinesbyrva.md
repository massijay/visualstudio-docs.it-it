---
title: "IDiaSession::findInlineeLinesByRVA | Microsoft Docs"
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
ms.assetid: 7a74d5ee-0dbf-47c0-92b4-47ec03b13ce9
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findInlineeLinesByRVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un'enumerazione che consente a un client ripetere direttamente o indirettamente dalle informazioni sul numero di riga di tutte le funzioni in linea, dal simbolo padre specificato e che è contenuto all'interno dell'indirizzo virtuale relativo specificato \(RVA\).  
  
## Sintassi  
  
```cpp#  
HRESULT findInlineeLinesByRVA (   
   IDiaSymbol*           parent,  
   DWORD                 rva,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parametri  
 `parent`  
 \[in\] un oggetto `IDiaSymbol` che rappresenta il padre.  
  
 `rva`  
 \[in\] specifica l'indirizzo come RVA.  
  
 `length`  
 \[in\] specifica l'intervallo di indirizzi, in numero di byte, per analizzare con questa query.  
  
 `ppResult`  
 \[out\] utilizza un oggetto `IDiaEnumLineNumbers` che contiene l'elenco dei numeri di riga recuperati.  
  
## Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)