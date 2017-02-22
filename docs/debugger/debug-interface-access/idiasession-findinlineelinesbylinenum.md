---
title: "IDiaSession::findInlineeLinesByLinenum | Microsoft Docs"
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
ms.assetid: cf32ae7c-a0c8-4800-bc8f-d64fdd15fb06
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSession::findInlineeLinesByLinenum
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera un'enumerazione che consente a un client ripetere direttamente o indirettamente dalle informazioni sul numero di riga di tutte le funzioni in linea, nel file di origine e il numero di riga specificato.  
  
## Sintassi  
  
```cpp#  
HRESULT findInlineeLinesByVA (   
   IDiaSymbol*           compiland,  
   IDiaSourceFile*       file,  
   DWORD                 linenum,  
   DWORD                 column,  
   IDiaEnumLineNumbers** ppResult  
);  
```  
  
#### Parametri  
 `compiland`  
 \[in\] un oggetto [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) che rappresenta il modulo in cui trovare i numeri di riga.  Questo parametro non può essere `NULL`.  
  
 `file`  
 \[in\] un oggetto [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md) che rappresenta il file di origine in cui cercare.  Questo parametro non può essere `NULL`.  
  
 `linenum`  
 \[in\] specifica un numero di riga in base uno.  
  
> [!NOTE]
>  Non è possibile utilizzare zero per specificare tutte le righe \(utilizzare il metodo [IDiaSession::findLines](../../debugger/debug-interface-access/idiasession-findlines.md) per trovare tutte le righe\).  
  
 `column`  
 \[in\] specifica il numero di colonne.  Utilizzare zero specificare tutte le colonne.  Una colonna è un offset di byte in una riga.  
  
 `ppResult`  
 \[out\] restituisce un oggetto [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md) contenente un elenco di numeri di riga recuperati.  
  
## Valore restituito  
 In caso di esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice errore.  
  
## Vedere anche  
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [IDiaSourceFile](../../debugger/debug-interface-access/idiasourcefile.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [Enumerazione SymTagEnum](../../debugger/debug-interface-access/symtagenum.md)   
 [IDiaEnumLineNumbers](../../debugger/debug-interface-access/idiaenumlinenumbers.md)