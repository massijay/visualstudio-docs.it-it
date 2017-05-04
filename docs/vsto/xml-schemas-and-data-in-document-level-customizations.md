---
title: "XML Schema e dati nelle personalizzazioni a livello di documento | Microsoft Docs"
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
helpviewer_keywords: 
  - "sviluppo per Office in Visual Studio, XML"
  - "schemi [sviluppo per Office in Visual Studio]"
  - "XML [sviluppo per Office in Visual Studio], XML Schema"
  - "XML Schema [sviluppo per Office in Visual Studio]"
  - "XML Schema [sviluppo per Office in Visual Studio], informazioni su dati e XML Schema"
ms.assetid: 74bd5773-6cb0-44fb-9738-75e2f2c6e48d
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# XML Schema e dati nelle personalizzazioni a livello di documento
  **importante** le informazioni relative in questo argomento relative a Microsoft Word è verificato esclusivamente per il vantaggio e l'utilizzo degli utenti e le organizzazioni che si trovano fuori dagli Stati Uniti e i relativi territori, o sviluppano programmi eseguiti con prodotti, Microsoft Word che sono stati concessi in licenza da Microsoft prima del gennaio 2010, quando È stato rimosso un'implementazione di determinata funzionalità correlata alla classe personalizzata XML da Microsoft Word.  Queste informazioni relative a Microsoft Word non possono essere lette o utilizzate dagli individui o delle organizzazioni che si trovano negli Stati Uniti o nei relativi territori oppure che usano o sviluppano programmi eseguiti con prodotti Microsoft Word concessi in licenza da Microsoft dopo il 10 gennaio 2010. Questi prodotti funzioneranno in modo diverso rispetto a quelli concessi in licenza prima di tale data oppure acquistati e concessi in licenza per l'uso all'esterno degli Stati Uniti.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Microsoft Office Excel e Microsoft Office Word forniscono le funzionalità per mappare gli schemi ai documenti.  Queste funzionalità consentono di semplificare l'importazione e l'esportazione di dati XML da e nel documento.  
  
 In Visual Studio vengono esposti come controlli nel modello di programmazione gli elementi di schema mappati nelle personalizzazioni a livello di documento.  Nel caso di Excel, in Visual Studio viene aggiunto il supporto per l'associazione dei controlli ai dati dei database, dei servizi Web e degli oggetti.  Nel caso di Word ed Excel, in Visual Studio viene aggiunto il supporto per i riquadri delle azioni, che possono essere utilizzati con documenti dotati di mapping a schemi per migliorare le attività degli utenti con le soluzioni.  Per ulteriori informazioni, vedere [Cenni preliminari sul riquadro delle azioni](../vsto/actions-pane-overview.md).  
  
> [!NOTE]  
>  Nelle soluzioni Excel non è possibile utilizzare schemi XML multipart.  
  
## Oggetti creati quando gli schemi sono collegati alle cartelle di lavoro di Excel  
 Quando si allega un schema a una cartella di lavoro, Visual Studio crea automaticamente diversi oggetti e li aggiunge al progetto.  Questi oggetti non devono essere eliminati con gli strumenti di Visual Studio, perché sono gestiti da Excel.  Per eliminarli, rimuovere gli elementi mappati dal foglio di lavoro o scollegare lo schema con gli strumenti di Excel.  
  
 Esistono due oggetti principali:  
  
-   XML Schema \(file XSD\).  Per ogni schema della cartella di lavoro, al progetto viene aggiunto uno schema  che in **Esplora soluzioni** appare come elemento di progetto con estensione XSD.  
  
-   Classe <xref:System.Data.DataSet> tipizzata.  Questa classe viene creata in base allo schema.  Questa classe Dataset è visibile in **Visualizzazione classi**.  
  
## Oggetti creati quando gli elementi dello schema vengono mappati ai fogli di lavoro di Excel  
 Quando si mappa un elemento dello schema dal riquadro attività **Origine XML** a un foglio di lavoro, numerosi oggetti vengono automaticamente creati e aggiunti al progetto da Visual Studio.  
  
-   Controlli.  Per ogni oggetto mappato nella cartella di lavoro, viene creato nel modello di programmazione un controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> \(per gli elementi dello schema non ripetuti\) o un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> \(per gli elementi dello schema ripetuti\).  Il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> può essere eliminato solo eliminando dalla cartella di lavoro i mapping e gli oggetti mappati.  Per ulteriori informazioni sui controlli, vedere [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md).  
  
