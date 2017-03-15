---
title: "How to: Automatically Increment the ClickOnce Publish Version | Microsoft Docs"
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
  - "deploying applications [ClickOnce], incrementing publish version automatically"
  - "Publish Version property, incrementing"
  - "ClickOnce deployment, incrementing publish version automatically"
  - "publishing, ClickOnce"
ms.assetid: 686ab88a-6305-4914-a05b-fe269cc0ae1e
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 9
---
# How to: Automatically Increment the ClickOnce Publish Version
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando viene pubblicata un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], se si modifica la proprietà `Publish Version`, l'applicazione verrà pubblicata come aggiornamento.  Per impostazione predefinita, ogni volta che si pubblica l'applicazione viene incrementato automaticamente il numero `Revision` della proprietà `Publish Version`.  
  
 È possibile disabilitare questo comportamento nella scheda **Pubblica** di **Progettazione progetti**.  
  
> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere **Importa\/esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Per disabilitare l'incremento automatico del numero di versione pubblicazione dell'applicazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Pubblica**.  
  
3.  Nella sezione **Versione pubblicazione** deselezionare la casella di controllo **Incrementa automaticamente revisione a ogni rilascio**.  
  
## Vedere anche  
 [How to: Set the ClickOnce Publish Version](../Topic/How%20to:%20Set%20the%20ClickOnce%20Publish%20Version.md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)