---
title: "IDebugErrorEvent2::GetErrorMessage | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugErrorEvent2::GetErrorMessage"
helpviewer_keywords: 
  - "IDebugErrorEvent2::GetErrorMessage"
ms.assetid: 9e3b0d74-a2dd-4eaa-bd95-21b2f9c79409
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# IDebugErrorEvent2::GetErrorMessage
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Restituisce le informazioni che consentono la costruzione di un messaggio di errore leggibile.  
  
## Sintassi  
  
```cpp#  
HRESULT GetErrorMessage(  
   MESSAGETYPE* pMessageType,  
   BSTR*        pbstrErrorFormat,  
   HRESULT*     hrErrorReason,  
   DWORD*       pdwType,  
   BSTR*        pbstrHelpFileName,  
   DWORD*       pdwHelpId  
);  
```  
  
```c#  
int GetErrorMessage(  
   out enum_MESSAGETYPE   pMessageType,  
   out string             pbstrErrorFormat,  
   out int                phrErrorReason,  
   out uint               pdwType,  
   out string             pbstrHelpFileName,  
   out uint               pdwHelpId  
);  
```  
  
#### Parametri  
 `pMessageType`  
 \[out\]  Restituisce un valore [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md) dell'enumerazione, descrivente il tipo di messaggio.  
  
 `pbstrErrorFormat`  
 \[out\]  Il formato del messaggio all'utente finale \(vedere “commenti„ per i dettagli\).  
  
 `hrErrorReason`  
 \[out\]  Il codice di errore il messaggio è su.  
  
 `pdwType`  
 \[out\]  Gravità dell'errore \(utilizzare le costanti di MB\_XXX per `MessageBox`; ad esempio, `MB_EXCLAMATION` o `MB_WARNING`\).  
  
 `pbstrHelpFileName`  
 \[out\]  Percorso di un file della Guida \(impostata su un valore null se non c " è il file della Guida.  
  
 `pdwHelpId`  
 \[out\]  ID dell'argomento della Guida da visualizzare \(impostato su 0 se non c " è argomento della Guida.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Il messaggio di errore deve essere formattato lungo le linee di `"What I was doing.  %1"`.  `"%1"` sarebbe stato sostituito dal chiamante con il messaggio di errore derivato dal codice di errore \(che viene restituito in `hrErrorReason`\).  Il parametro di `pMessageType` indica al chiamante come messaggio di errore finale deve essere visualizzato.  
  
## Vedere anche  
 [IDebugErrorEvent2](../../../extensibility/debugger/reference/idebugerrorevent2.md)   
 [MESSAGETYPE](../../../extensibility/debugger/reference/messagetype.md)