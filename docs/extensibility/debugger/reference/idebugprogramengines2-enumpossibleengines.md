---
title: "IDebugProgramEngines2::EnumPossibleEngines | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProgramEngines2::EnumPossibleEngines"
helpviewer_keywords: 
  - "IDebugProgramEngines2::EnumPossibleEngines"
ms.assetid: 993d70a4-f6a5-4e47-a603-0b162b9fde00
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProgramEngines2::EnumPossibleEngines
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Restituisce i GUID per tutti i motori di debug possibili \(DE\) che è possibile eseguire il debug del programma.  
  
## Sintassi  
  
```cpp#  
HRESULT EnumPossibleEngines(   
   DWORD  celtBuffer,  
   GUID*  rgguidEngines,  
   DWORD* pceltEngines  
);  
```  
  
```c#  
int EnumPossibleEngines(   
   uint      celtBuffer,  
   GUID[]    rgguidEngines,  
   ref DWORD pceltEngines  
);  
```  
  
#### Parametri  
 `celtBuffer`  
 \[in\]  il numero di DE GUIDs da restituire.  Viene anche specifica la dimensione massima della matrice di `rgguidEngines` .  
  
 `rgguidEngines`  
 \[in, out\]  una matrice di DE GUIDs da riempire.  
  
 `pceltEngines`  
 \[out\]  Restituisce il numero effettivo di DE GUIDs restituito.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  Restituisce \[C\+\+\] `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` o \[c\#\] 0x8007007A se il buffer non è sufficiente.  
  
## Note  
 Per determinare quanti motori presenti una volta, chiama questo metodo con il parametro di `celtBuffer` impostato su 0 e il parametro di `rgguidEngines` impostato su un valore null.  Viene restituito `HRESULT_FROM_WIN32(ERROR_INSUFFICIENT_BUFFER)` \(0x8007007A per c\#\) e il parametro di `pceltEngines` restituisce la dimensione necessaria del buffer.  
  
## Vedere anche  
 [IDebugProgramEngines2](../../../extensibility/debugger/reference/idebugprogramengines2.md)