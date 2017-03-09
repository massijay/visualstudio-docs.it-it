---
title: "EndCapture | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# EndCapture
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Termina un intervallo di acquisizione che è stato avviato con `BeginCapture`.  
  
## Sintassi  
  
```cpp  
void EndCapture();  
```  
  
## Note  
 Un intervallo di acquisizione in genere estende un sottoinsieme di un singolo frame, come ad esempio quando si desidera acquisire informazioni grafiche solo su un determinato tipo di chiamata di disegno.  Se l'intervallo di acquisizione estende una chiamata da presentare, allora vengono acquisiti due frame di informazioni grafiche.  Il primo fotogramma estende l'intervallo tra la chiamata a `BeginCapture` e la chiamata da presentare; il secondo frame estende l'intervallo tra il primo evento di Direct3d dopo la chiamata da presentare e la chiamata a `EndCapture`.  
  
 Per acquisire un intervallo, è necessario preparare l'applicazione a catturare e registrare le informazioni grafiche, ovvero è necessario chiamare [Init](../debugger/init.md) tramite un'istanza della classe `VsgDbg` prima di chiamare `BeginCapture` o `EndCapture`.  
  
## Vedere anche  
 [BeginCapture](../debugger/begincapture.md)   
 [CaptureCurrentFrame](../debugger/capturecurrentframe.md)