---
title: "IDebugProgram3::ExecuteOnThread | Microsoft Docs"
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
  - "IDebugProgram3::ExecuteOnThread"
ms.assetid: 2f5211e3-7a3f-47bf-9595-dfc8b4895d0d
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugProgram3::ExecuteOnThread
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Esegue il programma del debugger.  Il thread viene restituito per fornire al debugger le informazioni sui quali il thread l'utente accede durante l'esecuzione del programma.  
  
## Sintassi  
  
```cpp#  
HRESULT ExecuteOnThread(  
   [in] IDebugThread2* pThread)  
```  
  
```c#  
int ExecuteOnThread(  
   IDebugThread2 pThread  
);  
```  
  
#### Parametri  
 `pThread`  
 \[in\]  [IDebugThread2](../../../extensibility/debugger/reference/idebugthread2.md) un oggetto.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Esistono tre diverse modalità in cui un debugger può riprendere l'esecuzione dopo aver arrestato:  
  
-   di esecuzione: Annullare qualsiasi passaggio precedente e l'esecuzione fino al punto di interruzione successivo e così via.  
  
-   passaggio: Annullare qualsiasi passaggio precedente ed eseguito fino al nuovo passaggio completo.  
  
-   continuare: Eseguire nuovamente e lasciare qualsiasi attivo recente del passaggio.  
  
 Il thread passato a `ExecuteOnThread` è utile quando si decide quale passaggio da null.  Se non si conosce il thread, eseguendo di annullamento di esecuzione tutti i passi.  A conoscenza del thread, è sufficiente annullare il passaggio del thread attivo.  
  
## Vedere anche  
 [Esegui](../../../extensibility/debugger/reference/idebugprogram2-execute.md)   
 [IDebugProgram3](../../../extensibility/debugger/reference/idebugprogram3.md)