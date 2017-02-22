---
title: "IDebugSymbolProvider::GetAddressesFromContext | Microsoft Docs"
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
  - "IDebugSymbolProvider::GetAddressesFromContext"
helpviewer_keywords: 
  - "Metodo IDebugSymbolProvider::GetAddressesFromContext"
ms.assetid: a3124883-a255-4543-a5ec-e1c7a97beb69
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugSymbolProvider::GetAddressesFromContext
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questo metodo esegue il mapping di un contesto di documento in una matrice degli indirizzi di debug.  
  
## Sintassi  
  
```cpp#  
HRESULT GetAddressesFromContext(   
   IDebugDocumentContext2* pDocContext,  
   BOOL                    fStatmentOnly,  
   IEnumDebugAddresses**   ppEnumBegAddresses,  
   IEnumDebugAddresses**   ppEnumEndAddresses  
);  
```  
  
```c#  
int GetAddressesFromContext(  
   IDebugDocumentContext2  pDocContext,  
   bool                    fStatmentOnly,  
   out IEnumDebugAddresses ppEnumBegAddresses,  
   out IEnumDebugAddresses ppEnumEndAddresses  
);  
```  
  
#### Parametri  
 `pDocContext`  
 \[in\]  Il contesto del documento.  
  
 `fStatmentOnly`  
 \[in\]  Se TRUE, limiti di debug è destinato a un'unica istruzione.  
  
 `ppEnumBegAddresses`  
 \[out\]  Restituisce un enumeratore per gli indirizzi iniziali di debug associati a questa istruzione o riga.  
  
 `ppEnumEndAddresses`  
 \[out\]  Restituisce [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md) un enumeratore per gli indirizzi finali di debug associati a questa istruzione o riga.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Un contesto del documento in genere indica un intervallo di righe di codice sorgente.  Questo metodo fornisce gli indirizzi inizianti e terminare di debug associati a tali righe.  Alcuni linguaggi consentono le istruzioni che si estendono in più righe, o le righe che contiene più di un'istruzione.  Questo metodo fornisce un flag per limitare gli indirizzi di debug a una sola istruzione.  
  
 È possibile che una singola istruzione di indirizzi più di debug, come nel caso di modelli.  
  
## Vedere anche  
 [IDebugSymbolProvider](../../../extensibility/debugger/reference/idebugsymbolprovider.md)   
 [GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)   
 [IEnumDebugAddresses](../../../extensibility/debugger/reference/ienumdebugaddresses.md)