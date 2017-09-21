---
title: "Procedura: salvare un dataset come XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dati [Visual Studio], salvataggio in XML"
  - "dataset [Visual Basic], salvataggio in XML"
  - "salvataggio di dati"
  - "XML [Visual Basic], dataset"
ms.assetid: 68b8327c-ae05-49ff-b9ba-99183e70b52c
caps.latest.revision: 11
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: salvare un dataset come XML
L'accesso ai dati XML è possibile mediante la chiamata ai metodi XML disponibili nel dataset.  Per salvare i dati in formato XML, è possibile chiamare il metodo <xref:System.Data.DataSet.GetXml%2A> oppure il metodo <xref:System.Data.DataSet.WriteXml%2A> di un oggetto <xref:System.Data.DataSet>.  
  
 Nella chiamata al metodo <xref:System.Data.DataSet.GetXml%2A> viene restituita una stringa in cui sono contenuti i dati provenienti da tutte le tabelle dati del dataset in formato XML.  
  
 Nella chiamata al metodo <xref:System.Data.DataSet.WriteXml%2A> i dati in formato XML vengono inviati a un file specificato.  
  
### Per salvare i dati in un dataset come XML in una variabile  
  
-   Il metodo <xref:System.Data.DataSet.GetXml%2A> restituisce un oggetto <xref:System.String>, dichiarando una variabile di tipo <xref:System.String> e assegnandole i risultati del metodo <xref:System.Data.DataSet.GetXml%2A>.  
  
     [!code-vb[VbRaddataSaving#12](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_1.vb)]
     [!code-cs[VbRaddataSaving#12](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_1.cs)]  
  
### Per salvare i dati in un dataset come XML in un file  
  
-   Il metodo <xref:System.Data.DataSet.WriteXml%2A> dispone di diversi overload.  Nel codice riportato di seguito viene illustrato come salvare i dati in un file creando una variabile e assegnando a questa variabile un percorso valido in cui salvare il file.  
  
     [!code-vb[VbRaddataSaving#13](../data-tools/codesnippet/VisualBasic/save-a-dataset-as-xml_2.vb)]
     [!code-cs[VbRaddataSaving#13](../data-tools/codesnippet/CSharp/save-a-dataset-as-xml_2.cs)]  
  
## Vedere anche  
 [DataSet, DataTable e DataView](../Topic/DataSets,%20DataTables,%20and%20DataViews.md)   
 [Strumenti XML in Visual Studio](../xml-tools/xml-tools-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Connessione ai dati in Visual Studio](../data-tools/connecting-to-data-in-visual-studio.md)   
 [Preparazione dell'applicazione al ricevimento di dati](../Topic/Preparing%20Your%20Application%20to%20Receive%20Data.md)   
 [Recupero di dati nell'applicazione](../data-tools/fetching-data-into-your-application.md)   
 [Associazione di controlli ai dati in Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)   
 [Modifica di dati nell'applicazione](../data-tools/editing-data-in-your-application.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)