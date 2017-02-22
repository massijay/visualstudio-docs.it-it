---
title: "Procedura: Personalizzare la pagina Web predefinita per un&#39;applicazione ClickOnce | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
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
  - "Publish.htm (pagina Web)"
  - "pagina Web predefinita della distribuzione ClickOnce"
  - "distribuzione di applicazioni [ClickOnce], pubblicazione"
  - "pubblicazione, ClickOnce"
ms.assetid: 418de18c-bee9-4f24-9cd9-0252d175070d
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Procedura: Personalizzare la pagina Web predefinita per un&#39;applicazione ClickOnce
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Quando si pubblica un'applicazione ClickOnce sul Web, insieme all'applicazione viene generata e pubblicata automaticamente una pagina Web.  La pagina predefinita contiene il nome dell'applicazione e i collegamenti per installare l'applicazione e i componenti prerequisiti o per accedere alla Guida in MSDN.  
  
> [!NOTE]
>  I collegamenti effettivamente presenti nella pagina dipendono dal computer in cui la pagina viene visualizzata e dai prerequisiti inclusi.  
  
 Il nome predefinito della pagina Web è Publish.htm. Se necessario, il nome può essere modificato in **Progettazione progetti**.  Per ulteriori informazioni, vedere [How to: Specify a Publish Page for a ClickOnce Application](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md).  
  
 La pagina Web Publish.htm viene pubblicata solo se viene rilevata una versione più recente.  
  
> [!NOTE]
>  Le modifiche apportate alle impostazioni di pubblicazione non avranno effetto sulla pagina Publish.htm. Tuttavia, se si aggiungono o si rimuovono componenti prerequisiti dopo la pubblicazione iniziale, l'elenco dei prerequisiti non sarà più preciso.  Sarà quindi necessario modificare il testo relativo al collegamento dei prerequisiti in base alle modifiche apportate.  
  
### Per personalizzare la pagina Web di pubblicazione  
  
1.  Pubblicare l'applicazione ClickOnce in un percorso Web.  Per ulteriori informazioni, vedere [How to: Publish a ClickOnce Application using the Publish Wizard](../Topic/How%20to:%20Publish%20a%20ClickOnce%20Application%20using%20the%20Publish%20Wizard.md).  
  
2.  Sul server Web aprire il file Publish.htm nella finestra di progettazione Web di Visual Studio o in un altro editor HTML.  
  
3.  Personalizzare la pagina nel modo desiderato e salvarla.  
  
4.  Opzionale.  Per evitare che Visual Studio sovrascriva la pagina Web di pubblicazione personalizzata, deselezionare **Genera automaticamente pagina Web di distribuzione dopo ogni pubblicazione** nella finestra di dialogo Opzioni di pubblicazione.  
  
## Vedere anche  
 [ClickOnce Security and Deployment](../deployment/clickonce-security-and-deployment.md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [How to: Install Prerequisites with a ClickOnce Application](../Topic/How%20to:%20Install%20Prerequisites%20with%20a%20ClickOnce%20Application.md)   
 [How to: Specify a Publish Page for a ClickOnce Application](../deployment/how-to-specify-a-publish-page-for-a-clickonce-application.md)