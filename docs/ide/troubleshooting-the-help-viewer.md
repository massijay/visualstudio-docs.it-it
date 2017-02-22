---
title: "Risoluzione dei problemi relativi al visualizzatore della Guida | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visualizzatore della Guida 2.0, risoluzione dei problemi"
  - "risoluzione dei problemi [Visualizzatore della Guida 2.0]"
ms.assetid: 461a4553-064a-4142-a2d2-058658b9ba12
caps.latest.revision: 13
caps.handback.revision: 13
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Risoluzione dei problemi relativi al visualizzatore della Guida
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento vengono illustrati i problemi che possono verificarsi con il Visualizzatore della Guida.  
  
## L'audio non funziona.  
 Il Visualizzatore della Guida non include un lettore audio.  Se si scarica il contenuto audio e quando si sceglie **Riproduci** non viene riprodotto niente, installare un lettore audio.  
  
## La ricerca non funziona in Windows Server 2008, Windows Server 2008 con SP1 o Windows Server 2008 R2.  
 Le funzionalità di filtro e di ricerca nel Visualizzatore della Guida richiedono che il servizio Windows Search sia installato e in esecuzione.  Per impostazione predefinita, questo servizio è disattivato in Windows Server 2008, Windows Server 2008 con Service Pack 1 \(SP1\) e Windows Server 2008 R2.  
  
#### Per attivare il servizio Windows Search  
  
1.  Avviare Server Manager.  
  
2.  Nel riquadro di navigazione a sinistra, scegliere **Ruoli**.  
  
3.  Nel riquadro Riepilogo ruoli, selezionare **Aggiungi ruolo**.  
  
4.  Selezionare il ruolo di Servizi file, quindi fare clic su **Avanti**.  
  
5.  Scegliere il servizio ruoli di Windows Search.  
  
## Risorse supplementari  
 È possibile ottenere ulteriori informazioni e fornire un feedback sul visualizzatore della Guida utilizzando le seguenti risorse:  
  
-   Per fornire feedback, vedere [Microsoft Connect](http://go.microsoft.com/fwlink/?linkid=243983) sul sito Web Microsoft o inviare un messaggio di posta elettronica a [hlpfdbk@microsoft.com](mailto:hlpfdbk@microsoft.com).  
  
-   Per ulteriori informazioni, vedere il forum sulla [Guida e documentazione per sviluppatori](http://go.microsoft.com/fwlink/?LinkId=232741) e il blog [The Help Guy](http://go.microsoft.com/fwlink/?LinkId=232743).  
  
## Vedere anche  
 [Guida dell'amministratore di Help Viewer 2.1](http://go.microsoft.com/fwlink/?LinkId=243985)