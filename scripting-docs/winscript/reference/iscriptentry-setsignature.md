---
title: "IScriptEntry::SetSignature | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.SetSignature
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::SetSignature"
ms.assetid: 8513587d-9df2-4621-afe7-56eacbb5e688
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# IScriptEntry::SetSignature
Imposta le informazioni relative a un oggetto funzione `IScriptEntry`.  
  
## Sintassi  
  
```  
HRESULT SetSignature(  
   ITypeInfo          *pti  
   ULONG              iMethod  
);  
```  
  
#### Parametri  
 `pti`  
 \[in\] informazioni sul tipo.  
  
 `iMethod`  
 \[in\] indirizzo di metodo nell'oggetto `ITypeInfo`.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 È necessario digitare informazioni in impostate tramite `IScriptEntry::SetSignature` o [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md).  Le informazioni sui tipi possono essere generate dalla voce sulla rappresentazione interna di funzione.  
  
## Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)