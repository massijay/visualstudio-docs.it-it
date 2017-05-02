---
title: "IPerPropertyBrowsing2::GetPredefinedStrings | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IPerPropertyBrowsing2.GetPredefinedStrings
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IPerPropertyBrowsing2::GetPredefinedStrings"
ms.assetid: d2fa30f7-a566-4dbd-8b47-ffdc00419771
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IPerPropertyBrowsing2::GetPredefinedStrings
Consente al chiamante fornisca una casella di riepilogo calcolata matrice di puntatori di stringhe che rappresentano i valori possibili per questa proprietà.  
  
## Sintassi  
  
```  
HRESULT GetPredefinedStrings(  
   DISPID  dispid,  
   CALPOLESTR*  pCaStrings,  
   CADWORD*  pCaCookies  
);  
```  
  
#### Parametri  
 `dispid`  
 \[in\] identificatore di invio di proprietà per il quale il chiamante sta richiedendo l'elenco della stringa.  
  
 `pCaStrings`  
 \[out\] puntatore a una struttura allocato dal chiamante e calcolata di matrice che contiene il conteggio di elementi e l'indirizzo di una matrice metodo allocata i puntatori di stringa.  Se il metodo non riesce, nessuna memoria allocata e il contenuto della struttura è definito.  
  
 `pCaCookies`  
 \[out\] puntatore alla struttura allocato dal chiamante e calcolata di matrice che contiene il conteggio di elementi e l'indirizzo di una matrice metodo allocata di DWORD.  Se il metodo non riesce, nessuna memoria allocata e il contenuto della struttura è definito.  
  
## Valore restituito  
 Restituisce `HRESULT`valido, in genere `S_OK`.  
  
## Vedere anche  
 [Interfaccia IPerPropertyBrowsing2](../../winscript/reference/iperpropertybrowsing2-interface-1.md)