---
title: "IActiveScriptAuthor::AddTypeLib | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScriptAuthor.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScriptAuthor::AddTypeLib"
ms.assetid: d6696547-3eb5-4f31-9c5c-60aa29b6f083
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# IActiveScriptAuthor::AddTypeLib
Aggiunge una libreria dei tipi nello spazio dei nomi per lo script.  
  
## Sintassi  
  
```  
HRESULT AddTypeLib(  
   REFGUID   rguidTypeLib,  
   DWORD     dwMajor,  
   DWORD     dwMinor,  
   DWORD     dwFlags  
);  
```  
  
#### Parametri  
 `rguidTypeLib`  
 \[in\] Il CLSID \(identificatore di classe\) della libreria dei tipi da aggiungere.  
  
 `dwMajor`  
 \[in\] numero di versione principale.  
  
 `dwMinor`  
 \[in\] numero di versione secondario.  
  
 `dwFlags`  
 \[in\] Non utilizzato.  
  
## Valore restituito  
 Oggetto `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Questo metodo chiama `LoadTypeLib` per caricare la libreria dei tipi.  Al termine, questo metodo chiama `IActiveScriptAuthor::AddNamedItem` per aggiungere informazioni sul tipo.  
  
## Vedere anche  
 [Interfaccia IActiveScriptAuthor](../../winscript/reference/iactivescriptauthor-interface.md)   
 [IActiveScriptAuthor::AddNamedItem](../../winscript/reference/iactivescriptauthor-addnameditem.md)   
 [LoadTypeLib](http://msdn.microsoft.com/it-it/155b48e5-5438-409e-9342-630a6a500f60)