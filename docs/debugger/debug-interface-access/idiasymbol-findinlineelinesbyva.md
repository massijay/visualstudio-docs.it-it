---
title: "IDiaSymbol::findInlineeLinesByVA | Microsoft Docs"
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
ms.assetid: 61427d33-30d2-4ac9-9bd6-c58c6c705072
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::findInlineeLinesByVA
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un'enumerazione che consente a un client ripetere direttamente o indirettamente dalle informazioni sul numero di riga di tutte le funzioni in linea, in questo simbolo interno dell'indirizzo virtuale specificato \(VA\).  
  
## Sintassi  
  
```cpp#  
HRESULT findInlineeLinesByVA (   
   ULONGLONG             va,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parametri  
 `va`  
 \[in\] specifica l'indirizzo come VA.  
  
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