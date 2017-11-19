---
title: I server (Visual Studio SDK) | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- servers, debugging
- debugging [Debugging SDK], servers
ms.assetid: 62236d64-7956-448c-9ac3-5528f3edac1d
caps.latest.revision: "17"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 496e9b361dbb7f5c3eb5cf5197a1351a1182af3e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="servers-visual-studio-sdk"></a>Server (Visual Studio SDK)
In termini di architettura del debugger, un **server**:  
  
-   È un contenitore di porte e i fornitori di porte e viene utilizzato per comunicare le porte e i fornitori di porte con gestore di sessione di debug (SDM) e motori di debug.  
  
-   Possibile identificarsi in base al nome ed enumerare le porte e i fornitori di porte.  
  
-   È rappresentato da un [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md) interfaccia, che viene implementato solo da Visual Studio (un'istanza di un server per ogni istanza di esecuzione di Visual Studio).  
  
## <a name="see-also"></a>Vedere anche  
 [Porte](../../extensibility/debugger/ports.md)   
 [Fornitori di porte](../../extensibility/debugger/port-suppliers.md)   
 [Concetti di debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugCoreServer2](../../extensibility/debugger/reference/idebugcoreserver2.md)