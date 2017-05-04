---
title: "Funzione GetVstoSolutionMetadata | Microsoft Docs"
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
ms.assetid: e8195838-fb9f-42b2-bb76-7ae3753f7751
caps.latest.revision: 6
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 5
---
# Funzione GetVstoSolutionMetadata
  Questa API supporta l'infrastruttura di Office e non deve essere utilizzato direttamente dal codice.  
  
## Sintassi  
  
```  
HRESULT WINAPI GetVstoSolutionMetadata(  
    LPCWSTR lpwszSolutionMetadataKey,  
    ISolutionMetadata** ppSolutionInfo  
);  
```  
  
#### Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*lpwszSolutionMetadataKey*|Non utilizzare.|  
|*ppSolutionInfo*|Non utilizzare.|  
  
## Valore restituito  
 Se la funzione ha esito positivo, restituisce **S\_OK**.  Se la funzione ha esito negativo, restituisce un codice di errore.  
  
  