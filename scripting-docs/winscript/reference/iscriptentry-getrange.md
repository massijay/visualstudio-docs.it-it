---
title: "IScriptEntry::GetRange | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IScriptEntry.GetRange
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IScriptEntry::GetRange"
ms.assetid: 3ac18f0a-b470-4f4d-b8f5-2da3fdef74f1
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# IScriptEntry::GetRange
Restituisce la posizione iniziale e la lunghezza di una voce.  
  
## Sintassi  
  
```  
HRESULT GetRange(  
   ULONG              *pichMin  
   ULONG              *pcch  
);  
```  
  
#### Parametri  
 `pichMin`  
 \[out\] per gli oggetti `IScriptEntry` che specificano un blocco di script, restituisce 0.  
  
 Per gli oggetti `IScriptEntry` che specificano un oggetto funzione, restituisce la posizione iniziale della funzione nel blocco di script corrente.  
  
 Per gli oggetti `IScriptScriptlet`, restituisce 0.  
  
 `pcch`  
 \[out\] per gli oggetti `IScriptEntry` che specificano un blocco di script, restituisce la lunghezza del testo.  
  
 Per gli oggetti `IScriptEntry` che specificano un oggetto funzione, restituisce la lunghezza della definizione di funzione.  
  
 Per gli oggetti `IScriptScriptlet`, restituisce la lunghezza della voce.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
  
## Vedere anche  
 [Interfaccia IScriptEntry](../../winscript/reference/iscriptentry-interface.md)