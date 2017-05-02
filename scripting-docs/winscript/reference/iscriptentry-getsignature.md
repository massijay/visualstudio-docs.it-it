---
title: "IScriptEntry::GetSignature | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetSignature
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetSignature"
ms.assetid: 8cbf37ac-b14c-4e15-a613-06f34857da9b
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetSignature
Restituisce informazioni sui tipi per un oggetto funzione `IScriptEntry`.  
  
## Sintassi  
  
```  
HRESULT GetSignature(  
   ITypeInfo          **ppti  
   ULONG              *piMethod  
);  
```  
  
#### Parametri  
 `ppti`  
 \[out\] le informazioni sui tipi associati a questo oggetto funzione `IScriptEntry`.  
  
 `piMethod`  
 \[out\] indice di metodo nell'oggetto `ITypeInfo`.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 È necessario digitare informazioni in impostate tramite [IScriptEntry::SetSignature](../../winscript/reference/iscriptentry-setsignature.md) o [IScriptNode::CreateChildHandler](../../winscript/reference/iscriptnode-createchildhandler.md).  Le informazioni sui tipi possono essere generate dalla voce sulla rappresentazione interna di funzione.  
  
## Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)