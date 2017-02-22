---
title: "Modifica e continuazione non supportate per F# | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Debug [F#], Modifica e continuazione"
  - "Modifica e continuazione [F#]"
ms.assetid: 40ec77bb-07e3-4b58-9254-ae015009441c
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Modifica e continuazione non supportate per F# #
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La modifica e la continuazione non sono supportate quando si esegue il debug del codice F \#.  Le modifiche al codice F\# durante una sessione di debug sono possibili ma devono essere evitate.  Le modifiche di codice non vengono applicate durante la sessione di debug.  Pertanto, qualsiasi modifica apportata al codice F\# durante il debug comporterà una non corrispondenza del codice sorgente con il codice in fase di debug.