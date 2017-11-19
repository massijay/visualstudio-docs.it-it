---
title: IDebugProgram2::WriteDump | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugProgram2::WriteDump
helpviewer_keywords: IDebugProgram2::WriteDump
ms.assetid: 375afb8c-882d-44db-bfa7-e2c9eb555122
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: b68392d94b16f13106e421c5d466e3fbdf4a2b27
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugprogram2writedump"></a>IDebugProgram2::WriteDump
Scrive un dump in un file.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT WriteDump(   
   DUMPTYPE  DumpType,  
   LPCOLESTR pszDumpUrl  
);  
```  
  
```csharp  
int WriteDump(   
   enum_DUMPTYPE  DumpType,  
   string         pszDumpUrl  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `DumpType`  
 [in] Un valore di [DUMPTYPE](../../../extensibility/debugger/reference/dumptype.md) enumerazione che specifica il tipo di dump, ad esempio, short o long.  
  
 `pszDumpUrl`  
 [in] L'URL per scrivere il dump per. In genere, si tratta sotto forma di `file://c:\path\filename.ext`, ma può essere un URL valido.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## <a name="remarks"></a>Note  
 Un dump del programma in genere include lo stack frame corrente, lo stesso stack, un elenco dei thread in esecuzione nel programma e possibilmente memoria che possiede il programma.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugProgram2](../../../extensibility/debugger/reference/idebugprogram2.md)