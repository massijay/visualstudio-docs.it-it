---
title: "Metodo SetWefProcessId"
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
ms.assetid: 404eec23-a67e-4f5b-b27d-86651f08be03
caps.latest.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 7
---
# Metodo SetWefProcessId
  Fornisce l'identificatore del processo che esegue il contenuto Web di Framework \(WEF\) extensions.  
  
## Sintassi  
  
```  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*dwProcessId*|L'identificatore del processo che verrà utilizzato per eseguire il contenuto di WEF.|  
  
## Valore restituito  
 Valore HRESULT indicante se il metodo è stato eseguito correttamente.  
  
## Note  
 Questo metodo deve essere chiamato dopo che il processo del contenuto di WEF viene creato ma prima di tutto il contenuto di WEF funzioni.  
  
 Se si desidera l'ambiente di sviluppo per connettere un debugger al processo del contenuto di WEF, l'ambiente deve eseguire questa operazione nell'implementazione del metodo.  
  
  