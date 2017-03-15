---
title: "Percentuale di riduzione del rumore | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.cv.threads.filter"
helpviewer_keywords: 
  - "Visualizzatore di concorrenze, Percentuale di riduzione del rumore"
ms.assetid: 1c10cd4c-2fdd-48c9-b562-a334b3b2df6c
caps.latest.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 6
---
# Percentuale di riduzione del rumore
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per impostazione predefinita, il valore dell'impostazione relativa alla percentuale di riduzione del rumore è pari a 2.  Solo le voci con una percentuale di tempo inclusivo maggiore o uguale a quella indicata in questa impostazione vengono visualizzate nella struttura ad albero delle chiamate.  Modificando l'impostazione, è possibile controllare il numero di voci visualizzate nella struttura ad albero delle chiamate.  Se ad esempio si imposta il valore su 10, verranno visualizzate solo le voci della struttura ad albero delle chiamate con un tempo inclusivo maggiore o uguale al 10%.  Aumentando il valore dell'impostazione, è possibile concentrarsi sulle voci con maggiore impatto sulle prestazioni del processo.