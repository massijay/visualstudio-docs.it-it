---
title: "DA0029: Versione CLR non supportata | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.29"
  - "vs.performance.rules.DA0029"
helpviewer_keywords: 
  - "vs.performance.29"
  - "vs.performance.DA0029"
  - "vs.performance.rules.DA0029"
ms.assetid: 76247259-c6f3-44c4-b3f9-d8dac16b5e0d
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0029: Versione CLR non supportata
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0029|  
|Category|Utilizzo di strumenti di profilatura|  
|Metodo di profilatura|Profilatura dalla riga di comando|  
|Messaggio|È stata rilevata una versione CLR non supportata durante la raccolta.  È possibile che i simboli gestiti non vengano risolti correttamente.|  
|Tipo regola|Informazioni.|  
  
## Causa  
 Si sta tentando di profilare un'applicazione che utilizza [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)], che non è supportata dagli strumenti di profilatura.  
  
## Descrizione della regola  
 Questo avviso viene generato perché gli strumenti di profilatura non saranno in grado di risolvere simboli per il codice gestito in esecuzione nell'applicazione.  Gli strumenti di profilatura non possono risolvere simboli di codice gestito per applicazioni eseguite in [!INCLUDE[net_v11_long](../profiling/includes/net_v11_long_md.md)].  
  
## Come correggere le violazioni  
 Nessuno.