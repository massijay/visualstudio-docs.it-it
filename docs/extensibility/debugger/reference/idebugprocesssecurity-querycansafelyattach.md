---
title: "IDebugProcessSecurity::QueryCanSafelyAttach | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "IDebugProcessSecurity::QueryCanSafelyAttach"
ms.assetid: 63ec1ae8-27da-4574-aa15-1c986fe9fe58
caps.latest.revision: 4
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 4
---
# IDebugProcessSecurity::QueryCanSafelyAttach
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo consente al fornitore di porte visualizzare un avviso prima che si connette utente a un processo non sicuro.  
  
## Sintassi  
  
```cpp#  
HRESULT QueryCanSafelyAttach();  
```  
  
```c#  
int QueryCanSafelyAttach();  
```  
  
## Valore restituito  
 I valori restituiti sono le seguenti:  
  
-   `S_OK`: Allegare da elaborare è sicuro e alcuna finestra di dialogo di avviso viene visualizzata.  
  
-   `S_FALSE`: La connessione potrebbe esserci un problema di sicurezza e una finestra di dialogo contenente un avviso viene visualizzata.  
  
-   `FAILURE`: Allegare per l'elaborazione avrà esito negativo.  
  
## Vedere anche  
 [IDebugProcessSecurity](../../../extensibility/debugger/reference/idebugprocesssecurity.md)