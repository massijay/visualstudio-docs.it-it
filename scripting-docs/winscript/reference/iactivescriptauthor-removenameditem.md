---
title: "IActiveScriptAuthor::RemoveNamedItem | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.RemoveNamedItem
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::RemoveNamedItem"
ms.assetid: 1173ef46-39a5-4bc1-8e0c-89259a16be16
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IActiveScriptAuthor::RemoveNamedItem
Rimuove un oggetto `NamedItem` dallo spazio dei nomi del motore di creazione di script.  
  
## Sintassi  
  
```  
HRESULT RemoveNamedItem(  
   LPCOLESTR          pszName  
);  
```  
  
#### Parametri  
 `pszName`  
 \[in\] indirizzo del buffer che identifica l'oggetto `NamedItem` per rimuovere.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
|`S_FALSE`|L'oggetto `NamedItem` non è presente nello spazio dei nomi del motore di creazione di script.|  
  
## Note  
 [IActiveScript::AddNamedItem](../../winscript/reference/iactivescript-addnameditem.md) viene utilizzato per inserire l'oggetto `NamedItem` nello spazio dei nomi degli script del motore di creazione.  
  
## Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)