---
title: Porta Suppliers | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- port suppliers
- debugging [Debugging SDK], port suppliers
ms.assetid: a8f3db96-1a13-4e93-9ef6-0861880369e0
caps.latest.revision: 15
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: bd603588a47f565f7f1d177c0740c3289afc8d7e
ms.lasthandoff: 02/22/2017

---
# <a name="port-suppliers"></a>Fornitori di porte
In termini di architettura debugger, un **fornitore della porta**:  
  
-   È contenuto da un server e vengono fornite le porte su richiesta al server.  
  
-   Può aggiungere e rimuovere le porte dal server che lo contiene.  
  
-   Possibile enumerare tutte le porte che è fornito per il server.  
  
-   È rappresentato da un [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md) interfaccia, che è stato registrato con Visual Studio tramite il Registro di sistema. Questa interfaccia può essere ottenuta chiamando [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]fornisce un fornitore di porta predefinito e una porta predefinita. Se una porta personalizzata deve essere implementato, un fornitore di porta personalizzato deve inoltre essere implementati per fornire tali porte personalizzate.  
  
## <a name="see-also"></a>Vedere anche  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Porte](../../extensibility/debugger/ports.md)   
 [Concetti del debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPortSupplier2](../../extensibility/debugger/reference/idebugportsupplier2.md)   
 [GetPortSupplier](../../extensibility/debugger/reference/idebugcoreserver2-getportsupplier.md)
