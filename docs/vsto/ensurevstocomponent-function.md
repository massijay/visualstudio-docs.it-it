---
title: "Funzione EnsureVSTOComponent"
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
ms.assetid: e101fcd5-37a2-4b8c-b9ac-a84624298736
caps.latest.revision: 9
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 8
---
# Funzione EnsureVSTOComponent
  Questa API supporta l'infrastruttura di Office e non deve essere utilizzato direttamente dal codice.  
  
## Sintassi  
  
```  
HRESULT EnsureVSTOComponent(  
    IVSTProject *pProject  
);  
```  
  
#### Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*pProject*|Non utilizzare.|  
  
## Valore restituito  
 Se la funzione ha esito positivo, restituisce **S\_OK**.  Se la funzione ha esito negativo, restituisce un codice di errore.  
  
  