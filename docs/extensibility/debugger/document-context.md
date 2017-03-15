---
title: Contesto del documento | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], contexts
ms.assetid: 8e8b5702-5c16-4988-953d-69dd807d8b84
caps.latest.revision: 10
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
ms.openlocfilehash: 8ed5498961a575d0f9d3f7c64b46bc73a2d510b5
ms.lasthandoff: 02/22/2017

---
# <a name="document-context"></a>Contesto del documento
In [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] il debug, un **contesto del documento**:  
  
-   Rappresenta una posizione in un file di origine. Per le lingue in cui il file di origine non siano presente, un contesto di documento identifica una posizione in un documento in genere generato dall'ambiente di runtime. Ad esempio, un motore di script potrebbe generare un documento da script. Per ulteriori informazioni, vedere [posizione documento](../../extensibility/debugger/document-position.md).  
  
-   Descrive una posizione in un documento di origine che corrisponde a un contesto di codice. Il gestore dei simboli esegue il mapping di un contesto di codice al contesto di documentazione, utilizzando le informazioni generate dal compilatore o interprete.  
  
-   Viene implementata da un [IDebugDocumentContext2](../../extensibility/debugger/reference/idebugdocumentcontext2.md) interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 [Contesto del codice](../../extensibility/debugger/code-context.md)   
 [Provider di simboli](../../extensibility/debugger/symbol-provider.md)   
 [Interfacce del Provider di simboli](../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [Contesti di debugger](../../extensibility/debugger/debugger-contexts.md)
