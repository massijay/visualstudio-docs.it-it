---
title: IDebugGenericFieldInstance | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: IDebugGenericFieldInstance interface
ms.assetid: f68b4761-be8b-4801-9d4b-cde90e01d95e
caps.latest.revision: "7"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7d7a0a16a6e7eb9f5901cecb5765d1ea2de2fb98
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebuggenericfieldinstance"></a>IDebugGenericFieldInstance
Rappresenta un'istanza di un campo per un tipo generico di codice gestito.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugGenericFieldInstance : IUnknown  
```  
  
## <a name="methods"></a>Metodi  
 Questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[GetTypeArguments](../../../extensibility/debugger/reference/idebuggenericfieldinstance-gettypearguments.md)|Recupera gli argomenti di parametro di tipo per questa istanza.|  
|[TypeArgumentCount](../../../extensibility/debugger/reference/idebuggenericfieldinstance-typeargumentcount.md)|Restituisce il numero del tipo di argomenti di parametro per questa istanza.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: Sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll