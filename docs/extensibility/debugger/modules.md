---
title: I moduli | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- modules
- debugging [Debugging SDK], modules
ms.assetid: c4cf2809-dbdb-4e75-9273-b3d3d77b67d0
caps.latest.revision: "9"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c363ea8809449118782597e68f60637f296af89f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="modules"></a>Moduli
In termini di architettura del debugger, un **modulo**:  
  
-   È un contenitore fisico di codice, ad esempio un file eseguibile o una DLL.  
  
-   Possibile ricaricare i simboli e descrivere se stesso. Descrizioni dei moduli vengono visualizzati nella finestra moduli dell'IDE.  
  
-   È rappresentato da un [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md) interfaccia, creato da un motore di debug per descrivere il modulo.  
  
## <a name="see-also"></a>Vedere anche  
 [Concetti di debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugModule2](../../extensibility/debugger/reference/idebugmodule2.md)