---
title: "Creazione del pacchetto e distribuzione delle soluzioni SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "distribuzione [sviluppo per SharePoint in Visual Studio]"
  - "creazione di pacchetti [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, creazione di pacchetti e distribuzione"
ms.assetid: 39072fa7-9f94-49c0-9a67-cbcce0147e61
caps.latest.revision: 34
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Creazione del pacchetto e distribuzione delle soluzioni SharePoint
  In genere, una soluzione SharePoint viene distribuita a un server SharePoint tramite un file di pacchetto della soluzione \(con estensione wsp\).  È possibile utilizzare Visual Studio per organizzare gli elementi del progetto SharePoint in funzionalità e creare un pacchetto per distribuire le funzionalità SharePoint.  
  
 In questo argomento vengono fornite le seguenti informazioni:  
  
-   [Creazione di funzionalità e pacchetti](#Creating)  
  
-   [Supporto delle funzionalità e dello strumento di creazione di pacchetti](#Tools)  
  
-   [Distribuzione di soluzioni SharePoint](#Deploying)  
  
-   [Distribuzione di file nelle soluzioni SharePoint](#DeployingFiles)  
  
##  <a name="Creating"></a> Creazione di funzionalità e pacchetti  
 È possibile utilizzare Visual Studio per raggruppare gli elementi di SharePoint correlati in una *funzionalità*.  Ad esempio, una funzionalità per una definizione dell'elenco Contatti può includere l'istanza e la definizione di elenco.  È possibile combinare questi due elementi in un'unica funzionalità per la distribuzione.  Per ulteriori informazioni sulle funzionalità, vedere [Blocco di costruzione: Funzionalità](http://go.microsoft.com/fwlink/?LinkID=169183).  
  
 Successivamente, è possibile creare un pacchetto della soluzione SharePoint \(con estensione wsp\) per aggregare più funzionalità, definizioni di siti, assembly e altri file in un unico pacchetto che archivia i file in un formato richiesto da SharePoint per distribuire i file al server.  Per ulteriori informazioni, vedere [Blocco di costruzione: Soluzioni](http://go.microsoft.com/fwlink/?LinkID=169186).  
  
##  <a name="Tools"></a> Supporto delle funzionalità e dello strumento di creazione di pacchetti  
 In Visual Studio è possibile utilizzare gli strumenti di sviluppo di SharePoint per organizzare rapidamente i file di SharePoint in funzionalità e pacchetti della soluzione per una distribuzione più semplice.  È possibile utilizzare gli strumenti riportati di seguito per configurare le funzionalità e il pacchetto della soluzione.  
  
-   Finestra di progettazione della funzionalità e finestra di progettazione del pacchetto.  
  
-   Esplora pacchetti, una finestra degli strumenti.  
  
-   Esplora soluzioni.  
  
### Finestra di progettazione della funzionalità e finestra di progettazione del pacchetto  
 Tramite la finestra di progettazione della funzionalità è possibile creare funzionalità, impostare gli ambiti e contrassegnare altre funzionalità come dipendenze.  Tale finestra consente inoltre di generare anche il file XML finale che descrive ogni funzionalità.  Per ulteriori informazioni, vedere [Creazione di funzionalità SharePoint](../sharepoint/creating-sharepoint-features.md).  
  
 Applicare la funzionalità a un sito Web specifico o a un gruppo di siti Web impostandone l'*ambito* nella finestra di progettazione della funzionalità.  Una funzionalità attivata per un singolo sito Web funziona solo in quel particolare sito Web.  Se una funzionalità viene attivata per una raccolta siti, gli elementi della funzionalità si applicano a tutta la raccolta.  Per ulteriori informazioni, vedere l'elemento [Ambito di elemento](http://go.microsoft.com/fwlink/?LinkID=169189).  
  
 Se la funzionalità si basa su altre funzionalità, è possibile impostare una *dipendenza di attivazione funzionalità* per contrassegnare le funzionalità dipendenti prima di rendere disponibile la funzionalità.  Una dipendenza di 'attivazione funzionalità verifica se le funzionalità dipendenti sono già attivate in tale ambito.  Per ulteriori informazioni, vedere [Dipendenze di attivazione e ambito](http://go.microsoft.com/fwlink/?LinkID=169190).  
  
 Nella finestra di progettazione del pacchetto è possibile raggruppare gli elementi di SharePoint in un unico pacchetto della soluzione e configurare se reimpostare il server Web durante la distribuzione.  Per impostare il tipo di server di distribuzione, utilizzare la finestra **Proprietà**.  La finestra di progettazione genera anche il file XML che descrive il contenuto del pacchetto.  Per ulteriori informazioni, vedere [Creazione di pacchetti delle soluzioni SharePoint](../sharepoint/creating-sharepoint-solution-packages.md).  
  
 Durante la distribuzione, il servizio Internet Information Services \(IIS\) viene arrestato per copiare i file della soluzione nel server SharePoint.  Mediante Progettazione pacchetti di Visual Studio, è possibile scegliere se il server Web deve essere riavviato.  Per configurare se la soluzione viene distribuita a un server Web front\-end o a un server applicazioni, utilizzare la finestra **Proprietà**.  Per ulteriori informazioni, vedere [Elemento di soluzione \(soluzione\)](http://go.microsoft.com/fwlink/?LinkID=169191).  
  
### Esplora pacchetti  
 A supporto della finestra di progettazione della funzionalità e della finestra di progettazione del pacchetto, è possibile utilizzare Esplora pacchetti per raggruppare i file SharePoint in funzionalità e pacchetti.  Inoltre, è possibile vedere la visualizzazione gerarchica del pacchetto, delle funzionalità, degli elementi del progetto SharePoint e dei file.  Esplora pacchetti è una finestra degli strumenti che è possibile utilizzare per completare le attività seguenti:  
  
-   Aprire gli elementi e i file del progetto SharePoint.  
  
-   Trascinare gli elementi del progetto SharePoint da una funzionalità a un'altra.  
  
-   Trascinare gli elementi e le funzionalità del progetto SharePoint da un pacchetto a un altro.  
  
-   Aggiungere una nuova funzionalità a un pacchetto.  
  
-   Aprire una finestra di progettazione della funzionalità o del pacchetto.  
  
-   Convalidare funzionalità e pacchetti.  
  
 Gli strumenti di sviluppo di SharePoint in Visual Studio dispongono di regole di convalida che garantiscono la creazione corretta del pacchetto della soluzione.  Inoltre, le regole consentono di verificare che il file della soluzione con estensione wsp possa essere distribuito e attivato correttamente in un server SharePoint.  Per ulteriori informazioni sullo Schema XML per le funzionalità, vedere [Schemi di funzionalità](http://go.microsoft.com/fwlink/?LinkID=169192).  
  
 È possibile aggiungere regole di convalida personalizzate per funzionalità e pacchetti al sistema del progetto SharePoint.  Per ulteriori informazioni, vedere [How to: Create Custom Feature and Package Validation Rules for SharePoint Solutions](../sharepoint/how-to-create-custom-feature-and-package-validation-rules-for-sharepoint-solutions.md).  
  
 Per ulteriori informazioni su Esplora pacchetti, vedere [Procedura: aggiungere e rimuovere funzionalità ed elementi in un pacchetto utilizzando Esplora pacchetti](../sharepoint/how-to-add-and-remove-features-and-items-to-a-package-by-using-the-packaging-explorer.md).  
  
### Esplora soluzioni  
 È possibile utilizzare Esplora soluzioni per esplorare e aprire i file del progetto SharePoint.  Utilizzare il menu di scelta rapida di Esplora soluzioni per aggiungere funzionalità, ricevitori di eventi di funzionalità e risorse di funzionalità.  Inoltre, è possibile aprire le finestre di progettazione della funzionalità e del pacchetto per configurare le funzionalità e i pacchetti per la distribuzione.  
  
##  <a name="Deploying"></a> Distribuzione di soluzioni SharePoint  
 Dopo aver personalizzato le funzionalità e il pacchetto in Visual Studio, è possibile creare un file con estensione wsp da distribuire ai server SharePoint.  Visual Studio può essere utilizzato per eseguire il debug e testare solo il file con estensione wsp sul server SharePoint del computer di sviluppo.  Per ulteriori informazioni sulla distribuzione delle soluzioni SharePoint a un server SharePoint remoto, vedere [Distribuzione di una soluzione](http://go.microsoft.com/fwlink/?LinkID=169194).  
  
 Sul computer di sviluppo è anche possibile personalizzare i passaggi di distribuzione.  Per ulteriori informazioni, vedere [Distribuzione, pubblicazione e aggiornamento dei pacchetti delle soluzioni SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md).  
  
##  <a name="DeployingFiles"></a> Distribuzione di file nelle soluzioni SharePoint  
 In genere, quando si aggiunge un elemento di progetto SharePoint alla soluzione SharePoint, sono inclusi tutti i file necessari.  I file compilabili \(file di codice\) sono compilati nell'assembly di output della soluzione.  Tuttavia, è possibile che a un progetto SharePoint si debbano aggiungere anche file non compilabili, ad esempio file con estensione xml, txt o file di risorse.  Questi file non sono inclusi automaticamente nel pacchetto della soluzione.  Per assicurarsi che vengono inclusi, aggiungere i file a una cartella mappata o a un elemento di progetto SharePoint.  
  
 I file aggiunti alle cartelle mappate vengono copiati automaticamente nell'hive SharePoint quando la soluzione viene distribuita.  I file aggiunti a un elemento di progetto SharePoint vengono distribuiti nel percorso specificato nella proprietà **Percorso di distribuzione** per ogni file, che viene impostato parzialmente in base alla proprietà **Tipo distribuzione**.  Per impostazione predefinita, il valore della proprietà **Tipo distribuzione** è **NoDeployment**, pertanto il file non viene distribuito con la soluzione.  È necessario impostare un altro valore affinché tramite la proprietà il file venga incluso nel pacchetto.  
  
 Ad esempio, per aggiungere un file con estensione xml a un progetto SharePoint, eseguire una di queste azioni:  
  
-   Aggiungere una cartella mappata "Layouts" di SharePoint al progetto.  In questo modo in **Esplora soluzioni** viene creata una cartella denominata **Layouts** che dispone di una sottocartella per il progetto.  Aggiungere il file con estensione xml alla nuova sottocartella.  Per impostazione predefinita, il file viene distribuito nel file system di SharePoint sotto ..\\TEMPLATE\\LAYOUTS\\*Folder Name*\\.  Per informazioni su come aggiungere cartelle mappate, vedere [Procedura: aggiungere e rimuovere cartelle mappate](../sharepoint/how-to-add-and-remove-mapped-folders.md).  
  
-   Aggiungere il file con estensione xml alla cartella di un elemento di progetto SharePoint, quindi modificare l'impostazione della proprietà **Tipo distribuzione** del file con estensione xml da **NoDeployment** in un'altra impostazione quale **RootFile** o **ElementFile**.  L'impostazione **Tipo distribuzione** adatta dipende dal file e dal progetto.  Per ulteriori informazioni sulle impostazioni della proprietà **Tipo distribuzione**, vedere [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md).  
  
 Se un file aggiunto non si applica a nessun progetto specifico nella soluzione, è possibile aggiungere un progetto SharePoint vuoto alla soluzione a cui aggiungere successivamente i file aggiuntivi.  Un'altra alternativa alla distribuzione di file in SharePoint, in particolare nel database del contenuto, consiste nell'aggiungere un modulo al progetto e quindi aggiungere i file al modulo.  Per ulteriori informazioni, vedere [Utilizzo di moduli per includere file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md).  
  
## Vedere anche  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Compilazione e debug delle soluzioni SharePoint](../sharepoint/building-and-debugging-sharepoint-solutions.md)  
  
  