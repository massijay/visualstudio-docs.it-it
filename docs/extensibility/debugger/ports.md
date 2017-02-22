---
title: "Porte | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "porte"
  - "debug [Debugging SDK], porte"
ms.assetid: 1d7f3aa7-7eff-4cab-bc53-0a566b1a9363
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Porte
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In termini di architettura del debugger, **una porta**:  
  
-   È un contenitore per un set di processi in esecuzione su un server.  Ad esempio, una porta può rappresentare una connessione a un dispositivo basato su windows CE da un responsabile seriale, oppure su un computer di reti non DCOM.  Una porta speciale, chiamare la porta locale, contiene tutti i processi in esecuzione sul computer locale.  
  
-   può identificarsi per nome o l'identificatore.  
  
-   È possibile enumerare tutti i processi in esecuzione sulla porta e all'avvio e terminare questi processi.  
  
-   È [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md) rappresentato da un'interfaccia, a cui viene creato [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md) il passaggio di un argomento [Aggiungi porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md).  
  
 [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce una porta predefinita che gestisce tutti i processi basati su Windows, nativo e gestito.  una porta personalizzata deve essere implementata per le connessioni con i dispositivi esterni che non sono basati su Windows.  Per fornire tali porte personalizzate, esigenze personalizzate di un fornitore di porte anche da implementare.  
  
## Vedere anche  
 [Server](../../extensibility/debugger/servers-visual-studio-sdk.md)   
 [Processi](../../extensibility/debugger/processes.md)   
 [Concetti del debugger](../../extensibility/debugger/debugger-concepts.md)   
 [IDebugPort2](../../extensibility/debugger/reference/idebugport2.md)   
 [IDebugPortRequest2](../../extensibility/debugger/reference/idebugportrequest2.md)   
 [Aggiungi porta](../../extensibility/debugger/reference/idebugportsupplier2-addport.md)