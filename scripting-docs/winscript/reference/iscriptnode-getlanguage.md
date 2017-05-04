---
title: "IScriptNode::GetLanguage | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptNode.GetLanguage
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptNode::GetLanguage"
ms.assetid: 089715fd-6746-474e-94ed-2e57ee4bc0da
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# IScriptNode::GetLanguage
Restituisce il linguaggio di script che viene utilizzato dal nodo corrente dello script.  
  
## Sintassi  
  
```  
HRESULT GetLanguage(  
   BSTR               *pbstr  
);  
```  
  
#### Parametri  
 `pbstr`  
 \[out\] restituisce "JScript" se il nodo dello script utilizza JScript, o "VBScript" se il nodo dello script utilizza l'edizione di scripting di Visual Basic \(VBScript\).  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
  
## Vedere anche  
 [Interfaccia IScriptNode](../../winscript/reference/iscriptnode-interface.md)