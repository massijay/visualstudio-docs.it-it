---
title: DUMPTYPE | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DUMPTYPE
helpviewer_keywords: DUMPTYPE enumeration
ms.assetid: ea8160db-8732-4056-a1d7-892ef72da71e
caps.latest.revision: "10"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 26e2836215ac5563a6ebaefb9d31d682348c7e89
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="dumptype"></a>DUMPTYPE
Specifica la quantità di stato di un programma (ad esempio un thread in esecuzione, gli stack frame e indirizzo dell'istruzione corrente) per eseguire il dump.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
typedef DWORD DUMPTYPE;  
```  
  
```csharp  
public enum enum_DUMPTYPE {   
   DUMP_MINIDUMP = 0,  
   DUMP_FULLDUMP = 1  
};  
```  
  
## <a name="members"></a>Membri  
 DUMP_MINIDUMP  
 Specifica un dump compatto.  
  
 DUMP_FULLDUMP  
 Specifica un dump completo e di grandi dimensioni.  
  
## <a name="remarks"></a>Note  
 Passata come argomento per il [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md) metodo.  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: msdbg.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Enumerazioni](../../../extensibility/debugger/reference/enumerations-visual-studio-debugging.md)   
 [WriteDump](../../../extensibility/debugger/reference/idebugprogram2-writedump.md)