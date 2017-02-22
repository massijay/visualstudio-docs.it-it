---
title: "IDebugGenericFieldDefinition | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Interfaccia IDebugGenericFieldDefinition"
ms.assetid: b5a853b7-221e-4d62-8948-07423089d75d
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugGenericFieldDefinition
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

rappresenta la definizione di un campo per un tipo generico di codice gestito.  
  
## Sintassi  
  
```  
IDebugGenericFieldDefinition : IUnknown  
```  
  
## Metodi  
 Questa interfaccia implementa i metodi seguenti:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[ConstructInstantiation](../../../extensibility/debugger/reference/idebuggenericfielddefinition-constructinstantiation.md)|Costruisce un'istanza del campo fornita una matrice di argomenti di tipo.|  
|[GetFormalTypeParams](../../../extensibility/debugger/reference/idebuggenericfielddefinition-getformaltypeparams.md)|Recupera i parametri di tipo forniti il numero dei parametri.|  
|[TypeParamCount](../../../extensibility/debugger/reference/idebuggenericfielddefinition-typeparamcount.md)|Recupera il numero di parametri di tipo associati al campo generico.|  
  
## Requisiti  
 intestazione: Sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll