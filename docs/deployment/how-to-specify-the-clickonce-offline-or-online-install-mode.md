---
title: "How to: Specify the ClickOnce Offline or Online Install Mode | Microsoft Docs"
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
  - "ClickOnce deployment, specifying install mode"
  - "install mode"
  - "online applications"
  - "offline applications"
  - "ClickOnce install mode"
ms.assetid: 0aee5fc1-e966-4bda-9b8f-d9997aeaa779
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Specify the ClickOnce Offline or Online Install Mode
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La proprietà `Install Mode` di un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] determina se l'applicazione sarà disponibile in modalità online o offline.  Se si sceglie **Applicazione disponibile solo online**, per eseguire l'applicazione l'utente dovrà avere accesso al percorso di pubblicazione \(una pagina Web o una condivisione file\) di [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Se invece si sceglie **Applicazione disponibile anche offline dal menu Start**, verranno aggiunte le voci appropriate al menu Start e alla finestra di dialogo **Installazione applicazioni** per consentire l'esecuzione dell'applicazione anche se l'utente non è connesso.  
  
 La proprietà `Install Mode` può essere impostata nella scheda **Pubblica** di **Progettazione progetti**.  
  
 **Nota** Per impostare la proprietà `Install Mode` è anche possibile utilizzare la Pubblicazione guidata.  Per ulteriori informazioni, vedere [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md).  
  
### Per rendere un'applicazione ClickOnce disponibile solo online  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Pubblica**.  
  
3.  Nell'area **Modalità di installazione e impostazioni** selezionare il pulsante di opzione **Applicazione disponibile solo online**.  
  
### Per rendere un'applicazione ClickOnce disponibile sia online che offline  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Pubblica**.  
  
3.  Nell'area **Modalità di installazione e impostazioni** selezionare il pulsante di opzione **Applicazione disponibile anche offline dal menu Start**.  
  
     Durante l'installazione verranno aggiunte le voci appropriate al menu Start e alla finestra di dialogo **Installazione applicazioni** nel Pannello di controllo.  
  
## Vedere anche  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)   
 [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md)