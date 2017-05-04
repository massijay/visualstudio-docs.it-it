---
title: "IActiveScriptAuthor::GetLanguageFlags | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.GetLanguageFlags
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::GetLanguageFlags"
ms.assetid: eb244452-62f7-4a73-b48f-1aa05cbcc32d
caps.latest.revision: 14
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 14
---
# IActiveScriptAuthor::GetLanguageFlags
Restituisce informazioni in lingua inglese\).  
  
## Sintassi  
  
```  
HRESULT GetLanguageFlags(  
   DWORD              *pgrfasa  
);  
```  
  
#### Parametri  
 `pgrfasa`  
 \[out\] flag che contengono informazioni in lingua inglese\).  Può essere una combinazione dei valori seguenti:  
  
|Costante|Valore|Descrizione|  
|--------------|------------|-----------------|  
|fasaPreferInternalHandler|0x0001|Il linguaggio preferisce la creazione del gestore eventi di script nel motore di creazione di script anziché applicazione.|  
|fasaSupportInternalHandler|0x0002|I gestori eventi di script dei supporti linguistici creati dal motore di creazione di script.|  
|fasaCaseSensitive|0x0004|Il linguaggio di script viene applicata la distinzione tra maiuscole e minuscole.|  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Se il motore di creazione di script gestiti i gestori eventi, l'applicazione deve chiamare `CreateChildHandler` da un oggetto `IScriptEntry`.  Verrà creato un oggetto `IScriptScriptlet` che corrisponde al gestore eventi.  Il motore aggiunge un gestore eventi alla voce dello script.  Il gestore eventi è una funzione vuota contenente le informazioni sulla firma.  
  
 Se l'applicazione gestisce i gestori eventi, deve chiamare `CreateChildHandler` da un oggetto `IScriptNode` che rappresenta uno scriptlet del gestore eventi.  Verrà creato un oggetto `IScriptScriptlet` associato allo scriptlet del gestore eventi.  L'applicazione deve anche aggiungere una funzione vuota come gestore eventi a un oggetto nuovo o esistente `IScriptEntry`.  
  
## Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)