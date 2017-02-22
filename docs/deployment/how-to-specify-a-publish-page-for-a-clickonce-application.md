---
title: "How to: Specify a Publish Page for a ClickOnce Application | Microsoft Docs"
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
  - "deploying applications [ClickOnce], specifying publish page"
  - "Publish Page property"
  - "publishing, ClickOnce"
  - "ClickOnce deployment, specifying publish page"
ms.assetid: 9d70eebb-bdee-4b42-8e7e-7a07e199bdf7
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Specify a Publish Page for a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando viene pubblicata un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], insieme all'applicazione viene generata e pubblicata una pagina Web predefinita \(publish.htm\).  Questa pagina contiene il nome dell'applicazione, un collegamento per installare l'applicazione e\/o eventuali componenti prerequisiti, nonché un collegamento a un argomento della Guida in cui vengono fornite informazioni sull'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  La proprietà **Publish Page** del progetto consente di specificare un nome per la pagina Web relativa all'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  
  
 Una volta specificata la pagina di pubblicazione, alla successiva pubblicazione l'applicazione verrà copiata nel percorso di pubblicazione e, se pubblicata nuovamente, non verrà sovrascritta.  In questo modo, sarà possibile personalizzare l'aspetto della pagina senza preoccuparsi di perdere le modifiche apportate.  Per ulteriori informazioni, vedere [Procedura: Personalizzare la pagina Web predefinita ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md).  
  
 La proprietà **Publish Page** può essere impostata nella finestra di dialogo **Opzioni di pubblicazione**, accessibile dal riquadro **Pubblica** di **Progettazione progetti**.  
  
### Per specificare una pagina Web personalizzata per un'applicazione ClickOnce  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Selezionare il riquadro **Pubblica**.  
  
3.  Scegliere il pulsante **Opzioni** per aprire la finestra di dialogo **Opzioni di pubblicazione**.  
  
4.  Fare clic su **Distribuzione**.  
  
5.  Nella finestra di dialogo **Opzioni di pubblicazione** assicurarsi che la casella di controllo **Apri pagina Web di distribuzione dopo la pubblicazione** sia selezionata \(impostazione predefinita\).  
  
6.  Nella casella **Pagina Web di distribuzione** immettere il nome della pagina Web, quindi scegliere **OK**.  
  
### Per impedire che la pagina di pubblicazione venga avviata a ogni pubblicazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Selezionare il riquadro **Pubblica**.  
  
3.  Scegliere il pulsante **Opzioni** per aprire la finestra di dialogo **Opzioni di pubblicazione**.  
  
4.  Fare clic su **Distribuzione**.  
  
5.  Nella finestra di dialogo **Opzioni di pubblicazione** deselezionare la casella di controllo **Apri pagina Web di distribuzione dopo la pubblicazione**.  
  
## Vedere anche  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)   
 [Procedura: Personalizzare la pagina Web predefinita ClickOnce](../deployment/how-to-customize-the-default-web-page-for-a-clickonce-application.md)