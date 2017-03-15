---
title: "IDebugEnumField::GetValueFromString | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugEnumField::GetValueFromString"
helpviewer_keywords: 
  - "Metodo IDebugEnumField::GetValueFromString"
ms.assetid: 1ef8ac5e-a3e0-4078-b876-7f5615aedcbb
caps.latest.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 7
---
# IDebugEnumField::GetValueFromString
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo restituisce il valore associato al nome di una costante di enumerazione.  
  
## Sintassi  
  
```cpp#  
HRESULT GetValueFromString(  
   LPCOLESTR  pszValue,  
   ULONGLONG* pvalue  
);  
```  
  
```c#  
int GetValueFromString(  
   string    pszValue,  
   out ulong pValue  
);  
```  
  
#### Parametri  
 `pszValue`  
 \[in\]  Una stringa che specifica il nome per il quale ottenere il valore.  Si noti che per C\+\+, questo è una stringa di caratteri estesi.  
  
 `pValue`  
 \[out\]  restituisce il valore numerico associato.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE`, se il nome non fa parte dell'enumerazione, o un codice di errore.  
  
## Note  
 Questo metodo distingue tra maiuscole e minuscole.  Se una ricerca senza distinzione tra maiuscole e minuscole è necessaria \(ad esempio, in un linguaggio ad esempio Visual Basic dove i nomi non viene fatta distinzione tra maiuscole e minuscole\), utilizzare [GetValueFromStringCaseInsensitive](../Topic/IDebugEnumField::GetValueFromStringCaseInsensitive.md).  
  
## Vedere anche  
 [IDebugEnumField](../../../extensibility/debugger/reference/idebugenumfield.md)   
 [GetValueFromStringCaseInsensitive](../Topic/IDebugEnumField::GetValueFromStringCaseInsensitive.md)