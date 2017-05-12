---
title: "Funzione GetValidCompatibleFramework"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: dfb365c0-5ffc-4290-ab8b-bd347e0f0db9
caps.latest.revision: 7
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 6
---
# Funzione GetValidCompatibleFramework
  Questa API supporta l'infrastruttura di Office e non deve essere utilizzato direttamente dal codice.  
  
## Sintassi  
  
```  
HRESULT WINAPI GetValidCompatibleFramework(  
    LPCWSTR lpwszCompatibleFrameworksXML,  
    BSTR* pbstrValidFrameworkTag  
);  
```  
  
#### Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*lpwszCompatibleFrameworksXML*|Non utilizzare.|  
|*pbstrValidFrameworkTag*|Non utilizzare.|  
  
## Valore restituito  
 Se la funzione ha esito positivo, restituisce **S\_OK**.  Se la funzione ha esito negativo, restituisce un codice di errore.  
  
  