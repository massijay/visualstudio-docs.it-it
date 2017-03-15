---
title: "How to: Check for Application Updates Programmatically Using the ClickOnce Deployment API | Microsoft Docs"
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
  - "ClickOnce deployment, updates"
  - "application updates"
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Check for Application Updates Programmatically Using the ClickOnce Deployment API
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In ClickOnce è possibile procedere in due modi per aggiornare un'applicazione già distribuita.  Il primo modo consiste nel configurare la distribuzione ClickOnce affinché venga controllata automaticamente la disponibilità degli aggiornamenti a determinati intervalli.  Il secondo modo invece consiste nello scrivere codice in cui viene utilizzata la classe <xref:System.Deployment.Application.ApplicationDeployment> affinché venga controllata la disponibilità degli aggiornamenti in base a un evento, ad esempio una richiesta dell'utente.  
  
 Nelle procedure descritte di seguito viene illustrato il codice per l'esecuzione di un aggiornamento a livello di codice e viene descritto inoltre come configurare la distribuzione ClickOnce in modo da attivare i controlli della disponibilità degli aggiornamenti a livello di codice.  
  
 Per aggiornare un'applicazione ClickOnce a livello di codice, è necessario specificare un percorso per gli aggiornamenti,  denominato talvolta provider di distribuzione.  Per ulteriori informazioni sull'impostazione di questa proprietà, vedere [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md).  
  
> [!NOTE]
>  La tecnica descritta di seguito può essere utilizzata inoltre per distribuire l'applicazione da una posizione e aggiornarla da un'altra.  Per ulteriori informazioni, vedere [How to: Specify an Alternate Location for Deployment Updates](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).  
  
### Per controllare gli aggiornamenti a livello di codice  
  
1.  Creare una nuova applicazione Windows Form utilizzando gli strumenti da riga di comando o visivi preferiti.  
  
2.  Creare pulsanti, voci di menu o altri elementi dell'interfaccia utente che si desidera che vengano utilizzati dagli utenti per controllare la disponibilità degli aggiornamenti.  Dal gestore eventi dell'elemento creato chiamare il metodo seguente per controllare la disponibilità e installare gli aggiornamenti.  
  
     [!CODE [ClickOnceAPI#6](../CodeSnippet/VS_Snippets_Winforms/ClickOnceAPI#6)]  
  
3.  Compilare l'applicazione.  
  
### Utilizzo di Mage.exe per la distribuzione di un'applicazione per il controllo della disponibilità degli aggiornamenti a livello di codice  
  
-   Seguire le istruzioni per la distribuzione dell'applicazione con Mage.exe descritte in [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Quando si chiama Mage.exe per generare il manifesto di distribuzione, utilizzare l'opzione della riga di comando `providerUrl` e specificare l'URL in cui deve essere controllata la disponibilità degli aggiornamenti.  Se ad esempio gli aggiornamenti dell'applicazione sono contenuti in [http:\/\/www.microsoft.com\/it\/it\/default.aspx](http://www.microsoft.com/it/it/default.aspx), la chiamata per generare il manifesto di distribuzione sarà simile alla seguente:  
  
    ```  
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application  
    ```  
  
### Utilizzo di MageUI.exe per la distribuzione di un'applicazione per il controllo della disponibilità degli aggiornamenti a livello di codice  
  
-   Seguire le istruzioni per la distribuzione dell'applicazione con Mage.exe descritte in [Walkthrough: Manually Deploying a ClickOnce Application](../deployment/walkthrough-manually-deploying-a-clickonce-application.md).  Nella scheda **Opzioni di distribuzione** impostare il campo **Posizione di partenza** sul manifesto dell'applicazione che deve essere controllato per ricercare eventuali aggiornamenti.  Nella scheda **Opzioni aggiornamento** deselezionare la casella di controllo **Controlla aggiornamenti dell'applicazione**.  
  
## Sicurezza di .NET Framework  
 L'applicazione deve disporre di autorizzazioni di attendibilità totale per utilizzare l'aggiornamento a livello di codice.  
  
## Vedere anche  
 [How to: Specify an Alternate Location for Deployment Updates](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)   
 [Choosing a ClickOnce Update Strategy](../deployment/choosing-a-clickonce-update-strategy.md)   
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)