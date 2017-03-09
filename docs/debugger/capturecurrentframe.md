---
title: "CaptureCurrentFrame | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4509311d-6fe2-4b65-9b4a-ff0522585d6a
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# CaptureCurrentFrame
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Acquisisce il resto del frame corrente nel file di log degli elementi grafici.  
  
## Sintassi  
  
```cpp  
void CaptureCurrentFrame();  
```  
  
## Note  
 Se è attualmente in corso un'altra acquisizione, come ad esempio un'acquisizione avviata tramite la funzione `BeginCapture`, allora questa viene completata e salvata nel file di log degli elementi grafici come frame distinto.  Immediatamente dopo, la diagnostica di grafica inizia ad acquisire la parte rimanente del frame corrente, registrato a sua volta come frame distinto.  La fine del frame corrente viene marcata da una funzione da presentare.  
  
 Per acquisire un frame, è necessario preparare l'applicazione a catturare e registrare le informazioni grafiche, ovvero è necessario chiamare [Init](../debugger/init.md) tramite un'istanza della classe `VsgDbg` prima di chiamare `CaptureCurrentFrame`.  
  
## Vedere anche  
 [Init](../debugger/init.md)   
 [BeginCapture](../debugger/begincapture.md)