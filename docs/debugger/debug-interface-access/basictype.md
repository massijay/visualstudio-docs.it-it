---
title: "BasicType | Microsoft Docs"
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
helpviewer_keywords: 
  - "BasicType (enumerazione)"
ms.assetid: 19ae53ba-cd6e-47b6-9f94-27ae663ce955
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# BasicType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Specifica il tipo di base del simbolo.  
  
## Sintassi  
  
```cpp#  
enum BasicType {   
   btNoType   = 0,  
   btVoid     = 1,  
   btChar     = 2,  
   btWChar    = 3,  
   btInt      = 6,  
   btUInt     = 7,  
   btFloat    = 8,  
   btBCD      = 9,  
   btBool     = 10,  
   btLong     = 13,  
   btULong    = 14,  
   btCurrency = 25,  
   btDate     = 26,  
   btVariant  = 27,  
   btComplex  = 28,  
   btBit      = 29,  
   btBSTR     = 30,  
   btHresult  = 31  
};  
```  
  
## Elementi  
 btNoType  
 Nessun tipo di base viene specificato.  
  
 btVoid  
 Il tipo di base è un oggetto `void`.  
  
 btChar  
 Il tipo di base è un oggetto `char` \(Tipo di C\/C\+\+\).  
  
 btWChar  
 Il tipo di base è un ampio carattere \(Unicode\) \(`WCHAR`\).  
  
 btInt  
 Il tipo di base viene `signed int` \(Tipo di C\/C\+\+\).  
  
 btUInt  
 Il tipo di base viene `unsigned int` \(Tipo di C\/C\+\+\).  
  
 btFloat  
 Il tipo di base è un numero a virgola mobile`FLOAT`\).  
  
 btBCD  
 il tipo di base è un numero decimale con codice binario \(`BCD`\).  
  
 btBool  
 Il tipo di base è un valore booleano \(`BOOL`\).  
  
 btLong  
 Il tipo di base è un oggetto `long int` \(Tipo di C\/C\+\+\).  
  
 btULong  
 Il tipo di base viene `unsigned long int` \(Tipo di C\/C\+\+\).  
  
 btCurrency  
 il tipo di base è valuta.  
  
 btDate  
 Il tipo di base viene data\/ora \(`DATE`\).  
  
 btVariant  
 Il tipo di base è una struttura variabile di tipo \(`VARIANT`\).  
  
 btComplex  
 il tipo di base è un numero complesso.  
  
 btBit  
 il tipo di base è un bit.  
  
 btBSTR  
 il tipo di base è una base o una stringa binaria \(`BSTR`\).  
  
 btHresult  
 Il tipo di base viene `HRESULT`.  
  
## Note  
 I valori in questa enumerazione sono restituiti da [IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md) metodo.  
  
## Requisiti  
 intestazione: cvconst.h  
  
## Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)   
 [IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)