---
title: "IActiveScript::Clone | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IActiveScript.Clone
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IActiveScript_Clone"
ms.assetid: aa000b2a-7085-448d-a422-f7adac7851cb
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IActiveScript::Clone
Duplica il motore di scripting corrente \(meno qualsiasi stato corrente di esecuzione, restituendo un motore di script caricato che non dispone di sito nel thread corrente.  Le proprietà del nuovo modulo di gestione di scripting saranno identiche alle proprietà che il motore di script originale in se sarebbe opportuno quindi fornire nuovamente lo stato inizializzato.  
  
## Sintassi  
  
```  
HRESULT Clone(  
    IActiveScript **ppscript  // receives pointer to IActiveScript  
);  
```  
  
#### Parametri  
 `ppscript`  
 \[out\] indirizzo di una variabile che riceve un puntatore a un'interfaccia [IActiveScript](../../winscript/reference/iactivescript.md) del motore di scripting duplicato.  L'host deve creare un sito e chiamare il metodo [IActiveScript::SetScriptSite](../../winscript/reference/iactivescript-setscriptsite.md) sul motore di scripting prima che sia stato inizializzato e, pertanto, utilizzabile.  
  
## Valore restituito  
 Restituisce uno dei seguenti valori:  
  
|Valore restituito|Significato|  
|-----------------------|-----------------|  
|`S_OK`|Riuscita.|  
|`E_NOTIMPL`|Metodo non supportato.|  
|`E_POINTER`|Un puntatore non valido è stato specificato.|  
|`E_UNEXPECTED`|La chiamata non era prevista, ad esempio il motore di scripting non è ancora stato caricato o non inizializzata\).|  
  
## Note  
 Il metodo `IActiveScript::Clone` è un'ottimizzazione `IPersist*::Save`, `CoCreateInstance`e `IPersist*::Load`, in modo che lo stato di un nuovo modulo di gestione di script deve essere uguale a se lo stato del modulo di gestione di script originale è stato salvato e stato caricato in un nuovo modulo di gestione di script.  Gli elementi denominati siano duplicati nel motore di scripting duplicato, ma puntatori a oggetti specifici per ciascun elemento sono dimenticati e vengono ottenuti con il metodo [IActiveScriptSite::GetItemInfo](../../winscript/reference/iactivescriptsite-getiteminfo.md).  Ciò consente un modello a oggetti identico a punti di ingresso per thread \(un modello di apartment\) da utilizzare.  
  
 Questo metodo viene utilizzato per gli host server con multithreading che possono eseguire più istanze dello stesso script.  Il motore di scripting può restituire `E_NOTIMPL`in questo caso, l'host può ottenere lo stesso risultato duplicando lo stato persistente e creando una nuova istanza del motore di scripting con un'interfaccia `IPersist*`.  
  
 Questo metodo può essere chiamato dai thread non di base senza con conseguente callout di non base agli oggetti host o a un'interfaccia [IActiveScriptSite](../../winscript/reference/iactivescriptsite.md).  
  
## Vedere anche  
 [IActiveScript](../../winscript/reference/iactivescript.md)