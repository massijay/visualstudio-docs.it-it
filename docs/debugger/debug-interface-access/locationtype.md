---
title: "LocationType | Microsoft Docs"
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
  - "LocationType (enumerazione)"
ms.assetid: d3e1eedc-bfd3-4c91-881b-d69565138d0f
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# LocationType
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Indica il tipo di informazioni sul contenuto di un simbolo.  
  
## Sintassi  
  
```cpp#  
enum LocationType {   
   LocIsNull,  
   LocIsStatic,  
   LocIsTLS,  
   LocIsRegRel,  
   LocIsThisRel,  
   LocIsEnregistered,  
   LocIsBitField,  
   LocIsSlot,  
   LocIsIlRel,  
   LocInMetaData,  
   LocIsConstant,  
   LocTypeMax  
};  
```  
  
## Elementi  
 `LocIsNull`  
 Le informazioni sul percorso non sono disponibili.  
  
 `LocIsStatic`  
 la posizione è statica.  
  
 `LocIsTLS`  
 La posizione è nella memoria locale di thread.  
  
 `LocIsRegRel`  
 la posizione è registro\-parente.  
  
 `LocIsThisRel`  
 la posizione è `this`\- relativo.  
  
 `LocIsEnregistered`  
 la posizione è in un registro.  
  
 `LocIsBitField`  
 La posizione è rappresentata da un campo di bit.  
  
 `LocIsSlot`  
 la posizione è uno slot di Microsoft Intermediate Language \(MSIL\).  
  
 `LocIsIlRel`  
 la posizione è MSIL\-parente.  
  
 `LocInMetaData`  
 La posizione è nei metadati.  
  
 `LocIsConstant`  
 La posizione è rappresentata da un valore costante.  
  
 `LocTypeMax`  
 Il numero di posizione nell'enumerazione.  
  
## Note  
 Le proprietà disponibili a [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md) l'interfaccia dipende dalla posizione del simbolo nel file di immagine.  Per ulteriori informazioni, vedere [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md).  
  
 I valori in questa enumerazione restituiti da una chiamata a [IDiaSymbol::get\_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md) metodo.  
  
## Requisiti  
 intestazione: cvconst.h  
  
## Vedere anche  
 [Enumerazioni e strutture](../../debugger/debug-interface-access/enumerations-and-structures.md)   
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)   
 [IDiaSymbol::get\_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)   
 [Percorsi dei simboli](../../debugger/debug-interface-access/symbol-locations.md)