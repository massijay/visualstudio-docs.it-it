---
title: "IDebugAddress | Microsoft Docs"
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
  - "IDebugAddress"
helpviewer_keywords: 
  - "Interfaccia IDebugAddress"
ms.assetid: bc709ff7-4966-4f36-9af2-690efe2cea1d
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugAddress
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

questa interfaccia rappresenta l'indirizzo di un elemento.  Viene restituita dal gestore dei simboli.  
  
## Sintassi  
  
```  
IDebugAddress : IUnknown  
```  
  
## Note per gli implementatori  
 Un provider del simbolo implementa questa interfaccia per rappresentare un indirizzo di un oggetto.  
  
## Note per i chiamanti  
 Molti metodi in molte interfacce restituiscono questa interfaccia.  
  
## Metodi nell'ordine di Vtable  
 questa interfaccia implementa il seguente metodo:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)|Recupera [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md) una struttura che descrive un oggetto e la relativa posizione.|  
  
## Note  
 Il provider del simbolo restituisce questa interfaccia per rappresentare un oggetto e la relativa posizione all'interno di un determinato ambito, ad esempio funzione, metodo, o classe\).  Questa interfaccia viene restituita da e viene passata ai vari metodi del provider e l'analizzatore di espressioni del simbolo.  In genere, il provider del simbolo è l'unica entità che deve interpretare il contenuto dell'interfaccia.  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [DEBUG\_ADDRESS](../../../extensibility/debugger/reference/debug-address.md)