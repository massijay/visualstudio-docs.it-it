---
title: "IPerPropertyBrowsing2::GetDisplayString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.GetDisplayString
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::GetDisplayString"
ms.assetid: 8f75c6a9-86a9-4e2d-8cb4-74e7b1c0a524
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::GetDisplayString
Ottiene una stringa a visualizzare tipi che non sono implicitamente visualizzabili il testo viene restituito un nome che descrive la proprietà e possono essere visualizzati nell'interfaccia utente del chiamante.  
  
## Sintassi  
  
```  
HRESULT GetDisplayString(  
   DISPID  dispid,  
   BSTR*  pBstr  
);  
```  
  
#### Parametri  
 `dispid`  
 \[in\] inviare l'identificatore della proprietà il cui nome visualizzato è obbligatorio.  
  
 `pBstr`  
 \[out\] puntatore a `BSTR` che contiene il nome visualizzato per la proprietà identificata da `dispID`.  
  
## Valore restituito  
 Restituisce `HRESULT`valido, in genere `S_OK`.  
  
## Note  
 La stringa restituita non è un valore valido della proprietà.  Corrisponde a una visualizzazione della stringa della proprietà.  
  
## Vedere anche  
 [Interfaccia IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)