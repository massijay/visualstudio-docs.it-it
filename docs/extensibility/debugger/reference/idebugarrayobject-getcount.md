---
title: "IDebugArrayObject::GetCount | Microsoft Docs"
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
  - "IDebugArrayObject::GetCount"
helpviewer_keywords: 
  - "Metodo IDebugArrayObject::GetCount"
ms.assetid: 7931f3f7-033c-4bf8-8abd-95183952ebb0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugArrayObject::GetCount
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il numero degli elementi nella matrice.  
  
## Sintassi  
  
```  
[C++]  
HRESULT GetCount(   
   DWORD* pdwElements  
);  
```  
  
```  
[C#]  
int GetCount(  
   out uint pdwElements  
);  
```  
  
#### Parametri  
 `pdwElements`  
 \[out\]  Restituisce il numero.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo visualizza tutti gli elementi di un oggetto matrice come matrice unidimensionale, anche se l'oggetto matrice è multidimensionale.  Ad esempio, data la matrice `myarray[3][2][6]`, questo metodo restituisce 36 nel parametro di `pdwElements` .  Utilizzare [GetElement](../Topic/IDebugArrayObject::GetElement.md) il metodo per recuperare i singoli elementi per volta.  
  
## Vedere anche  
 [IDebugArrayObject](../../../extensibility/debugger/reference/idebugarrayobject.md)