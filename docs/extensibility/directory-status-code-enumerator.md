---
title: Enumeratore di codice di stato directory | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- directory status code enumerator
- source control plug-ins, directory status enumeration
ms.assetid: 616026b5-f529-40ef-90c1-1836e116d797
caps.latest.revision: 13
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
ms.openlocfilehash: 9cee432270a31eacbcbd09d80d861aadbf7bc3f2
ms.lasthandoff: 02/22/2017

---
# <a name="directory-status-code-enumerator"></a>Enumeratore di codice di stato directory
Il `SccDirStatus` enumeratore contiene valori costanti denominati che specificano lo stato di una directory nel sistema di controllo di origine. Questa enumerazione viene utilizzata per la [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md). Questo è stato introdotto nella versione 1.2 dell'API dei plug-in controllo di origine.  
  
## <a name="syntax"></a>Sintassi  
  
```  
enum SccDirStatus {  
   SCC_DIRSTATUS_INVALID       = -1L,  
   SCC_DIRSTATUS_NOTCONTROLLED = 0x0000L,  
   SCC_DIRSTATUS_CONTROLLED    = 0x0001L,  
   SCC_DIRSTATUS_EMPTYPROJ     = 0x0002L  
};  
```  
  
## <a name="members"></a>Membri  
 SCC_DIRSTATUS_INVALID  
 Non è stato possibile ottenere lo stato; non fare affidamento su di esso.  
  
 SCC_DIRSTATUS_NOTCONTROLLED  
 Directory non è incluso nel controllo del codice sorgente.  
  
 SCC_DIRSTATUS_CONTROLLED  
 Directory si trova sotto controllo del codice sorgente.  
  
 SCC_DIRSTATUS_EMPTYPROJ  
 Progetto corrispondente a questa directory è vuota.  
  
## <a name="see-also"></a>Vedere anche  
 [Plug-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)   
 [SccDirQueryInfo](../extensibility/sccdirqueryinfo-function.md)
