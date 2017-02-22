---
title: "IDiaSymbol::findInlineeLinesByAddr | Microsoft Docs"
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
ms.assetid: f1ab47ca-c851-48ea-9c12-47fb80b31102
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::findInlineeLinesByAddr
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un'enumerazione che consente a un client ripetere direttamente o indirettamente dalle informazioni sul numero di riga di tutte le funzioni in linea, in questo simbolo nell'intervallo di indirizzi specificato.  
  
## Sintassi  
  
```cpp#  
HRESULT findInlineeLinesByAddr (   
   DWORD                 isect,  
   DWORD                 offset,  
   DWORD                 length,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parametri  
 `isect`  
 \[in\] specifica la parte della sezione dell'indirizzo.  
  
 `offset`  
 \[in\] specifica il componente di offset dell'indirizzo.  
  
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
 [IDiaSession::findInlineeLines](../../debugger/debug-interface-access/idiasession-findinlineelines.md)