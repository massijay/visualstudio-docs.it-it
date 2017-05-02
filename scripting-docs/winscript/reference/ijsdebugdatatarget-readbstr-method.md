---
title: "Metodo IJsDebugDataTarget::ReadBSTR | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadBSTR
apilocation: jscript9diag.dll
ms.assetid: 4b571db7-04b9-42a0-9a3e-310ac9d0e659
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsDebugDataTarget::ReadBSTR
Legge una stringa BSTR dalla destinazione del debug.  
  
## Sintassi  
  
```  
HRESULT ReadBSTR(  
   UINT64 address,  
   BSTR *pString  
);  
```  
  
#### Parametri  
 `address`  
 \[in\] Indirizzo da cui leggere.  
  
 `pString`  
 \[out\] Stringa BSTR letta dalla destinazione del debug.  
  
## Valore restituito  
  
## Note  
 Restituisce E\_JsDEBUG\_INVALID\_MEMORY\_ADDRESS se l'indirizzo non è valido.  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)