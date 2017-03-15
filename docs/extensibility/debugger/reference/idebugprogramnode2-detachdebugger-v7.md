---
title: IDebugProgramNode2::DetachDebugger_V7 | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugProgramNode2::DetachDebugger
helpviewer_keywords:
- IDebugProgramNode2::DetachDebugger
- IDebugProgramNode2::DetachDebugger_V7
ms.assetid: d2d4b78e-a2dd-4217-97a6-ab648fd2ee2f
caps.latest.revision: 11
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
ms.openlocfilehash: ea8843a824eb5e1cd0c7bcd658908d7cdaac98ce
ms.lasthandoff: 02/22/2017

---
# <a name="idebugprogramnode2detachdebuggerv7"></a>IDebugProgramNode2::DetachDebugger_V7
DEPRECATO. NON UTILIZZARE.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT DetachDebugger_V7 (   
   void   
);  
```  
  
```c#  
int DetachDebugger_V7 ();  
```  
  
## <a name="return-value"></a>Valore restituito  
 Un'implementazione deve sempre restituire `E_NOTIMPL`.  
  
## <a name="remarks"></a>Note  
  
> [!WARNING]
>  A partire da [!INCLUDE[vsprvslong](../../../code-quality/includes/vsprvslong_md.md)], questo metodo non viene più utilizzato e deve sempre restituire `E_NOTIMPL`.  
  
 Questo metodo viene chiamato quando il debugger viene chiuso. Quando questo metodo viene chiamato, il DE deve essere ripreso il programma come se l'utente è disconnesso da esso. Nessun evento di debug più deve essere inviato. Il programma deve essere in uno stato in cui è associabile da un'altra istanza del debugger.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgramNode2](../../../extensibility/debugger/reference/idebugprogramnode2.md)
