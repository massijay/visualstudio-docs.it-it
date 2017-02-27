---
title: "Limitazioni sulle lunghezze di stringa | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "origine plug-in del controllo, le restrizioni sulle lunghezze di stringa"
ms.assetid: 877173d2-ca27-43b3-b1f4-8379f7c5e268
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# Limitazioni sulle lunghezze di stringa
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'API di plug\-in controllo origine limita la lunghezza delle stringhe utilizzate in varie funzioni.  
  
## Valori di lunghezza stringa  
  
|Costante|Valore|  
|--------------|------------|  
|`SCC_NAME_LEN`|31|  
|`SCC_AUXLABEL_LEN`|31|  
|`SCC_USER_LEN`|31|  
|`SCC_PRJPATH_LEN`|300|  
  
> [!NOTE]
>  La lunghezza non include l'interruzione del `null`. Altre costanti con un suffisso "\_SIZE" anziché "\_LEN" include uno spazio per l'interruzione del `null`.  
  
|Costante|Valore|  
|--------------|------------|  
|SCC\_NAME\_SIZE|32|  
|SCC\_AUXLABEL\_SIZE|32|  
|SCC\_USER\_SIZE|32|  
|SCC\_PRJPATH\_SIZE|301|  
  
## Vedere anche  
 [Plug\-in del controllo codice sorgente](../extensibility/source-control-plug-ins.md)