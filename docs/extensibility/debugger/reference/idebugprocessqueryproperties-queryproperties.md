---
title: "IDebugProcessQueryProperties::QueryProperties | Microsoft Docs"
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
  - "IDebugProcessQueryProperties::QueryProperties"
ms.assetid: 976a9962-b689-45bb-afb6-16b2c5dbc3b8
caps.latest.revision: 5
caps.handback.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcessQueryProperties::QueryProperties
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Query di questo metodo per valori di proprietà specifici del processo di debug.  
  
## Sintassi  
  
```cpp#  
HRESULT QueryProperties(  
   ULONG                  celt,  
   PROCESS_PROPERTY_TYPE *rgdwPropTypes,  
   VARIANT               *rgtPropValues);  
```  
  
```c#  
int QueryProperties(  
   uint                       celt,  
   enum_PROCESS_PROPERTY_TYPE rgdwPropTypes,  
   out object[ ]              rgtPropValues);  
```  
  
#### Parametri  
 `celt`  
 \[in\]  Dimensione delle matrici contenenti le definizioni e i valori delle proprietà.  
  
 `dwPropType`  
 \[in\]  Una matrice contenente le definizioni delle proprietà per eseguire una query.  I valori possibili sono:  
  
-   PROCESS\_PROPERTY\_COMMAND\_LINE \= 1  
  
-   PROCESS\_PROPERTY\_CURRENT\_DIRECTORY \= 2  
  
-   PROCESS\_PROPERTY\_ENVIRONMENT\_VARIABLES \= 3  
  
 `pvarPropValue`  
 \[out\]  Una matrice contenente i valori della proprietà.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo viene utilizzata raramente.  
  
## Vedere anche  
 [IDebugProcessQueryProperties](../../../extensibility/debugger/reference/idebugprocessqueryproperties.md)