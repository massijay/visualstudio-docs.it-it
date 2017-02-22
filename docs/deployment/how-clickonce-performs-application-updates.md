---
title: "How ClickOnce Performs Application Updates | Microsoft Docs"
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
  - "updates, ClickOnce"
  - "ClickOnce deployment, updates"
  - "deploying applications [ClickOnce], application updates"
ms.assetid: d54313c2-cf0c-420d-b151-99953a95f0bb
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How ClickOnce Performs Application Updates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In ClickOnce vengono utilizzate le informazioni sulla versione dei file specificate nel manifesto di distribuzione di un'applicazione per decidere se aggiornare i file dell'applicazione.  Dopo l'avvio di un aggiornamento, in ClickOnce viene utilizzata una tecnica denominata *applicazione di patch ai file* per evitare il download ridondante di file dell'applicazione.  
  
## Applicazione di patch ai file  
 Durante l'aggiornamento di un'applicazione, ClickOnce non scarica tutti i file della nuova versione dell'applicazione a meno che i file non siano cambiati.  Vengono confrontate invece le firme di hash dei file specificati nel manifesto dell'applicazione corrente rispetto alle firme contenute nel manifesto della nuova versione.  Se le firme di un file sono diverse, viene scaricata la nuova versione.  Se invece le firme corrispondono, il file non è cambiato da una versione all'altra.  In questo caso nella nuova versione dell'applicazione verrà copiato e utilizzato il file esistente.  Questo approccio consente a ClickOnce di non scaricare nuovamente l'intera applicazione, anche se sono cambiati solo uno o due file.  
  
 L'applicazione di patch ai file funziona anche per gli assembly scaricati su richiesta utilizzando i metodi <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroup%2A> e <xref:System.Deployment.Application.ApplicationDeployment.DownloadFileGroupAsync%2A>.  
  
 Se si utilizza Visual Studio per compilare l'applicazione, verranno generate nuove firme di hash per tutti i file ogni volta che si rigenera l'intero progetto.  In questo caso verranno scaricati nel client tutti gli assembly, anche se ne sono stati modificati solo alcuni.  
  
 L'applicazione di patch ai file non funziona per file contrassegnati come file di dati e archiviati nella directory dati.  Questi file vengono scaricati sempre indipendentemente dalla firma di hash del file.  Per ulteriori informazioni sulla directory dati, vedere [Accesso a dati locali e remoti in applicazioni ClickOnce](../deployment/accessing-local-and-remote-data-in-clickonce-applications.md).  
  
## Vedere anche  
 [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Choosing a ClickOnce Deployment Strategy](../deployment/choosing-a-clickonce-deployment-strategy.md)