---
title: "Cenni preliminari sulle web part XML personalizzate | Microsoft Docs"
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
  - "parti XML personalizzate [sviluppo per Office in Visual Studio]"
  - "parti XML personalizzate [sviluppo per Office in Visual Studio], informazioni"
  - "dati [sviluppo per Office in Visual Studio], parti XML personalizzate"
  - "documenti [sviluppo per Office in Visual Studio], parti XML personalizzate"
  - "incorporamento di dati XML in documenti [sviluppo per Office in Visual Studio]"
  - "Excel [sviluppo per Office in Visual Studio], parti XML personalizzate"
  - "documenti Office [sviluppo per Office in Visual Studio], parti XML personalizzate"
  - "Office (formati XML aperti) [sviluppo per Office in Visual Studio]"
  - "Word [sviluppo per Office in Visual Studio], parti XML personalizzate"
  - "XML [sviluppo per Office in Visual Studio], parti XML personalizzate"
  - "formati di file XML [sviluppo per Office in Visual Studio]"
  - "parti XML [sviluppo per Office in Visual Studio]"
ms.assetid: a14119dc-59e8-4614-94f1-08c92bdf7300
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Cenni preliminari sulle web part XML personalizzate
  È possibile incorporare i dati XML nei documenti per alcune applicazioni di Microsoft Office.  Quando si incorporano i dati XML in un documento, i dati vengono denominati *parti XML personalizzate*.  
  
 È possibile creare e modificare le parti XML personalizzate in un documento usando un componente aggiuntivo VSTO o una soluzione a livello di documento in Visual Studio.  Non è necessario avviare l'applicazione di Microsoft Office per creare e modificare le parti XML personalizzate.  
  
 **Si applica a:** le informazioni contenute in questo argomento sono valide per i progetti a livello di documento e per i progetti di componenti aggiuntivi VSTO per Excel, PowerPoint e Word.  Per altre informazioni, vedere [Funzionalità disponibili in base ai tipi di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
> [!NOTE]  
>  Visual Studio consente anche di memorizzare nella cache gli oggetti dati nelle personalizzazioni a livello di documento.  Questa funzionalità è diversa dalle parti XML personalizzate, sebbene siano presenti alcune somiglianze.  Per altre informazioni, vedere [Dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md).  
  
## Informazioni sulle parti XML personalizzate  
 Le parti XML personalizzate sono state introdotte nel sistema Microsoft Office 2007, insieme ai formati Open XML.  I formati includono i nuovi formati di file basati su XML per Excel, PowerPoint e Word \(ad esempio con estensione xlsx, pptx e docx\).  I documenti in questi formati includono file XML \(denominati anche *parti XML*\) organizzati in cartelle in un archivio ZIP.  Per la maggior parte, si tratta di parti XML predefinite che consentono di definire la struttura e lo stato del documento.  Tuttavia, i documenti possono contenere anche parti XML personalizzate, che è possibile usare per archiviare i dati XML arbitrari nei documenti.  
  
 I formati di file XML consentono alle applicazioni di usare nei documenti funzionalità non consentite con i vecchi formati di file binari \(ad esempio, xls, ppt e doc\).  Tutte le applicazioni in grado di leggere gli archivi ZIP possono esaminare e modificare i contenuti dei documenti, anche se Microsoft Office non è installato.  
  
 Per altre informazioni sulla struttura di Open XML e delle parti XML personalizzate, vedere i seguenti articoli:  
  
-   [Introducing the Office \(2007\) Open XML File Formats \(informazioni in lingua inglese\)](http://msdn.microsoft.com/it-it/96018532-f62c-4da7-bbff-16b96a483fbf)  
  
-   [Procedura: Modificare i documenti con formati Open XML](http://msdn.microsoft.com/it-it/c989d4e2-053d-4e1f-83be-257c608b343f)  
  
-   [Procedura dettagliata: Formato XML di Word 2007](http://msdn.microsoft.com/it-it/fc1afcb2-27fb-4608-9f29-11b7bd23ea4a)  
  
-   [Compilazione di documenti di Word 2007 con i formati Open XML](http://msdn.microsoft.com/it-it/59a46f4e-5a5a-4dac-86e5-7dfd43330766)  
  
> [!NOTE]  
>  Excel, Word e PowerPoint consentono anche di usare parti XML personalizzate nei documenti salvati in formati di file binari.  Tuttavia, se un documento viene salvato in un formato binario, non è possibile aggiungere o modificare le parti XML personalizzate senza avviare l'applicazione di Microsoft Office.  
  
## Creazione e modifica delle parti XML personalizzate  
 È possibile creare o modificare le parti XML personalizzate quando il documento è aperto nell'applicazione di Office oppure quando il documento è chiuso, anche se Microsoft Office non è installato.  
  
### Modifica delle parti XML durante l'esecuzione dell'applicazione di Office  
 È possibile usare le parti XML personalizzate usando una personalizzazione a livello di documento o un componente aggiuntivo VSTO.  Se si una personalizzazione a livello di documento, vengono usate in genere le parti XML personalizzate nel documento personalizzato.  Se si usa un componente aggiuntivo VSTO, è possibile creare o modificare le parti XML personalizzate in qualsiasi documento aperto nell'applicazione.  
  
 Per creare una parte XML personalizzata usando Visual Studio, aggiungere un nuovo <xref:Microsoft.Office.Core.CustomXMLPart> alla raccolta <xref:Microsoft.Office.Core.CustomXMLParts> nel documento.  Per altre informazioni, vedere i seguenti argomenti:  
  
-   [Procedura: Aggiungere parti XML personalizzate a personalizzazioni a livello di documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
-   [Procedura: Aggiungere parti XML personalizzate a documenti usando componenti aggiuntivi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)  
  
### Modifica delle parti XML senza avviare l'applicazione di Office  
 È possibile aggiungere o modificare una parte XML personalizzata senza avviare Excel, PowerPoint o Word.  Questa funzione è utile per usare i dati XML di un documento in un computer in cui sono installate le applicazioni di Microsoft Office, ad esempio un server.  
  
 Per aggiungere una parte XML personalizzata senza avviare Microsoft Office, usare le classi in Open XML SDK.  Queste classi sono progettate per fornire l'accesso ai contenuti Open XML specifici dei documenti di Office.  Ad esempio, per aggiungere una parte XML personalizzata a una cartella di lavoro di Excel si usa il metodo [AddNewPart\<T\>](http://msdn.microsoft.com/it-it/47c348c0-77ab-a504-5097-bcd6a213921a) di un oggetto [WorkbookPart](http://msdn.microsoft.com/it-it/d011e6f4-77dd-d02d-66ef-dc4a9e7b26f2).  Per altre informazioni, vedere [Open XML SDK 2.0](http://msdn.microsoft.com/it-it/f6a9ae68-7989-4208-97f5-3c945137a0ab).  
  
## Binding di parti XML personalizzate a controlli contenuto Word  
 È possibile associare i controlli contenuto in una soluzione Word agli elementi in una parte XML personalizzata.  Quando un controllo contenuto è associato a una parte XML personalizzata, i dati nella parte XML personalizzata vengono visualizzati nell'interfaccia utente del controllo contenuto.  Se un utente modifica testo nel controllo, l'elemento XML corrispondente viene automaticamente aggiornato.  Analogamente, se si modificano i valori degli elementi nelle parti XML personalizzate, i controlli contenuto associati agli elementi XML visualizzeranno i nuovi dati.  Per altre informazioni, vedere [Controlli del contenuto](../vsto/content-controls.md).  
  
## Vedere anche  
 [XML Schema e dati nelle personalizzazioni a livello di documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)   
 [Procedura: Aggiungere parti XML personalizzate a personalizzazioni a livello di documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)   
 [Procedura: Aggiungere parti XML personalizzate a documenti usando componenti aggiuntivi VSTO](../vsto/how-to-add-custom-xml-parts-to-documents-by-using-vsto-add-ins.md)   
 [Controlli del contenuto](../vsto/content-controls.md)   
 [Procedura dettagliata: associazione dei controlli del contenuto a parti XML personalizzate](../vsto/walkthrough-binding-content-controls-to-custom-xml-parts.md)  
  
  