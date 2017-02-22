---
title: "DataKind | Microsoft Docs"
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
  - "DataKind (enumerazione)"
ms.assetid: b64be708-22d6-4360-99e7-8f4e6b196de7
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DataKind
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Indica l'ambito particolare di un valore di dati.  
  
## Sintassi  
  
```cpp#  
enum DataKind {   
   DataIsUnknown,  
   DataIsLocal,  
   DataIsStaticLocal,  
   DataIsParam,  
   DataIsObjectPtr,  
   DataIsFileStatic,  
   DataIsGlobal,  
   DataIsMember,  
   DataIsStaticMember,  
   DataIsConstant  
};  
```  
  
## Elementi  
 DataIsUnknown  
 Il simbolo di dati non può essere specificato.  
  
 DataIsLocal  
 L'elemento dati è una variabile locale.  
  
 DataIsStaticLocal  
 L'elemento dati è una variabile locale statica.  
  
 DataIsParam  
 L'elemento dati è un parametro formale.  
  
 DataIsObjectPtr  
 L'elemento dati è un puntatore all'oggetto \(`this`\).  
  
 DataIsFileStatic  
 L'elemento dati è una variabile di file\-scoped.  
  
 DataIsGlobal  
 L'elemento dati è una variabile globale.  
  
 DataIsMember  
 L'elemento dati è una variabile membro dell'oggetto.  
  
 DataIsStaticMember  
 L'elemento dati è variabile statica della classe.  
  
 DataIsConstant  
 L'elemento dati è un valore costante.  
  
## Note  
 I valori in questa enumerazione sono restituiti da [IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md) metodo.  
  
## Requisiti  
 intestazione: cvconst.h  
  
## Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)