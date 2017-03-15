---
title: "AddMessage | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 102a0404-a00c-4566-93f3-01bc8df63280
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# AddMessage
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Aggiunge un messaggio personalizzato alla diagnostica grafica *HUD* \(Head\-Up Display\).  
  
## Sintassi  
  
```cpp  
void AddMessage(  
  wchar_t const * szMessage  
);  
```  
  
#### Parametri  
 `szMessage`  
 Il messaggio da aggiungere a HUD.  
  
## Note  
 La diagnostica grafica HUD viene visualizzata nell'angolo superiore sinistro dell'applicazione in esecuzione sotto diagnostica di grafica.  Vengono visualizzate informazioni di runtime dell'applicazione, sull'acquisizione di informazioni grafiche e i messaggi aggiunti chiamando questa funzione.  
  
 Per aggiungere un messaggio a HUD, non è necessario acquisire attivamente informazioni grafiche, infatti un messaggio può essere aggiunto tramite un'istanza della classe `VsgDbg`, tuttavia la funzione membro [Init](../debugger/init.md) non deve essere chiamata per prima.  I messaggi vengono visualizzati solo in HUD, non vengono registrati nei file di log.