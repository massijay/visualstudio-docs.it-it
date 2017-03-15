---
title: "IDebugEngine3::SetSymbolPath | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::SetSymbolPath"
helpviewer_keywords: 
  - "IDebugEngine3::SetSymbolPath"
ms.assetid: 47b48f84-8a96-401f-84df-0baa8a96d26e
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# IDebugEngine3::SetSymbolPath
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Imposta il percorso o percorsi che vengono trovati i simboli di debug.  
  
## Sintassi  
  
```cpp#  
HRESULT SetSymbolPath (  
   LPOLESTR            szSymbolSearchPath,  
   LPOLESTR            szSymbolCachePath,  
   LOAD_SYMBOLS_FLAGS  Flags  
);  
```  
  
```c#  
int SetSymbolPath(  
   string                    szSymbolSearchPath,   
   string                    szSymbolCachePath,   
   enum_LOAD_SYMBOLS_FLAGS   Flags  
);  
```  
  
#### Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`szSymbolSearchPath`|\[in\]  Stringa contenente il percorso di ricerca o i percorsi di simboli.  Vedere “commenti„ per i dettagli.  Non può essere null.|  
|`szSymbolCachePath`|\[in\]  Stringa contenente il percorso locale in cui i simboli possono essere memorizzati nella cache.  Non può essere null.|  
|`Flags`|\[in\]  non utilizzato; sempre impostato su 0.|  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario restituisce un codice di errore.  
  
## Note  
 La stringa`szSymbolSearchPath` è un elenco di uno o più percorsi, separati da punto e virgola, per individuare i simboli.  Questi percorsi possono essere un percorso locale, un percorso UNC stile, o un URL.  Questi percorsi possono anche essere una combinazione di tipi diversi.  Se il percorso è UNC \(ad esempio, \\\\Symserver\\Symbols\), il motore di debug deve determinare se il percorso è in un server di simboli e può caricare i simboli da tale server, memorizzarli nella cache nel percorso specificato da `szSymbolCachePath`.  
  
 Il percorso dei simboli può anche contenere uno o più percorsi della cache.  Le cache sono elencati in ordine di priorità, con la cache di determinare innanzitutto e \* nei simboli da separati.  Di seguito è riportato un esempio:  
  
```  
\\symbols\symbols;\\someotherserver\symbols;c:\symbols\httpsymbols*http://msdl.microsoft.com  
```  
  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md) Il metodo esegue effettivamente il caricamento dei simboli.  
  
## Vedere anche  
 [LoadSymbols](../../../extensibility/debugger/reference/idebugengine3-loadsymbols.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)