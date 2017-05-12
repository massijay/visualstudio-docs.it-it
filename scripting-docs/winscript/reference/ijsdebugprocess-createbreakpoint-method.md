---
title: "Metodo IJsDebugProcess::CreateBreakPoint | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugProcess.CreateBreakPoint
apilocation: jscript9diag.dll
ms.assetid: a2cb4233-2846-4d11-aa13-21de43abda9f
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Metodo IJsDebugProcess::CreateBreakPoint
Imposta il punto di interruzione nella posizione del documento specificata.  
  
## Sintassi  
  
```  
HRESULT CreateBreakPoint(  
   UINT64 documentId,  
   DWORD characterOffset,  
   DWORD characterCount,  
   BOOL isEnabled,  
   IJsDebugBreakPoint **ppDebugBreakPoint  
);  
```  
  
#### Parametri  
 `documentId`  
 \[in\] Puntatore a IDebugDocumentText.  
  
 `characterOffset`  
 \[in\] Offset del carattere dall'inizio del file.  
  
 `characterCount`  
 \[in\] Lunghezza del testo del documento in cui deve essere inserito il punto di interruzione.  
  
 `isEnabled`  
 \[in\] Specifica se il punto di interruzione è abilitato.  
  
 `ppDebugBreakPoint`  
 \[out\] Oggetto che rappresenta il punto di interruzione creato.  
  
## Valore restituito  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsDebugProcess](../../winscript/reference/ijsdebugprocess-interface.md)