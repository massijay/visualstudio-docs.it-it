---
title: "Metodo IJsDebug::OpenVirtualProcess | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJSDebug.OpenVirtualProcess
apilocation: jscript9diag.dll
ms.assetid: 5612bf1b-a4e3-4eaf-ac5e-c2e1f147c395
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsDebug::OpenVirtualProcess
Metodo factory utilizzato per creare un nuovo oggetto processo virtuale.  
  
## Sintassi  
  
```  
 HRESULT OpenVirtualProcess(  
   DWORD processId,  
   UINT64 runtimeJsBaseAddress,  
   IJsDebugDataTarget *pDataTarget,  
   IJsDebugProcess **ppProcess  
);  
```  
  
#### Parametri  
 `processId`  
 \[in\] ID processo a cui connettere il debugger.  
  
 `runtimeJsBaseAddress`  
 \[in\] Indirizzo di base in cui il runtime JavaScript è stato caricato nel processo di destinazione.  
  
 `pDataTarget`  
 \[in\] Il debugger fornisce l'interfaccia per eseguire una query per lo stato del processo.  
  
 `ppProcess`  
 \[out\] Nuovo oggetto processo di debug  
  
## Valore restituito  
  
## Note  
 Restituisce E\_JsDEBUG\_MISMATCHED\_RUNTIME se Jscript9diag e Jscript9 non corrispondono.  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsDebug](../../winscript/reference/ijsdebug-interface.md)