-   Classe BindingSource.  Quando si crea un controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> eseguendo il mapping di un elemento di schema non ripetitivo al foglio di lavoro, viene creata una classe <xref:System.Windows.Forms.BindingSource> e il controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> viene associato alla classe <xref:System.Windows.Forms.BindingSource>.  È necessario associare la classe <xref:System.Windows.Forms.BindingSource> a un'istanza dell'origine dati corrispondente allo schema mappato al documento, ad esempio un'istanza della classe <xref:System.Data.DataSet> tipizzata precedentemente creata.  Creare l'associazione impostando le proprietà <xref:System.Windows.Forms.BindingSource.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A>, disponibili nella finestra **Proprietà**.  
  
    > [!NOTE]  
    >  La classe <xref:System.Windows.Forms.BindingSource> non viene creata per i controlli <xref:Microsoft.Office.Tools.Excel.ListObject>.  È necessario associare manualmente all'origine dati il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> mediante l'impostazione delle proprietà <xref:System.Windows.Forms.BindingSource.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> nella finestra **Proprietà**.  
  
### Schemi mappati di Office e finestra Origini dati di Visual Studio  
 Sia la funzionalità degli schemi mappati di Office che la finestra **Origini dati** di Visual Studio possono rivelarsi utili per la presentazione di dati in un foglio di lavoro di Excel allo scopo di eseguirne il report o la modifica.  In entrambi i casi, è possibile trascinare gli elementi di dati sul foglio di lavoro di Excel.  I due metodi consentono di creare controlli che vengono associati a dati mediante una classe <xref:System.Windows.Forms.BindingSource> a un'origine dati, come una classe <xref:System.Data.DataSet> o un servizio Web.  
  
> [!NOTE]  
>  Quando si esegue il mapping di un elemento di schema ripetitivo a un foglio di lavoro, in Visual Studio viene creato un controllo <xref:Microsoft.Office.Tools.Excel.ListObject>.  Tuttavia, tale controllo <xref:Microsoft.Office.Tools.Excel.ListObject> non viene associato automaticamente ai dati attraverso la classe <xref:System.Windows.Forms.BindingSource>.  È necessario associare manualmente all'origine dati il controllo <xref:Microsoft.Office.Tools.Excel.ListObject> mediante l'impostazione delle proprietà <xref:System.Windows.Forms.BindingSource.DataSource%2A> e <xref:System.Windows.Forms.BindingSource.DataMember%2A> nella finestra **Proprietà**.  
  
 Nella tabella riportata di seguito vengono evidenziate alcune delle differenze tra i due metodi.  
  
|XML Schema|Finestra Origini dati|  
|----------------|---------------------------|  
|Utilizza l'interfaccia di Office.|Utilizza la finestra **Origini dati** di Visual Studio.|  
|Consente le funzionalità incorporate di Office per l'importazione e l'esportazione di dati da file XML.|È necessario fornire le funzionalità di importazione ed esportazione a livello di codice.|  
|È necessario creare codice per riempire di dati i controlli generati.|I controlli aggiunti dalla finestra **Origini dati** vengono riempiti da codice generato automaticamente e dispongono delle stringhe di connessione necessarie quando si utilizzano i server database.|  
  
## Comportamento con gli schemi collegati ai documenti di Word  
 Gli oggetti dati non vengono creati quando si associa uno schema a un documento di Word utilizzato in un progetto di Office a livello di documento.  Vengono tuttavia creati dei controlli quando si mappa un elemento di schema al documento.  Il tipo di controllo dipende dal tipo di elemento mappato. Gli elementi ripetitivi generano controlli <xref:Microsoft.Office.Tools.Word.XMLNodes>, mentre gli elementi non ripetitivi generano controlli <xref:Microsoft.Office.Tools.Word.XMLNode>.  Per ulteriori informazioni, vedere [Controllo XMLNodes](../vsto/xmlnodes-control.md) e [Controllo XMLNode](../vsto/xmlnode-control.md).  
  
## Distribuzione di soluzioni che includono schemi XML  
 Per distribuire una soluzione che si avvale di uno schema XML mappato a un documento è necessario creare un programma di installazione.  Il compito del programma di installazione sarà quello di registrare lo schema nella libreria degli schemi del computer dell'utente.  Se non si registra lo schema, la soluzione potrà essere comunque utilizzata perché Word genera uno schema temporaneo basato sugli elementi presenti nel documento al momento dell'apertura.  L'utente tuttavia non sarà in grado di eseguire la convalida o salvare lo schema utilizzato per creare il progetto.  Per ulteriori informazioni sui programmi di installazione, vedere [Distribuzione di applicazioni, servizi e componenti](../deployment/deploying-applications-services-and-components.md).  
  
 È inoltre possibile aggiungere codice al progetto per verificare se lo schema è presente nella libreria ed è stato registrato.  In caso contrario, infatti, è possibile avvisare l'utente.  
  
 [!code-csharp[Trin_VstcoreDataWord#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataWord/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_VstcoreDataWord#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataWord/VB/ThisDocument.vb#1)]  
  
## Vedere anche  
 [Procedura: effettuare il mapping degli schemi a documenti di Word in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [Procedura: mappare schemi a fogli di lavoro in Visual Studio](../vsto/how-to-map-schemas-to-worksheets-inside-visual-studio.md)  
  
  