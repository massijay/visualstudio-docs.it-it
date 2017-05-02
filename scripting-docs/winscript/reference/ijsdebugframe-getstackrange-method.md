---
title: "Metodo IJsDebugFrame::GetStackRange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetStackRange
apilocation: jscript9diag.dll
ms.assetid: a6d1d8be-efc0-442d-9756-1959c8f102bd
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsDebugFrame::GetStackRange
Restituisce l'intervallo di indirizzi assoluti dello stack frame JavaScript logico.  
  
## Sintassi  
  
```  
HRESULT GetStackRange(  
   UINT64 *pStart,  
   UINT64 *pEnd  
);  
```  
  
#### Parametri  
 `pStart`  
 \[out\] Basare la maggior parte del puntatore dello stack del frame.  
  
 `pEnd`  
 \[out\] Completare la maggior parte del puntatore di impilatore del frame.  
  
## Valore restituito  
  
## Note  
 Questo metodo è utile per riunire tracce dello stack con interfoliazione raccolte da più runtime.  I puntatori di stack iniziale e finale possono includere più stack frame del computer virtuale \(frame di runtime di JavaScript interpretato\). Da inizio \> fine man mano che lo stack aumenta dall'indirizzo alto a quello basso.  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)