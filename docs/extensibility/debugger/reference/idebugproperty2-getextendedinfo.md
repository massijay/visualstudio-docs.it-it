---
title: "IDebugProperty2::GetExtendedInfo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugProperty2::GetExtendedInfo"
helpviewer_keywords: 
  - "IDebugProperty2::GetExtendedInfo"
ms.assetid: 0c9c0b2b-7540-4424-adb5-fce7aa37a026
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugProperty2::GetExtendedInfo
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Ottiene informazioni estese per la proprietà.  
  
## Sintassi  
  
```cpp#  
HRESULT GetExtendedInfo (   
   REFGUID* guidExtendedInfo,  
   VARIANT* pExtendedInfo  
);  
```  
  
```c#  
int GetExtendedInfo (   
   ref Guid guidExtendedInfo,  
   out object pExtendedInfo  
);  
```  
  
#### Parametri  
 `guidExtendedInfo`  
 \[in\]  GUID che determina il tipo di informazioni estese da recuperare.  Vedere le note per i dettagli.  
  
 `pExtendedInfo`  
 \[out\]  Restituisce `VARIANT` \(C\+\+\) oggetto o \(c\#\) che può essere utilizzato per recuperare le informazioni della proprietà estesa.  Ad esempio, questo parametro può restituire un'interfaccia di `IUnknown` che è possibile eseguire una query per [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) l'interfaccia.  Vedere le note per i dettagli.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce `S_OK`; in caso contrario restituisce il codice di errore.  Restituisce `S_GETEXTENDEDINFO_NO_EXTENDEDINFO` se non sono presenti informazioni estese da recuperare.  
  
## Note  
 Questo metodo esistente ai fini di recuperare le informazioni che non si prestano a essere recuperato chiamando [GetPropertyInfo](../../../extensibility/debugger/reference/idebugproperty2-getpropertyinfo.md) il metodo.  
  
 I seguenti GUID in genere vengono riconosciuti da questo metodo \(i valori di GUID sono specificati per c\# poiché il nome non è disponibile negli assembly\).  i GUID aggiuntivi possono essere creati per utilizzo interno.  
  
|Nome|GUID|Descrizione|  
|----------|----------|-----------------|  
|guidDocument|{} 3f98de84\-fee9\-11d0\-b47f\-00a0244a1dd2|Restituisce un'interfaccia di `IUnknown` al documento.  in genere, [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md) l'interfaccia può essere ottenuta da questa interfaccia di `IUnknown` .|  
|guidCodeContext|{} e2fc65e\-56ce\-11d1\-b528\-00aax004a8797|Restituisce un'interfaccia di `IUnknown` al contesto del documento.  in genere, [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md) l'interfaccia può essere ottenuta da questa interfaccia di `IUnknown` .|  
|guidCustomViewerSupported|{} d9c9da31\-ffbe\-4eeb\-9186\-23121e3c088c|Restituisce una stringa contenente il CLSID di un visualizzatore personalizzato, in genere implementata da un analizzatore di espressioni.|  
|guidExtendedInfoSlot|{} 6df235ad\-82c6\-4292\-9c97\-7389770bc42f|Restituisce un numero a 32 bit che rappresenta il numero di slot desiderato se questa proprietà rappresenta un indirizzo locale di codice gestito.|  
|guidExtendedInfoSignature|{} b5fb6d46\-f805\-417f\-96a3\-8ba737073ffd|Restituisce una stringa contenente la firma della variabile associata all'oggetto della proprietà.|  
  
## Vedere anche  
 [IDebugProperty2](../../../extensibility/debugger/reference/idebugproperty2.md)   
 [IDebugDocumentText2](../../../extensibility/debugger/reference/idebugdocumenttext2.md)   
 [IDebugDocumentContext2](../../../extensibility/debugger/reference/idebugdocumentcontext2.md)