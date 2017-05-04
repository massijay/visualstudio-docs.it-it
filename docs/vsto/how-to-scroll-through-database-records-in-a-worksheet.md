---
title: "Procedura: scorrere i record di un database in un foglio di lavoro | Microsoft Docs"
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
  - "dati [sviluppo per Office in Visual Studio], scorrimento di record di database"
  - "database [sviluppo per Office in Visual Studio], scorrimento di record"
  - "record [sviluppo per Office in Visual Studio], scorrimento"
  - "fogli di lavoro [sviluppo per Office in Visual Studio], scorrimento di record"
ms.assetid: aea4c86c-9d6d-47dd-8977-066e21945dab
caps.latest.revision: 33
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 32
---
# Procedura: scorrere i record di un database in un foglio di lavoro
  Nella seguente procedura viene illustrato come utilizzare la finestra di progettazione per visualizzare un singolo campo di una tabella di database in un foglio di lavoro di Microsoft Office Excel, con controlli che consentono all'utente finale di scorrere tutti i record.  
  
 È possibile utilizzare la finestra di progettazione solo in progetti a livello di documento.  Tuttavia, è anche possibile aggiungere controlli e associarli ai dati a livello di codice durante la fase di esecuzione.  Per ulteriori informazioni, vedere [Procedura dettagliata: data binding semplice in un progetto di componente aggiuntivo VSTO](../vsto/walkthrough-simple-data-binding-in-vsto-add-in-project.md).  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
### Per scorrere i record di database in un foglio di lavoro  
  
1.  Aprire un progetto Applicazione di Excel in Visual Studio.  
  
2.  Aprire la finestra **Origini dati** e creare un'origine dati dal database.  Per ulteriori informazioni, vedere [Procedura: connettersi ai dati di un database](../Topic/How%20to:%20Connect%20to%20Data%20in%20a%20Database.md).  
  
3.  Espandere la tabella contenente i dati che si desidera mostrare e selezionare la colonna specifica.  
  
4.  Aprire l'elenco di controlli e scegliere **NamedRange**.  
  
5.  Trascinare il controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> sulla cella in cui si desidera visualizzare i dati.  
  
6.  Dalla scheda **Windows Form** della **Casella degli strumenti**, aggiungere un controllo <xref:System.Windows.Forms.BindingNavigator> al foglio di lavoro e impostare i controlli che si desidera utilizzare.  Per ulteriori informazioni, vedere [Cenni preliminari sul controllo BindingNavigator &#40;Windows Form&#41;](../Topic/BindingNavigator%20Control%20Overview%20(Windows%20Forms).md).  
  
## Vedere anche  
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  