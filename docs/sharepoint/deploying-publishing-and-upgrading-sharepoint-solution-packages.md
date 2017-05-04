---
title: "Distribuzione, pubblicazione e aggiornamento dei pacchetti delle soluzioni SharePoint | Microsoft Docs"
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
  - "VS.SharePointTools.Project.SharePointProjectPropertyTab"
  - "VS.SharePointTools.Project.Publishing"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "distribuzione [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, distribuzione"
ms.assetid: 5efc1d99-2bd2-4f1a-a7b0-86c3b8f533f0
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Distribuzione, pubblicazione e aggiornamento dei pacchetti delle soluzioni SharePoint
  Dopo aver sviluppato una soluzione SharePoint in Visual Studio, è possibile distribuire il relativo file del pacchetto \(.wsp\) in un server SharePoint locale o pubblicarla su un server SharePoint remoto o locale.  Se si distribuisce i file, è possibile personalizzare la modalità con cui vengono distribuiti i file del pacchetto \(.wsp\).  
  
> [!NOTE]  
>  Attualmente, solo le soluzioni create mediante sandbox possono essere pubblicate in server SharePoint remoti.  Per ulteriori informazioni, vedere [Considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
## Distribuzione, pubblicazione e aggiornamento  
 Per *distribuzione* si intende copiare un file di soluzione SharePoint compilato da un progetto SharePoint in Visual Studio in un host locale.  In una soluzione distribuita, è possibile configurare i passaggi di distribuzione, come riciclare il pool di Internet Information Services \(IIS\), attivare la soluzione dopo la distribuzione, e così via.  Per distribuire, utilizzare il comando **Distribuisci** dal menu di **Compilazione**.  Per ulteriori informazioni, vedere [Procedura: modificare una configurazione di distribuzione SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md) e [Procedura: distribuire e pubblicare una soluzione SharePoint in un sito SharePoint locale](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 Per *pubblicazione* si intende caricare un file di soluzione creato mediante sandbox di SharePoint in un sito remoto di SharePoint; ovvero un sito che si trova in un altro sistema.  È inoltre possibile pubblicare un file di soluzione creato mediante sandbox di SharePoint in un sito SharePoint locale, ma indipendentemente dal fatto che il sito sia locale o remoto, non è possibile configurare i passaggi di distribuzione.  
  
 Per *aggiornamento* si intende aggiornare una soluzione SharePoint pubblicata in locale o in remoto.  Dopo aver applicato delle modifiche alla soluzione SharePoint in Visual Studio, modificare il nome del file del pacchetto della soluzione, ripubblicare la soluzione e quindi aggiornarla.  Se si ripubblica una soluzione pubblicata in locale, è possibile sovrascrivere il file di soluzione esistente.  
  
## Distribuzione di pacchetti  
 È possibile distribuire file di pacchetto in un server SharePoint nel proprio computer di sviluppo per sottoporli a test e debug.  È inoltre possibile creare un file di pacchetto che può essere installato in un altro computer scegliendo il pulsante di opzione **Pubblica su file system** nella finestra di dialogo **Pubblica**.  Il pacchetto viene creato e copiato nel percorso di file locale specificato.  Per distribuire una soluzione SharePoint in un server locale, utilizzare il comando **Distribuisci** dal menu **Compilazione**.  Per ulteriori informazioni, vedere [Procedura: distribuire e pubblicare una soluzione SharePoint in un sito SharePoint locale](../sharepoint/how-to-deploy-and-publish-a-sharepoint-solution-to-a-local-sharepoint-site.md).  
  
 Per informazioni su come distribuire una definizione di elenco, aggiungere un ricevitore di eventi e utilizzare le finestre di progettazione della funzionalità e del pacchetto, vedere [Procedura dettagliata: distribuzione di una definizione di elenco attività del progetto](../sharepoint/walkthrough-deploying-a-project-task-list-definition.md).  
  
## Personalizzazione del processo di distribuzione  
 Nella tabella seguente vengono mostrate le due configurazioni di distribuzione che è possibile utilizzare quando si esegue il debug e si distribuisce una soluzione SharePoint.  
  
|Configurazione della distribuzione|Descrizione|  
|----------------------------------------|-----------------|  
|Valore|Configurazione di distribuzione predefinita.  Vengono eseguiti i seguenti passaggi di distribuzione.<br /><br /> 1.  Esecuzione del comando di pre\-distribuzione.<br />2.  Riciclaggio del pool di applicazioni IIS.<br />3.  Ritiro della soluzione.<br />4.  Aggiunta della soluzione.<br />5.  Attivazione delle funzionalità.<br />6.  Esecuzione del comando di post\-distribuzione.<br /><br /> Quando un pacchetto viene disinstallato, vengono eseguiti i seguenti passaggi di ritrazione.<br /><br /> 1.  Riciclaggio del pool di applicazioni IIS.<br />2.  Ritiro della soluzione.|  
|Nessuna attivazione|Questa configurazione di distribuzione consente di eseguire gli stessi passaggi della configurazione predefinita, ma viene ignorato il passaggio di attivazione.|  
  
 È possibile creare configurazioni di distribuzione personalizzate per completare un singolo passaggio o modificare l'ordine dei passaggi nel processo di distribuzione.  Per ulteriori informazioni, vedere [Procedura: modificare una configurazione di distribuzione SharePoint](../sharepoint/how-to-edit-a-sharepoint-deployment-configuration.md).  
  
 È anche possibile aggiungere comandi da eseguire prima e dopo la distribuzione.  Per ulteriori informazioni, vedere [Procedura: impostare i comandi di distribuzione di SharePoint](../sharepoint/how-to-set-sharepoint-deployment-commands.md).  
  
## Pubblicare i pacchetti in un server remoto o locale  
 Per pubblicare una soluzione SharePoint creata mediante sandbox in un server remoto, scegliere **Compilazione**, **Pubblica** dalla barra dei menu, quindi nella finestra di dialogo **Pubblica**, scegliere il pulsante di opzione **Pubblica in sito SharePoint**, fornendo l'URL del server remoto, ad esempio https:\/\/someremoteserver.sharepoint.microsoftonline.com.  
  
 Per pubblicare una soluzione SharePoint in un server locale, dalla finestra di dialogo **Pubblica**, scegliere il pulsante di opzione **Pubblica su file system**, fornendo un percorso di sistema locale.  
  
 Dopo che una soluzione è stata correttamente pubblicata su SharePoint, la soluzione viene visualizzata in **Raccolta soluzioni** dove è possibile attivarla.  Per ulteriori informazioni, vedere [Procedura: distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
### Aggiornare pacchetti pubblicati  
 Se si apportano modifiche ad un progetto SharePoint in Visual Studio dopo la pubblicazione, il pacchetto pubblicato deve essere aggiornato per includere le modifiche.  Per aggiornarlo correttamente, un pacchetto deve avere un nome univoco.  Se viene trovato un package con lo stesso nome sul sito di SharePoint – fatto che può verificarsi quando si aggiorna un'applicazione esistente – un errore avverte della presenza di conflitto di nomi di file e consente di rinominare il pacchetto.  Dopo essere stato ripubblicato, il nuovo pacchetto viene visualizzato sul sito di SharePoint e può essere aggiornato.  Un pacchetto aggiornato aggiorna la soluzione utilizzando i dati del pacchetto precedente, quindi attiva la in SharePoint.  Per ulteriori informazioni, vedere [Procedura: distribuire, pubblicare e aggiornare soluzioni SharePoint in un server remoto](../sharepoint/how-to-deploy-publish-and-upgrade-sharepoint-solutions-on-a-remote-server.md).  
  
## Vedere anche  
 [Creazione del pacchetto e distribuzione delle soluzioni SharePoint](../sharepoint/packaging-and-deploying-sharepoint-solutions.md)  
  
  