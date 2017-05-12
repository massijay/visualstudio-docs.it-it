---
title: "Metodo IJsDebugFrame::Evaluate | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugFrame.Evaluate
apilocation: jscript9diag.dll
ms.assetid: 0ee61340-37b8-4fbb-a028-748b5315e279
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsDebugFrame::Evaluate
Valutare un'espressione nel contesto di questo stack frame.  
  
## Sintassi  
  
```  
HRESULT Evaluate(  
   LPCOLESTR pExpressionText,  
   IJsDebugProperty **ppDebugProperty,  
   BSTR *pError  
);  
```  
  
#### Parametri  
 `pExpressionText`  
 \[in\] Espressione da valutare.  
  
 `ppDebugProperty`  
 \[out\] Oggetto che rappresenta il browser delle proprietà.  
  
 `pError`  
 \[out\] Messaggio di errore, se si verifica un errore.  
  
## Valore restituito  
  
## Note  
 Restituisce quanto segue: S\_OK: quando la valutazione ha esito positivo, \*ppDebugProperty contiene il risultato della valutazione.  S\_FALSE: la valutazione genera un errore \(o l'operazione di valutazione non è supportata\), \*pError contiene il messaggio di errore.  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsDebugFrame](../../winscript/reference/ijsdebugframe-interface.md)