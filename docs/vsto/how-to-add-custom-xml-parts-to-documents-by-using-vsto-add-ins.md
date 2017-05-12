---
title: "Procedura: Aggiungere parti XML personalizzate a documenti usando componenti aggiuntivi VSTO"
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
  - "componenti aggiuntivi [sviluppo per Office in Visual Studio], parti XML personalizzate"
  - "documenti di Office [sviluppo per Office in Visual Studio], parti XML personalizzate"
  - "Word [sviluppo per Office in Visual Studio], parti XML personalizzate"
  - "PowerPoint [sviluppo per Office in Visual Studio], parti XML personalizzate"
  - "Excel [sviluppo per Office in Visual Studio], parti XML personalizzate"
  - "parti XML personalizzate [sviluppo per Office in Visual Studio], aggiunta"
  - "documenti [sviluppo per Office in Visual Studio], parti XML personalizzate"
  - "componenti aggiuntivi a livello di applicazione [sviluppo per Office in Visual Studio], parti XML personalizzate"
ms.assetid: 872d2beb-193b-49f9-9a7b-dcebab91a73b
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Procedura: Aggiungere parti XML personalizzate a documenti usando componenti aggiuntivi VSTO
  È possibile archiviare dati XML nei tipi seguenti di documenti creando una parte XML personalizzata in un componente aggiuntivo VSTO:  
  
-   Cartella di lavoro di Microsoft Office Excel.  
  
-   Documento di Microsoft Office Word.  
  
-   Presentazione di Microsoft Office PowerPoint.  
  
 Per altre informazioni, vedere [Cenni preliminari sulle web part XML personalizzate](../vsto/custom-xml-parts-overview.md).  
  
 **Si applica a:** le informazioni contenute in questo argomento si applicano ai progetti a livello di applicazione per Excel, PowerPoint e Word. Per altre informazioni, vedere [Funzionalità disponibili in base ai tipi di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
### Per aggiungere una parte XML personalizzata a una cartella di lavoro di Excel  
  
1.  Aggiungere un nuovo oggetto <xref:Microsoft.Office.Core.CustomXMLPart> alla raccolta <xref:Microsoft.Office.Interop.Excel._Workbook.CustomXMLParts%2A> della cartella di lavoro. <xref:Microsoft.Office.Core.CustomXMLPart> contiene la stringa XML che si vuole memorizzare nella cartella di lavoro.  
  
     Nell'esempio di codice seguente una parte XML personalizzata viene aggiunta a una cartella di lavoro specificata.  
  
     [!code-csharp[Trin_AddCustomXmlPartExcelAppLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelAppLevel/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartExcelAppLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartExcelAppLevel/VB/ThisAddIn.vb#1)]  
  
2.  Aggiungere il metodo `AddCustomXmlPartToWorkbook` alla classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per Excel.  
  
3.  Chiamare il metodo da altro codice nel progetto. Ad esempio, per creare la parte XML personalizzata quando l'utente apre una cartella di lavoro, chiamare il metodo da un gestore eventi per l'evento <xref:Microsoft.Office.Interop.Excel.AppEvents_Event.WorkbookOpen>.  
  
### Per aggiungere una parte XML personalizzata a un documento di Word  
  
1.  Aggiungere un nuovo oggetto <xref:Microsoft.Office.Core.CustomXMLPart> alla raccolta <xref:Microsoft.Office.Interop.Word._Document.CustomXMLParts%2A> del documento.<xref:Microsoft.Office.Core.CustomXMLPart> contiene la stringa XML che si vuole memorizzare nel documento.  
  
     Nell'esempio di codice seguente una parte XML personalizzata viene aggiunta a un documento specificato.  
  
     [!code-csharp[Trin_AddCustomXmlPartWordAppLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordAppLevel/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartWordAppLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartWordAppLevel/VB/ThisAddIn.vb#1)]  
  
2.  Aggiungere il metodo `AddCustomXmlPartToDocument` alla classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per Word.  
  
3.  Chiamare il metodo da altro codice nel progetto. Ad esempio, per creare la parte XML personalizzata quando l'utente apre un documento, chiamare il metodo da un gestore eventi per l'evento <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentOpen>.  
  
### Per aggiungere una parte XML personalizzata a una presentazione di PowerPoint  
  
1.  Aggiungere un nuovo oggetto <xref:Microsoft.Office.Core.CustomXMLPart> alla raccolta <xref:Microsoft.Office.Interop.PowerPoint._Presentation.CustomXMLParts%2A> della presentazione. L'oggetto <xref:Microsoft.Office.Core.CustomXMLPart> contiene la stringa XML che si vuole memorizzare nella presentazione.  
  
     Nell'esempio di codice seguente una parte XML personalizzata viene aggiunta a una presentazione specificata.  
  
     [!code-csharp[Trin_AddCustomXmlPartPowerPointAppLevel#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartPowerPointAppLevel/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_AddCustomXmlPartPowerPointAppLevel#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_AddCustomXmlPartPowerPointAppLevel/VB/ThisAddIn.vb#1)]  
  
2.  Aggiungere il metodo `AddCustomXmlPartToPresentation` alla classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO per PowerPoint.  
  
3.  Chiamare il metodo da altro codice nel progetto. Ad esempio, per creare la parte XML personalizzata quando l'utente apre una presentazione, chiamare il metodo da un gestore eventi per l'evento <xref:Microsoft.Office.Interop.PowerPoint.EApplication_Event.AfterPresentationOpen>.  
  
## Programmazione efficiente  
 Per semplicità, in questo esempio viene usata una stringa XML definita come variabile locale nel metodo. In genere, è necessario ottenere l'XML da un'origine esterna, ad esempio un file o un database.  
  
## Vedere anche  
 [Cenni preliminari sulle web part XML personalizzate](../vsto/custom-xml-parts-overview.md)   
 [Procedura: Aggiungere parti XML personalizzate a personalizzazioni a livello di documento](../vsto/how-to-add-custom-xml-parts-to-document-level-customizations.md)  
  
  