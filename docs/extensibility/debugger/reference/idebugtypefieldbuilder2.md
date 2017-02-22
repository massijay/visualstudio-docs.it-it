---
title: "IDebugTypeFieldBuilder2 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaccia IDebugTypeFieldBuilder2"
ms.assetid: 23911c5b-2bbf-4734-9976-87a0bd6ea36c
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugTypeFieldBuilder2
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Estende **il IDebugTypeFieldBuilder** per poter creare tipi di matrice.  
  
## Sintassi  
  
```  
IDebugTypeFieldBuilder2 : IDebugTypeFieldBuilder  
```  
  
## Note per i chiamanti  
 Tale interfaccia può essere ottenuta dal provider del simbolo.  
  
## Metodi  
 Oltre ai metodi [IDebugTypeFieldBuilder](../../../extensibility/debugger/reference/idebugtypefieldbuilder.md) in un'interfaccia, l'interfaccia implementa il seguente metodo:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[CreateArrayOfType](../../../extensibility/debugger/reference/idebugtypefieldbuilder2-createarrayoftype.md)|Crea una matrice di tipo e le dimensioni specificate.|  
  
## Requisiti  
 intestazione: Sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll