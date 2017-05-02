---
title: "Interfaccia IPerPropertyBrowsing2 | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Interfaccia IPerPropertyBrowsing2"
ms.assetid: 1e50b3f7-cc1c-495a-93c7-3ee03aea0b8a
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Interfaccia IPerPropertyBrowsing2
Accede alle informazioni nelle pagine delle proprietà offerte da un oggetto.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|`GetDisplayString`|Restituisce una stringa di testo che descrive la proprietà specificata.|  
|`MapPropertyToPage`|Restituisce il CLSID della pagina delle proprietà che consente la modifica della proprietà specificata.|  
|`GetPredefinedStrings`|Restituisce una matrice di stringhe calcolata \(di puntatori\)`LPOLESTR` relative descrizioni dei valori consentiti che la proprietà specificata può accettare.|  
|`SetPredefinedValue`|Imposta il valore della proprietà sul valore predefinito identificato da `dwCookie.`token|  
  
## Requisiti  
 Intestazione: dbgprop.h