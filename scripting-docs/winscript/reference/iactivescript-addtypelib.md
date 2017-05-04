---
title: "IActiveScript::AddTypeLib | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.AddTypeLib
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_AddTypeLib"
ms.assetid: 8e507ea8-c80a-471c-b482-ae753c6e8595
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::AddTypeLib
Aggiunge una libreria dei tipi nello spazio dei nomi per lo script.  È simile alla direttiva `#include` C\/C\+\+.  Consente un insieme di elementi predefiniti quali le definizioni della classe, `typedefs`e costanti denominate da aggiungere all'ambiente di runtime disponibile per lo script.  
  
## Sintassi  
  
```  
HRESULT AddTypeLib(  
    REFGUID guidTypeLib,  // CLSID of type library  
    DWORD dwMaj,          // major version number  
    DWORD dwMin,          // minor version number  
    DWORD dwFlags         // option flags  
);  
```  
  
#### Parametri  
 `guidTypeLib`  
 \[in\] CLSID della libreria dei tipi da aggiungere.  
  
 `dwMaj`  
 \[in\] numero di versione principale.  
  
 `dwMin`  
 \[in\] numero di versione secondario.  
  
 `dwFlags`  
 \[in\] contrassegni di opzione.  È necessario quanto segue:  
  
|Valore|Significato|  
|------------|-----------------|  
|SCRIPTTYPELIB\_ISCONTROL|La libreria dei tipi descrive un controllo ActiveX l'host.|  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Riuscita.|  
|`E_INVALIDARG`|Un argomento non è valido.|  
|`E_UNEXPECTED`|La chiamata non era prevista, ad esempio il motore di scripting non è ancora stato caricato o non inizializzata\).|  
|`TYPE_E_CANTLOADLIBRARY`|La libreria dei tipi specificata non può essere caricata.|  
  
## Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)