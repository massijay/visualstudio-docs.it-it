---
title: "IDebugProcess3::SetHostingProcessLanguage | Microsoft Docs"
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
  - "IDebugProcess3::SetHostingProcessLanguage"
helpviewer_keywords: 
  - "IDebugProcess3::SetHostingProcessLanguage"
ms.assetid: e42f33ed-f29c-4e45-92ce-ab504b72d77c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProcess3::SetHostingProcessLanguage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo imposta il linguaggio che il processo verrà incluso in.  Questo linguaggio che può quindi essere utilizzato dal motore di \(DE\) debug per caricare l'analizzatore di espressioni appropriato.  
  
## Sintassi  
  
```cpp  
HRESULT SetHostingProcessLanguage(  
   REFGUID guidLang  
);  
```  
  
```c#  
int SetHostingProcessLanguage(  
   ref Guid guidLang  
);  
```  
  
#### Parametri  
 `guidLang`  
 \[in\]  `GUID` il linguaggio che il DE deve utilizzare.  Specificare `GUID_NULL` \(C\+\+\) o `Guid.Empty` \(c\#\) per effettuare utilizzare il DE la lingua predefinita.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, codice di errore restituito.  
  
## Note  
 [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md) può essere utilizzato per recuperare il valore corrente della lingua.  
  
## Vedere anche  
 [IDebugProcess3](../../../extensibility/debugger/reference/idebugprocess3.md)   
 [GetHostingProcessLanguage](../../../extensibility/debugger/reference/idebugprocess3-gethostingprocesslanguage.md)