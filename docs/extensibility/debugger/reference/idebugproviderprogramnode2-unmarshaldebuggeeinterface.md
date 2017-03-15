---
title: "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface"
helpviewer_keywords: 
  - "IDebugProviderProgramNode2::UnmarshalDebuggeeInterface"
ms.assetid: 2e4653c5-10f1-493c-9973-f31d266c5d48
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProviderProgramNode2::UnmarshalDebuggeeInterface
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene un'interfaccia specificata mediante i limiti dei processi.  
  
## Sintassi  
  
```cpp  
HRESULT UnmarshalDebuggeeInterface(  
   REFIID riid,  
   void** ppvObject  
);  
```  
  
```c#  
int UnmarshalDebuggeeInterface(  
   ref Guid   riid,  
   out IntPtr ppvObject  
);  
```  
  
#### Parametri  
 `riid`  
 \[in\]  GUID dell'interfaccia da verificare.  
  
 `ppvObject`  
 \[out\]  restituisce l'oggetto che implementa l'interfaccia desiderata.  \[C\+\+\] questo può essere impostato direttamente al tipo di interfaccia desiderato.  \[C\#\] utilizzare il metodo di <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> per ottenere l'interfaccia desiderata.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo viene utilizzato quando il motore di debug è in esecuzione nello spazio di processo di [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] e il programma sottoposto a debug è in esecuzione nel relativo spazio del processo.  
  
## Vedere anche  
 [IDebugProviderProgramNode2](../../../extensibility/debugger/reference/idebugproviderprogramnode2.md)