---
title: "IDebugEngine3::LoadSymbols | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEngine3::LoadSymbols"
helpviewer_keywords: 
  - "IDebugEngine3::LoadSymbols"
ms.assetid: c846a440-1d91-4d48-b8f1-82e902ae152b
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugEngine3::LoadSymbols
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Carica \(a seconda delle esigenze\) i simboli per tutti i moduli di cui viene eseguito il debug di questo modulo di gestione del debug.  
  
## Sintassi  
  
```cpp  
HRESULT LoadSymbols();  
```  
  
```c#  
int LoadSymbols();  
```  
  
#### Parametri  
 Nessuno.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario restituisce il codice di errore.  
  
## Note  
 Verranno caricati i simboli di debug per tutti i moduli a cui si fa riferimento nel modulo di gestione del debug.  I simboli vengono caricati solo se non sono già stati caricati.  I simboli vengono trovati i percorsi impostati da una chiamata a [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md).  
  
## Vedere anche  
 [SetSymbolPath](../../../extensibility/debugger/reference/idebugengine3-setsymbolpath.md)   
 [IDebugEngine3](../../../extensibility/debugger/reference/idebugengine3.md)