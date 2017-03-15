---
title: "UnInit | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# UnInit
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Finalizza il file di log degli elementi grafici, lo chiude e libera le risorse utilizzate durante la registrazione delle informazioni grafiche dell'applicazione.  
  
## Sintassi  
  
```cpp  
void UnInit();  
```  
  
## Note  
 `UnInit` viene chiamata automaticamente quando un'istanza della classe `VsgDbg` viene eliminata.  Se l'istanza `VsgDbg` non stava attivamente registrando informazioni grafiche, questa non ha effetto.  
  
 Dopo che `UnInit` è stata chiamata su un'istanza della classe `VsgDbg`, è possibile creare un nuovo file di log degli elementi grafici chiamando `Init` e finalizzarlo chiamando `UnInit`.  È possibile ripetere questo procedimento tutte le volte che si desidera utilizzare la stessa istanza di `VsgDbg` per creare diversi file di log degli elementi grafici indipendenti tra loro.  
  
## Vedere anche  
 [Init](../debugger/init.md)