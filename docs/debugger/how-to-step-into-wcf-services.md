---
title: "Procedura: eseguire istruzioni nei servizi WCF | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "debug, WCF"
  - "WCF, debug"
ms.assetid: 9893ad01-54af-499f-85a6-9d1cfe6eb640
caps.latest.revision: 24
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 24
---
# Procedura: eseguire istruzioni nei servizi WCF
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], è possibile eseguire istruzioni in un servizio WCF.  Se il servizio WCF si trova nella stessa soluzione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] del client, è possibile raggiungere punti di interruzione nel servizio WCF.  
  
 Per consentire il funzionamento, è necessario avere attivato il debug nel file app.config o web.config.  Per informazioni sull'attivazione di debug e per le limitazioni sull'esecuzione dei servizi WCF, vedere [Limitazioni del debug di WCF](../debugger/limitations-on-wcf-debugging.md).  
  
### Per eseguire istruzioni in un servizio WCF  
  
1.  Creare una soluzione [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] contenente entrambi i progetti client WCF e servizio WCF.  
  
2.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto Client WCF e scegliere **Imposta come progetto di avvio**.  
  
3.  Attivare il debug nel file app.config o web.config.  Per ulteriori informazioni, vedere [Limitazioni del debug di WCF](../debugger/limitations-on-wcf-debugging.md).  
  
4.  Impostare un punto di interruzione nel percorso all'interno del progetto client in cui si desidera iniziare a eseguire le istruzioni.  In genere, si troverà poco prima della chiamata del servizio WCF.  
  
5.  Eseguire il debug nel punto d'interruzione, quindi iniziare a eseguire le istruzioni.  Il debugger eseguirà automaticamente le istruzioni nel servizio.  
  
## Vedere anche  
 [Debug dei servizi WCF](../debugger/debugging-wcf-services.md)   
 [Limitazioni del debug di WCF](../debugger/limitations-on-wcf-debugging.md)   
 [Procedura: eseguire il debug di un servizio WCF indipendente](../debugger/how-to-debug-a-self-hosted-wcf-service.md)