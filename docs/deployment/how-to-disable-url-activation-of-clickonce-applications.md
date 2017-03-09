---
title: "How to: Disable URL Activation of ClickOnce Applications | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "disallowUrlActivation"
  - "URL activation, ClickOnce applications"
  - "ClickOnce deployment, URL activation"
ms.assetid: db31a16b-960f-4264-91d7-c7c40f876068
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Disable URL Activation of ClickOnce Applications
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In genere, un’applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] viene avviata automaticamente subito dopo l'installazione da un server Web.  Per motivi legati alla sicurezza, è possibile disabilitare questo comportamento e invece indicare agli utenti di avviare l'applicazione dal menu **Start**.  La procedura seguente descrive come disabilitare l’attivazione dell’URL.  
  
 Questa tecnica può essere usata solo per le applicazioni [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] installate nel computer dell'utente da un server Web.  Non può essere usata per le applicazioni solo online, che possono essere avviate solo mediante l'URL.  Per altre informazioni sulla differenza tra le applicazioni solo online e installate, vedere [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md).  
  
 Questa procedura usa lo strumento MageUI.exe di [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)].  Per altre informazioni su questo strumento, vedere [MageUI.exe \(Manifest Generation and Editing Tool, Graphical Client\)](../Topic/MageUI.exe%20\(Manifest%20Generation%20and%20Editing%20Tool,%20Graphical%20Client\).md).  È anche possibile eseguire questa procedura mediante [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Routine  
  
#### Per disabilitare l'attivazione dell'URL per l'applicazione  
  
1.  Aprire il manifesto della distribuzione in MageUI.exe.  Se non ancora non ne è stato creato uno, seguire i passaggi in [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  
  
2.  Selezionare la scheda **Opzioni di distribuzione**.  
  
3.  Deselezionare la casella di controllo **Esegui automaticamente l'applicazione dopo l'installazione**.  
  
4.  Salvare e firmare il manifesto.  
  
## Vedere anche  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)