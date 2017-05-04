---
title: "Procedura: aggiungere righe e colonne alle tabelle di Word a livello di codice | Microsoft Docs"
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
  - "colonne [sviluppo per Office in Visual Studio], aggiunta a tabelle di Word"
  - "righe [sviluppo per Office in Visual Studio], aggiunta a tabelle di Word"
  - "tabelle [sviluppo per Office in Visual Studio], aggiunta di righe e colonne"
ms.assetid: 01a9b6ca-1373-4a6e-b9e6-2225a1321daf
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Procedura: aggiungere righe e colonne alle tabelle di Word a livello di codice
  In una tabella di Microsoft Office Word le celle sono organizzate in righe e colonne.  È possibile usare il metodo <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Rows> per aggiungere righe alla tabella e il metodo <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Columns> per aggiungere colonne.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Esempi di personalizzazione a livello di documento  
 Gli esempi di codice seguenti possono essere usati in una personalizzazione a livello di documento.  Per usare questi esempi, eseguirli dalla classe `ThisDocument` nel progetto.  Gli esempi presuppongono che il documento associato alla personalizzazione contenga già almeno una tabella.  
  
> [!IMPORTANT]  
>  Questo codice viene eseguito solo in progetti creati usando uno dei modelli di progetto seguenti:  
>   
>  -   Documento di Word 2013  
> -   Modello di Word 2013  
> -   Documento di Word 2010  
> -   Modello di Word 2010  
>   
>  Se si vuole eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento all'assembly **Microsoft.Office.Interop.Excel** e quindi usare le classi di tale assembly per aggiungere righe e colonne alle tabelle.  Per altre informazioni, vedere [Procedura: sviluppare applicazioni di Office mediante gli assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) e [Informazioni di riferimento sugli assembly di interoperabilità primari di Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### Per aggiungere una riga a una tabella  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> per aggiungere una riga alla tabella.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#95](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#95)]
     [!code-vb[Trin_VstcoreWordAutomation#95](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#95)]  
  
#### Per aggiungere una colonna a una tabella  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> e quindi usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> per applicare la stessa larghezza a tutte le colonne.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#96](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#96)]
     [!code-vb[Trin_VstcoreWordAutomation#96](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#96)]  
  
## Esempi di componente aggiuntivo VSTO  
 Gli esempi di codice seguenti possono essere usati in un componente aggiuntivo VSTO.  Per usare gli esempi, eseguirli dalla classe `ThisAddIn` nel progetto.  Gli esempi presuppongono che il documento attivo contenga già almeno una tabella.  
  
> [!IMPORTANT]  
>  Questo codice viene eseguito solo in progetti creati usando modelli di componente aggiuntivo VSTO per Word.  
>   
>  Se si vuole eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento all'assembly **Microsoft.Office.Interop.Excel** e quindi usare le classi di tale assembly per aggiungere righe e colonne alle tabelle.  Per altre informazioni, vedere [Procedura: sviluppare applicazioni di Office mediante gli assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) e [Informazioni di riferimento sugli assembly di interoperabilità primari di Word 2010](http://go.microsoft.com/fwlink/?LinkId=189588).  
  
#### Per aggiungere una riga a una tabella  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Rows.Add%2A> per aggiungere una riga alla tabella.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#95](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#95)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#95](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#95)]  
  
#### Per aggiungere una colonna a una tabella  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.Add%2A> e quindi usare il metodo <xref:Microsoft.Office.Interop.Word.Columns.DistributeWidth%2A> per applicare la stessa larghezza a tutte le colonne.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#96](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#96)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#96](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#96)]  
  
## Vedere anche  
 [Procedura: creare tabelle di Word a livello di codice](../vsto/how-to-programmatically-create-word-tables.md)   
 [Procedura: aggiungere testo e formattazione alle celle delle tabelle di Word a livello di codice](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Procedura: compilare tabelle di Word con le proprietà documento a livello di codice](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)  
  
  