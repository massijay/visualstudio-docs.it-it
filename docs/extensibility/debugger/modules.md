---
title: "Moduli | Microsoft Docs"
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
  - "moduli"
  - "il debug di moduli [debug SDK]"
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Moduli
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In termini di architettura del debugger, **un modulo**:  
  
-   È un contenitore fisico del codice, ad esempio un file eseguibile o una DLL.  
  
-   Possibile ricaricare i simboli e autodescriversi.  Le descrizioni del modulo visualizzate nella finestra moduli dell'IDE.  
  
-   È rappresentato da un'interfaccia di [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) , creata dal motore di debug per descrivere il modulo.  
  
## Vedere anche  
 [Concetti del debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)