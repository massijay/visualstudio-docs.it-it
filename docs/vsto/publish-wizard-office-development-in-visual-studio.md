---
title: "Pubblicazione guidata (sviluppo per Office in Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VST.ProjectProperties.PublishWizard"
  - "VST.PublishWizard.Publish.2007System"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "distribuzione ClickOnce [sviluppo per Office in Visual Studio], Pubblicazione guidata"
  - "distribuzione di applicazioni [sviluppo per Office in Visual Studio], Pubblicazione guidata"
  - "applicazioni di Office [sviluppo per Office in Visual Studio], Pubblicazione guidata"
  - "Pubblicazione guidata, soluzioni Office"
ms.assetid: 793314b6-b6a6-4509-8f1c-dd9466cf5190
caps.latest.revision: 17
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 13
---
# Pubblicazione guidata (sviluppo per Office in Visual Studio)
  Utilizzare **Pubblicazione guidata** per copiare i file della soluzione in una posizione specificata, creare file manifesto e creare un programma di installazione.  
  
 Per accedere a questa procedura guidata, scegliere dal menu di **Compila** , scegliere **Pubblica** *Nomesoluzione*.  In alternativa è possibile accedere alla **Pubblicazione guidata** da **Esplora soluzioni**.  Aprire il menu di scelta rapida del nodo di progetto e quindi scegliere **Pubblica**.  
  
 In ciascuna delle sezioni seguenti viene descritta una pagina della procedura guidata.  
  
## Specificare dove pubblicare l'applicazione  
 **Specificare il percorso in cui pubblicare l'applicazione**  
 Obbligatorio.  Il percorso di pubblicazione è la directory in cui la **Pubblicazione guidata** copierà i file della soluzione, ad esempio i manifesti, gli assembly, il certificato temporaneo e altri file della compilazione.  È necessario disporre di accesso in scrittura a tale directory.  
  
 Digitare il percorso come un percorso su disco, una condivisione file, un sito FTP, o sito Web URL, oppure fare clic sul pulsante di **Sfoglia** per individuare il percorso.  Il percorso può essere espresso nei formati seguenti:  
  
-   Percorso relativo o assoluto nel formato standard di Windows, ad esempio C:\\Deploy\\MyApplication o \\MyApplication.  
  
-   Percorso UNC \(Universal Naming Convention\), ad esempio \\\\ServerName\\MyApplication\\.  
  
-   Un URL di un sito Web, ad esempio http:\/\/www.microsoft.com\/MyApplication.  
  
 Per impostazione predefinita, il percorso di pubblicazione è *http:\/\/localhost\/nomeprogetto\/* se è installato IIS; in caso contrario, la directory publish\\.  
  
> [!NOTE]  
>  È opportuno considerare altri aspetti se sul computer di destinazione è in esecuzione Windows Vista.  Per utilizzare l'opzione di pubblicazione locale, è necessario disporre di diritti amministrativi sul computer su cui è in esecuzione Windows Vista.  Inoltre, il percorso predefinito è costituito sempre dalla directory *publish\\*, indipendentemente dal fatto che IIS sia installato o meno.  
  
## Qual è il percorso di installazione predefinito nel computer degli utenti finali?  
 Il percorso di installazione è facoltativo.  È possibile impostare il percorso di installazione in un secondo momento.  Per informazioni dettagliate, vedere [Procedura: modificare il percorso di installazione di una soluzione Office](http://msdn.microsoft.com/it-it/d0eaa07b-2d72-4902-899f-2f9fb165b8fd).  
  
 Il percorso di installazione rappresenta la directory da cui l'utente finale installerà la personalizzazione  e anche il percorso che verrà utilizzato dalla soluzione per controllare la disponibilità di aggiornamenti.  La **Pubblicazione guidata** non distribuisce la soluzione in questo percorso, a meno che il percorso non corrisponda a quello inserito nella casella **Specificare il percorso in cui pubblicare l'applicazione**, nella pagina precedente.  
  
 **Da un sito Web**  
 Specificare l'URL che gli utenti finali utilizzeranno per installare la soluzione.  
  
 **Da un percorso UNC o condivisione file**  
 Specificare il percorso UNC che gli utenti finali utilizzeranno per installare la soluzione.  
  
 **Da CD\-ROM o DVD\-ROM**  
 Tale opzione non richiede un percorso di installazione.  
  
 In Visual Studio non vengono masterizzati CD o DVD.  È necessario copiare l'output in un CD o DVD manualmente.  
  
## Vedere anche  
 [Distribuzione di una soluzione Office utilizzando ClickOnce](../vsto/deploying-an-office-solution-by-using-clickonce.md)   
 [Pagina Pubblicazione, Progettazione progetti &#40;sviluppo per Office in Visual Studio&#41;](../vsto/publish-page-project-designer-office-development-in-visual-studio.md)   
 [Distribuzione di una soluzione Office](../vsto/deploying-an-office-solution.md)  
  
  