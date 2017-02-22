---
title: "UdtKind | Microsoft Docs"
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
  - "UdtKind (enumerazione)"
ms.assetid: 400b59b9-373c-42cb-aae1-570494214328
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# UdtKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Viene descritta la vasta gamma di tipo definito dall'utente \(UDT\).  
  
## Sintassi  
  
```cpp#  
enum UdtKind {   
   UdtStruct,  
   UdtClass,  
   UdtUnion,  
   UdtInterface  
};  
```  
  
## Elementi  
 UdtStruct  
 Tipo definito dall'utente è una struttura.  
  
 UdtClass  
 Tipo definito dall'utente è una classe.  
  
 UdtUnion  
 Tipo definito dall'utente è un'unione.  
  
 UdtInterface  
 Tipo definito dall'utente è un'interfaccia.  
  
## Note  
 Vengono restituiti i valori di questa enumerazione per la [IDiaSymbol::get\_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md) metodo.  
  
## Requisiti  
 Intestazione: cvconst.h  
  
## Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)