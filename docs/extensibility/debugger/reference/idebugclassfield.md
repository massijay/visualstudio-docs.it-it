---
title: IDebugClassField | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugClassField
helpviewer_keywords: IDebugClassField interface
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 7c9c827c8c72ddf323848e9744edbdcda9a51b2f
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugclassfield"></a>IDebugClassField
Questa interfaccia rappresenta una classe come un tipo.  
  
## <a name="syntax"></a>Sintassi  
  
```  
IDebugClassField : IDebugContainerField  
```  
  
## <a name="notes-for-implementers"></a>Note per gli implementatori  
 Un provider di simboli implementa questa interfaccia sullo stesso oggetto che implementa il [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaccia. Questa interfaccia è una specializzazione che rappresenta un tipo di classe.  
  
## <a name="notes-for-callers"></a>Note per i chiamanti  
 Un numero di interfacce dispone di metodi che possono restituire questa interfaccia inclusi [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md), e [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md). Inoltre, è possibile utilizzare [QueryInterface](/cpp/atl/queryinterface) per questa interfaccia da ottenere il [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfaccia se il [GetKind](../../../extensibility/debugger/reference/idebugfield-getkind.md) il metodo restituisce un flag di `FIELD_TYPE_CLASS`.  
  
## <a name="methods-in-vtable-order"></a>Metodi nell'ordine Vtable  
 Oltre ai metodi nel [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) interfacce, questa interfaccia implementa le operazioni seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EnumBaseClasses](../../../extensibility/debugger/reference/idebugclassfield-enumbaseclasses.md)|Crea un enumeratore per le classi di base di questa classe.|  
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Determina se un'interfaccia specifica è definita nella classe.|  
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Crea un enumeratore per le classi annidate di questa classe.|  
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Ottiene la classe che include questa classe.|  
|[EnumInterfacesImplemented](../../../extensibility/debugger/reference/idebugclassfield-enuminterfacesimplemented.md)|Crea un enumeratore per le interfacce implementate da questa classe.|  
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Crea un enumeratore per i costruttori di questa classe.|  
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Ottiene il nome dell'indicizzatore predefinita.|  
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Crea un enumeratore per gli enumeratori annidati di questa classe.|  
  
## <a name="requirements"></a>Requisiti  
 Intestazione: sh.h  
  
 Namespace: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## <a name="see-also"></a>Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)