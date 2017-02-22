---
title: "IDebugSymbolProvider::GetClassTypeByName | Microsoft Docs"
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
  - "IDebugSymbolProvider::GetClassTypeByName"
helpviewer_keywords: 
  - "Metodo IDebugSymbolProvider::GetClassTypeByName"
ms.assetid: 2c748909-51dc-49b7-b193-19f96fca1138
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProvider::GetClassTypeByName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo ottiene il tipo di campo della classe che rappresenta un nome di classe completo.  
  
## Sintassi  
  
```cpp#  
HRESULT GetClassTypeByName(   
   LPCOLESTR          pszClassName,  
   NAME_MATCH         nameMatch,  
   IDebugClassField** ppField  
);  
```  
  
```c#  
int GetClassTypeByName(  
   string               pszClassName,   
   NAME_MATCH           nameMatch,   
   out IDebugClassField ppField  
);  
```  
  
#### Parametri  
 `pszClassName`  
 \[in\]  Il nome della classe.  
  
 `nameMatch`  
 \[in\]  Selezionare il tipo di corrispondenza, ad esempio, la distinzione tra maiuscole e minuscole.  Valore ottenuto dall'enumerazione [NAME\_MATCH](../../../extensibility/debugger/reference/name-match.md).  
  
 `ppField`  
 \[out\]  Restituisce il tipo della classe come rappresentato [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md) dall'interfaccia.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Vedere anche  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [NAME\_MATCH](../../../extensibility/debugger/reference/name-match.md)   
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)