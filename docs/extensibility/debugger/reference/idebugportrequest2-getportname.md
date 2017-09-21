---
title: "IDebugPortRequest2::GetPortName | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugPortRequest2::GetPortName"
helpviewer_keywords: 
  - "IDebugPortRequest2::GetPortName"
ms.assetid: 53e2a3a4-bb34-4a02-a983-6bd84ea70587
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugPortRequest2::GetPortName
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene il nome della porta.  
  
## Sintassi  
  
```cpp#  
HRESULT GetPortName(   
   BSTR* pbstrPortName  
);  
```  
  
```c#  
int GetPortName(   
   out string pbstrPortName  
);  
```  
  
#### Parametri  
 `pbstrPortName`  
 \[out\]  Restituisce il nome della porta.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md) L'interfaccia viene in genere passata da un pacchetto di debug \(il client\) a un fornitore di porte \(il server\) per ottenere una connessione a una porta.  Sia il pacchetto di debug e il fornitore di porte in grado di scelte possibili per la porta.  Se una stringa semplice possibile descrivere la porta, il metodo di `IDebugPortRequest2::GetPortName` dispone di informazioni sufficienti per effettuare la connessione.  In caso contrario, le interfacce aggiuntive possono essere fornite dal client, che può essere ottenuto dal server utilizzando `IDebugPortRequest2::QueryInterface`.  
  
## Vedere anche  
 [IDebugPortRequest2](../../../extensibility/debugger/reference/idebugportrequest2.md)