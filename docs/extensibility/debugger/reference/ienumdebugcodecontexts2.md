---
title: "IEnumDebugCodeContexts2 | Microsoft Docs"
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
  - "IEnumDebugCodeContexts2"
helpviewer_keywords: 
  - "IEnumDebugCodeContexts2"
ms.assetid: 72915146-215f-4c99-a034-131b2b474e0e
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# IEnumDebugCodeContexts2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia enumera i contesti di codice associati alla sessione di debug, o con un programma o un documento specifico.  
  
## Sintassi  
  
```  
IEnumDebugCodeContexts2 : IUnknown  
```  
  
## Note per gli implementatori  
 Il motore \(DE\) di debug implementa questa interfaccia per rappresentare un elenco dei contesti di codice per una particolare posizione del testo in un programma, o un elenco dei contesti di codice per un particolare contesto del documento.  
  
## Note per i chiamanti  
 La funzione restituisce false quando `N` è 0, altrimenti `get<0>(tpl1) != get<0>(tpl2) || get<1>(tpl1) != get<1>(tpl2) || ... || get<N - 1>(tpl1) == get<N - 1>(tpl2)`.  
  
 Chiamare [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md) per ottenere questa interfaccia che rappresenta un elenco di tutti i contesti di codice in un documento di origine specifico.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IEnumDebugCodeContexts2`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Successivo](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-next.md)|Recupera un numero specificato dei contesti di codice in una sequenza di enumerazione.|  
|[Skip](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-skip.md)|Ignora un numero specificato dei contesti di codice in una sequenza di enumerazione.|  
|[Reimposta](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-reset.md)|Reimposta una sequenza di enumerazione all'inizio.|  
|[Clona](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-clone.md)|Crea un enumeratore che contiene lo stesso stato di enumerazione dell'enumeratore corrente.|  
|[GetCount](../../../extensibility/debugger/reference/ienumdebugcodecontexts2-getcount.md)|Ottiene il numero dei contesti di codice in un enumeratore.|  
  
## Note  
 Chiamate [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md) di Visual Studio per popolare un elenco dei contesti di codice che l'utente può effettuare quando si imposta l'istruzione successiva o visualizzando il disassembly per un file di origine.  I contesti di codice più possono verificarsi, ad esempio, quando sono presenti più istanze del modello c \+\+\-style.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugprogram2-enumcodecontexts.md)   
 [EnumCodeContexts](../../../extensibility/debugger/reference/idebugdocumentcontext2-enumcodecontexts.md)