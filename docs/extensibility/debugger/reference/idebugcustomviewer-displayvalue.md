---
title: IDebugCustomViewer::DisplayValue | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: IDebugCustomViewer::DisplayValue
helpviewer_keywords: IDebugCustomViewer::DisplayValue
ms.assetid: 7a538248-5ced-450e-97cd-13fabe35fb1c
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 701c5e33273dc6d00156e554e1abaa9a003568eb
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="idebugcustomviewerdisplayvalue"></a>IDebugCustomViewer::DisplayValue
Questo metodo viene chiamato per visualizzare il valore specificato.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT DisplayValue(  
   HWND             hwnd,  
   DWORD            dwID,  
   IUnknown *       pHostServices,  
   IDebugProperty3* pDebugProperty);  
);  
```  
  
```csharp  
int DisplayValue(  
   IntPtr          hwnd,   
   uint            dwID,   
   object          pHostServices,   
   IDebugProperty3 pDebugProperty  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `hwnd`  
 [in] Finestra padre  
  
 `dwID`  
 [in] ID per i visualizzatori personalizzati che supportano più di un tipo.  
  
 `pHostServices`  
 [in] Riservato. Sempre impostata su null.  
  
 `pDebugProperty`  
 [in] Interfaccia che può essere utilizzato per recuperare il valore da visualizzare.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce il codice di errore.  
  
## <a name="remarks"></a>Note  
 La visualizzazione è "modale" in questo metodo verrà creare una finestra degli strumenti necessaria, visualizzare il valore, attendere l'input e chiudere la finestra, tutte prima di restituire al chiamante. Ciò significa che il metodo deve gestire tutti gli aspetti del valore della proprietà, la creazione di una finestra di output, in attesa di input dell'utente per l'eliminazione della finestra di visualizzazione.  
  
 Per supportare la modifica del valore sul determinato [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) dell'oggetto, è possibile utilizzare il [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md) (metodo), se il valore può essere espresso come stringa. In caso contrario, è necessario creare un'interfaccia personalizzata, esclusivo per l'analizzatore di espressioni l'implementazione di questa `DisplayValue` (metodo), sullo stesso oggetto che implementa il `IDebugProperty3` interfaccia. Questa interfaccia personalizzata verrà forniti metodi per modificare i dati di una dimensione arbitraria o complessità.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCustomViewer](../../../extensibility/debugger/reference/idebugcustomviewer.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)   
 [SetValueAsStringWithError](../../../extensibility/debugger/reference/idebugproperty3-setvalueasstringwitherror.md)