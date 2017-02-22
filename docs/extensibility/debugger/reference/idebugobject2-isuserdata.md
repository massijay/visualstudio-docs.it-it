---
title: "IDebugObject2::IsUserData | Microsoft Docs"
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
  - "IDebugObject2::IsUserData"
helpviewer_keywords: 
  - "Metodo IDebugObject2::IsUserData"
ms.assetid: 6ffa0d0e-f742-496d-acc7-db74c248bc45
caps.latest.revision: 7
caps.handback.revision: 7
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugObject2::IsUserData
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Determina se l'oggetto rappresenta i dati utente.  
  
## Sintassi  
  
```cpp  
HRESULT IsUserData(  
   BOOL* pfUser  
);  
```  
  
```c#  
int IsUserData(  
   out int pfUser  
);  
```  
  
#### Parametri  
 `pfUser`  
 \[out\]  Restituisce diverso da zero \(`TRUE`\) se l'oggetto rappresenta i dati utente; zero \(`FALSE`\) in caso contrario.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, in caso contrario, restituisce un codice di errore.  
  
## Note  
 I dati utente è qualsiasi oggetto che fa parte di un modulo definito come JustMyCode \(un'opzione utente\-configurabile che contrassegna un modulo come codice utente e quindi visibile in una traccia dello stack\).  
  
## Vedere anche  
 [IDebugObject2](../../../extensibility/debugger/reference/idebugobject2.md)