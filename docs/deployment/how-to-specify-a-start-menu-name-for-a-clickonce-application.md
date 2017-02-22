---
title: "How to: Specify a Start Menu Name for a ClickOnce Application | Microsoft Docs"
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
  - "Start menu resource name"
  - "Start menu name"
  - "ClickOnce deployment, Start menu name"
ms.assetid: 4b5183b2-2fd4-4433-9310-4a73bb12c4e3
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Specify a Start Menu Name for a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] viene installata per essere utilizzata sia online che offline, viene aggiunta una voce appropriata nel menu **Start** e nell'elenco **Installazione applicazioni**.  Per impostazione predefinita, il nome visualizzato corrisponde al nome dell'assembly dell'applicazione, ma è possibile modificarlo impostando **Nome prodotto** nella finestra di dialogo **Opzioni di pubblicazione**.  
  
 Il valore di **Nome prodotto** verrà visualizzato nella pagina publish.htm. Per un'applicazione installata e offline, corrisponderà al nome della voce del menu Starte a quello visualizzato in **Installazione applicazioni**.  
  
 Il valore di **Nome editore** verrà visualizzato nella pagina publish.htm al di sopra di **Nome prodotto**. Per un'applicazione installata e offline, corrisponderà anche al nome della cartella contenente l'icona dell'applicazione nel menu Start.  
  
 È possibile impostare le proprietà **Nome prodotto** e **Nome editore** nella finestra di dialogo **Opzioni di pubblicazione**, accessibile dalla scheda **Pubblica** di **Progettazione progetti**.  
  
### Per specificare un nome per il menu Start  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Pubblica**.  
  
3.  Scegliere il pulsante **Opzioni** per aprire la finestra di dialogo **Opzioni di pubblicazione**.  
  
4.  Fare clic su **Descrizione**.  
  
5.  Nella finestra di dialogo **Opzioni di pubblicazione** immettere il nome da visualizzare in **Nome prodotto**.  
  
6.  Se lo si desidera, è inoltre possibile specificare un nome in **Nome editore**.  
  
## Vedere anche  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)