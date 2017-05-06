---
title: "Procedura: mappare schemi a fogli di lavoro in Visual Studio"
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
  - "Excel [sviluppo per Office in Visual Studio], XML Schema"
  - "mapping [sviluppo per Office in Visual Studio], XML Schema a fogli di lavoro di Excel"
  - "fogli di lavoro [sviluppo per Office in Visual Studio], XML Schema"
  - "XML Schema [sviluppo per Office in Visual Studio], mapping"
ms.assetid: cef3f751-c1cf-46f3-9177-0bacdcee4121
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Procedura: mappare schemi a fogli di lavoro in Visual Studio
  È possibile mappare uno schema XML a un foglio di lavoro mentre quest'ultimo è aperto in Visual Studio.  Vengono utilizzati gli stessi strumenti di Microsoft Office Excel impiegati quando la cartella di lavoro è aperta all'esterno di Visual Studio.  Il progetto di Office crea gli stessi oggetti, indipendentemente dal fatto che lo schema venga mappato al foglio di lavoro prima o dopo aver creato la soluzione Excel.  
  
 [!INCLUDE[appliesto_xlalldoc](../vsto/includes/appliesto-xlalldoc-md.md)]  
  
> [!NOTE]  
>  Nelle soluzioni Excel non è possibile utilizzare schemi XML multipart.  
  
### Per effettuare il mapping di uno schema XML a un foglio di lavoro di Excel in Visual Studio  
  
1.  Aprire il progetto di cartella di lavoro o di modello di Excel in Visual Studio.  
  
2.  Fare clic nel foglio di lavoro per attivare la finestra di progettazione.  
  
3.  Sulla barra multifunzione, fare clic sulla scheda **Sviluppo**.  
  
    > [!NOTE]  
    >  Se la scheda **Sviluppo** non è visibile, è necessario prima visualizzarla.  Per ulteriori informazioni, vedere [Procedura: visualizzare la scheda Sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
4.  Nel gruppo **XML** fare clic su **Origine**.  
  
     Verrà visualizzata la finestra **Origine XML**.  
  
5.  Scegliere **Mapping XML** nella finestra **Origine XML**.  
  
     Verrà visualizzata la finestra di dialogo **XML Maps**.  
  
6.  Fare clic su **Aggiungi** nella finestra di dialogo **XML Maps**.  
  
7.  Individuare il file di schema, selezionarlo e fare clic su **Apri**.  
  
8.  Fare clic su **OK**.  
  
     Lo schema verrà rappresentato nella finestra **Origine XML**.  Nel progetto verrà generato un oggetto <xref:System.Data.DataSet> tipizzato basato sullo schema e verrà creato un oggetto <xref:System.Windows.Forms.BindingSource>.  
  
9. Trascinare gli elementi dalla finestra **Origine XML** sui punti del foglio di lavoro in cui si desidera creare i corrispondenti controlli.  
  
     Se si trascina un elemento di schema non ripetitivo, il progetto di Office genera un controllo <xref:Microsoft.Office.Tools.Excel.XmlMappedRange> che viene associato automaticamente a <xref:System.Windows.Forms.BindingSource>.  
  
     Se si trascina un elemento di schema ripetitivo, il progetto di Office genera un controllo <xref:Microsoft.Office.Tools.Excel.ListObject> che non viene associato automaticamente a un'origine dati.  Per ulteriori informazioni, vedere [XML Schema e dati nelle personalizzazioni a livello di documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md).  
  
## Vedere anche  
 [Procedura: effettuare il mapping degli schemi a documenti di Word in Visual Studio](../vsto/how-to-map-schemas-to-word-documents-inside-visual-studio.md)   
 [XML Schema e dati nelle personalizzazioni a livello di documento](../vsto/xml-schemas-and-data-in-document-level-customizations.md)  
  
  