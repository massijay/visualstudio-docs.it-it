---
title: "How to: Specify the Location Where End Users Will Install From | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
  - "deploying applications [ClickOnce], specifying an installation URL"
  - "URLs, specifying an installation URL"
  - "installation, specifying installation an URL"
  - "Installation URL property"
ms.assetid: 04a804bf-ed55-4a7a-a1e6-f63ed99c0276
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Specify the Location Where End Users Will Install From
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando viene pubblicata un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], è possibile che il percorso a cui gli utenti devono accedere per eseguire il download e l'installazione dell'applicazione non corrisponda a quello iniziale di pubblicazione.  In alcune organizzazioni, ad esempio, è possibile che uno sviluppatore pubblichi un'applicazione su un server di gestione temporanea e che successivamente un amministratore sposti tale applicazione su un server Web.  
  
 In questo caso, è possibile utilizzare la proprietà `Installation URL` per specificare il server Web che dovrà essere utilizzato dagli utenti per il download dell'applicazione.  Questa informazione è necessaria per rendere noto al manifesto dell'applicazione il percorso in cui cercare gli eventuali aggiornamenti.  
  
 La proprietà `Installation URL` può essere impostata nella pagina **Pubblica** di **Progettazione progetti**.  
  
 **Nota** Per impostare la proprietà `Installation URL` è anche possibile utilizzare la **Pubblicazione guidata**.  Per ulteriori informazioni, vedere [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md).  
  
### Per specificare un URL di installazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Pubblica**.  
  
3.  Nel campo relativo all'URL di installazione immettere il percorso di installazione utilizzando un URL completo in formato http:\/\/www.microsoft.com\/NomeApplicazione oppure un percorso UNC in formato \\\\Server\\NomeApplicazione.  
  
## Vedere anche  
 [How to: Specify Where Visual Studio Copies the Files](../deployment/how-to-specify-where-visual-studio-copies-the-files.md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)