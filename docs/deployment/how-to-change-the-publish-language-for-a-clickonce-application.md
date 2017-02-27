---
title: "How to: Change the Publish Language for a ClickOnce Application | Microsoft Docs"
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
  - "Publish language property"
  - "ClickOnce deployment, changing publish language"
  - "publishing, ClickOnce"
ms.assetid: ef5024c4-cda1-4970-bc75-32a2a10c92c3
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 19
---
# How to: Change the Publish Language for a ClickOnce Application
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando viene pubblicata un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], nell'interfaccia utente visualizzata durante l'installazione verranno specificate automaticamente le impostazioni cultura del computer di sviluppo.  Se si sta pubblicando un'applicazione localizzata, la lingua e le impostazioni cultura specificate devono corrispondere a quelle della versione localizzata.  Questa impostazione viene determinata dalla proprietà `Publish language` del progetto.  
  
 È possibile impostare la proprietà `Publish language` nella finestra di dialogo **Opzioni di pubblicazione**, accessibile dalla scheda **Pubblica** di **Progettazione progetti**.  
  
> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere **Importa\/esporta impostazioni** dal menu **Strumenti**.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### Per cambiare la lingua di pubblicazione  
  
1.  Con un progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
2.  Fare clic sulla scheda **Pubblica**.  
  
3.  Scegliere il pulsante **Opzioni** per aprire la finestra di dialogo **Opzioni di pubblicazione**.  
  
4.  Fare clic su **Descrizione**.  
  
5.  Nella finestra di dialogo **Opzioni di pubblicazione** selezionare la lingua e le impostazioni cultura dall'elenco a discesa **Lingua di pubblicazione**, quindi scegliere **OK**.  
  
## Vedere anche  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md)