---
title: PARSEFLAGS | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- PARSEFLAGS
helpviewer_keywords:
- PARSEFLAGS enumeration
ms.assetid: 47943f0a-54cb-4493-a62e-5dba97bd4c35
caps.latest.revision: 9
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
ms.openlocfilehash: 04cf02cc21fd6ae7324267805e89b1454566b9b6
ms.lasthandoff: 02/22/2017

---
# <a name="parseflags"></a>PARSEFLAGS
Specifica la modalità di analisi dell'espressione.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
typedef DWORD PARSEFLAGS;  
```  
  
```c#  
public enum enum_PARSEFLAGS {   
   PARSE_EXPRESSION            = 0x0001,  
   PARSE_FUNCTION_AS_ADDRESS   = 0x0002,  
   PARSE_DESIGN_TIME_EXPR_EVAL = 0x1000  
};  
```  
  
## <a name="members"></a>Membri  
 PARSE_EXPRESSION  
 Indica che l'espressione non è un'istruzione.  
  
 PARSE_FUNCTION_AS_ADDRESS  
 Indica che l'espressione deve essere analizzato (e valutate in un secondo momento) come un indirizzo.  
  
 PARSE_DESIGN_TIME_EXPR_EVAL  
 Indica che l'espressione viene analizzato in fase di progettazione (ovvero, quando una finestra di progettazione è aperta).  
  
## <a name="remarks"></a>Note  
 Passato come parametro per il [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md) e [analizzare](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md) metodi.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [ParseText](../../../extensibility/debugger/reference/idebugexpressioncontext2-parsetext.md)   
 [Analisi](../../../extensibility/debugger/reference/idebugexpressionevaluator-parse.md)
