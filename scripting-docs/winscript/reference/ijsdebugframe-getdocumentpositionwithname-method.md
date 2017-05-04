---
title: "Metodo IJsDebugFrame::GetDocumentPositionWithName | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.GetDocumentPositionWithName
apilocation: jscript9diag.dll
ms.assetid: 1d994714-2c87-4a9e-ae14-a15eec9520c7
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsDebugFrame::GetDocumentPositionWithName
Restituisce la posizione corrente dello stack frame nel documento a livello utente.  
  
## Sintassi  
  
```  
HRESULT GetDocumentPositionWithName(  
   BSTR *pDocumentName,  
   DWORD *pLine,  
   DWORD *pColumn  
);  
```  
  
#### Parametri  
 `pDocumentName`  
 \[out\] Per gli script statici, un URL da documentare.  Per gli script dinamici, viene restituito un nome contenente il tipo di script \(ad esempio, codice eval, codice della funzione e così via\).  
  
 `pLine`  
 \[out\] Posizione della riga in base 1 all'interno del documento.  
  
 `pColumn`  
 \[out\] Posizione della riga in base 1 all'interno del documento.  
  
## Valore restituito  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)