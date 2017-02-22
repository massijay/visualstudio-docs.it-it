---
title: "IDebugClassField | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugClassField"
helpviewer_keywords: 
  - "Interfaccia IDebugClassField"
ms.assetid: 49358cbc-8973-4862-9dcc-79b1248e6712
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta la classe come tipo.  
  
## Sintassi  
  
```  
IDebugClassField : IDebugContainerField  
```  
  
## Note per gli implementatori  
 Un provider del simbolo implementa questa interfaccia lo stesso oggetto che implementa [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) l'interfaccia.  Questa interfaccia è una specializzazione che rappresenta il tipo della classe.  
  
## Note per i chiamanti  
 Una serie di interfacce dispongono di metodi che possono restituire questa interfaccia inclusi [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md), [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)e [IDebugCustomAttribute](../../../extensibility/debugger/reference/idebugcustomattribute.md).  Inoltre, è possibile utilizzare [QueryInterface](/visual-cpp/atl/queryinterface) per ottenere questa interfaccia [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) ISAPI se [GetKind](../Topic/IDebugField::GetKind.md) il metodo restituisce il flag `FIELD_TYPE_CLASS`.  
  
## Metodi nell'ordine di Vtable  
 Oltre ai metodi [IDebugField](../../../extensibility/debugger/reference/idebugfield.md) e [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md) le interfacce, l'interfaccia implementa le operazioni seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[EnumBaseClasses](../Topic/IDebugClassField::EnumBaseClasses.md)|Crea un enumeratore per le classi base di questa classe.|  
|[DoesInterfaceExist](../../../extensibility/debugger/reference/idebugclassfield-doesinterfaceexist.md)|Determina se una specifica interfaccia è definita nella classe.|  
|[EnumNestedClasses](../../../extensibility/debugger/reference/idebugclassfield-enumnestedclasses.md)|Crea un enumeratore per le classi annidate di questa classe.|  
|[GetEnclosingClass](../../../extensibility/debugger/reference/idebugclassfield-getenclosingclass.md)|Ottiene la classe che racchiude questa classe.|  
|[EnumInterfacesImplemented](../Topic/IDebugClassField::EnumInterfacesImplemented.md)|crea un enumeratore per le interfacce implementate da questa classe.|  
|[EnumConstructors](../../../extensibility/debugger/reference/idebugclassfield-enumconstructors.md)|Crea un enumeratore per i costruttori della classe.|  
|[GetDefaultIndexer](../../../extensibility/debugger/reference/idebugclassfield-getdefaultindexer.md)|Ottiene il nome dell'indicizzatore predefinito.|  
|[EnumNestedEnums](../../../extensibility/debugger/reference/idebugclassfield-enumnestedenums.md)|Crea un enumeratore per gli enumeratori annidati di questa classe.|  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)   
 [IDebugContainerField](../../../extensibility/debugger/reference/idebugcontainerfield.md)