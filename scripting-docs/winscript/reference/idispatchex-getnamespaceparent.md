---
title: "IDispatchEx::GetNameSpaceParent | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IDispatchEx.GetNameSpaceParent
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Metodo GetNamespacesParent"
ms.assetid: 0b077d39-2fd6-4390-8cd5-128d9b8dc90c
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IDispatchEx::GetNameSpaceParent
Recupera l'interfaccia per il padre di spazio dei nomi di un oggetto.  
  
## Sintassi  
  
```  
HRESULT GetNameSpaceParent(  
   IUnknown **ppunk  
);  
```  
  
#### Parametri  
 `ppunk`  
 Indirizzo di un puntatore a interfaccia `IUnknown` che riceve l'interfaccia del padre dello spazio dei nomi.  
  
## Valore restituito  
 Restituisce `S_OK` caso di esito positivo oppure un codice di errore definito da OLE in caso contrario.  
  
## Vedere anche  
 [Interfaccia IDispatchEx](../../winscript/reference/idispatchex-interface.md)