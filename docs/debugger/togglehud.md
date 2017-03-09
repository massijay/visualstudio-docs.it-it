---
title: "ToggleHUD | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# ToggleHUD
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Alterna tra attivo o spento la sovrapposizione *HUD* della diagnostica grafica.  
  
## Sintassi  
  
```cpp  
void ToggleHUD();  
```  
  
## Note  
 La diagnostica grafica HUD viene visualizzata nell'angolo superiore sinistro dell'applicazione in esecuzione sotto diagnostica di grafica.  Vengono visualizzate informazioni di runtime dell'applicazione, sull'acquisizione di informazioni grafiche e i messaggi aggiunti chiamando la funzione membro [AddMessage](../debugger/addmessage.md).  
  
 Per alternare l'HUD, non è necessario acquisire attivamente gli elementi grafici, infatti lo si può fare tramite un'istanza della classe `VsgDbg`, ma la funzione membro [Init](../debugger/init.md) non deve essere chiamato per prima.