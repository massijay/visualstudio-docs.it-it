---
title: "VsgDbg::~VsgDbg (distruttore) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VsgDbg::~VsgDbg (distruttore)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Distrugge un'istanza della classe `VsgDbg`.  Se l'informazione grafica è attivamente in fase di registrazione, il rispettivo file di log viene completato e chiuso, e le risorse che erano in uso durante la fase di cattura delle informazioni grafiche vengono rilasciate.  
  
## Sintassi  
  
```cpp  
~VsgDbg();  
```  
  
## Vedere anche  
 [VsgDbg::VsgDbg \(costruttore\)](../debugger/vsgdbg-vsgdbg-constructor.md)