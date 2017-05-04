---
title: "Procedura: creare tabelle di Word a livello di codice | Microsoft Docs"
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
  - "documenti [sviluppo per Office in Visual Studio], aggiunta di tabelle"
  - "tabelle [sviluppo per Office in Visual Studio], aggiunta a documenti"
ms.assetid: fe1f9143-9622-45e8-b0a5-511336d99ad1
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Procedura: creare tabelle di Word a livello di codice
  La raccolta <xref:Microsoft.Office.Interop.Word.Tables> è un membro delle classi <xref:Microsoft.Office.Interop.Word.Document>, <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Interop.Word.Selection> e <xref:Microsoft.Office.Interop.Word.Range>, pertanto è possibile creare una tabella in ognuno di questi contenuti.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> della raccolta <xref:Microsoft.Office.Interop.Word.Tables> per aggiungere una tabella nell'intervallo specificato.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Creazione di tabelle nelle personalizzazioni a livello di documento  
  
#### Per aggiungere una tabella semplice in un documento  
  
-   Usare il metodo <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> per aggiungere una tabella costituita da tre righe e quattro colonne all'inizio del documento.  
  
     Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#86](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#86)]
     [!code-vb[Trin_VstcoreWordAutomation#86](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#86)]  
  
 Quando si crea una tabella, viene aggiunta automaticamente alla raccolta <xref:Microsoft.Office.Interop.Word.Tables> dell'elemento host <xref:Microsoft.Office.Tools.Word.Document>.  È quindi possibile fare riferimento alla tabella in base al numero dell'elemento usando la proprietà <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, come illustrato nel codice seguente.  
  
#### Per fare riferimento a una tabella in base al numero dell'elemento  
  
1.  Usare la proprietà <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> e fornire il numero di elemento a cui si vuole fare riferimento.  
  
     Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#87](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#87)]
     [!code-vb[Trin_VstcoreWordAutomation#87](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#87)]  
  
 Ogni oggetto <xref:Microsoft.Office.Interop.Word.Table> dispone anche di una proprietà <xref:Microsoft.Office.Interop.Word.Table.Range%2A> che consente di impostare gli attributi di formattazione.  
  
#### Per applicare uno stile a una tabella  
  
1.  Usare la proprietà <xref:Microsoft.Office.Interop.Word.Table.Style%2A> per applicare uno degli stili incorporati di Word a una tabella.  
  
     Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#88](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#88)]
     [!code-vb[Trin_VstcoreWordAutomation#88](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#88)]  
  
## Creazione di tabelle in componenti aggiuntivi VSTO  
  
#### Per aggiungere una tabella semplice in un documento  
  
-   Usare il metodo <xref:Microsoft.Office.Interop.Word.Tables.Add%2A> per aggiungere una tabella costituita da tre righe e quattro colonne all'inizio del documento.  
  
     L'esempio di codice seguente aggiunge una tabella al documento attivo.  Per usare questo esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#86](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#86)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#86](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#86)]  
  
 Quando si crea una tabella, viene aggiunta automaticamente alla raccolta <xref:Microsoft.Office.Interop.Word.Tables> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document>.  È quindi possibile fare riferimento alla tabella in base al numero dell'elemento usando la proprietà <xref:Microsoft.Office.Interop.Word.Tables.Item%2A>, come illustrato nel codice seguente.  
  
#### Per fare riferimento a una tabella in base al numero dell'elemento  
  
1.  Usare la proprietà <xref:Microsoft.Office.Interop.Word.Tables.Item%2A> e fornire il numero di elemento a cui si vuole fare riferimento.  
  
     L'esempio di codice seguente usa il documento attivo.  Per usare questo esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#87](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#87)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#87](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#87)]  
  
 Ogni oggetto <xref:Microsoft.Office.Interop.Word.Table> dispone anche di una proprietà <xref:Microsoft.Office.Interop.Word.Table.Range%2A> che consente di impostare gli attributi di formattazione.  
  
#### Per applicare uno stile a una tabella  
  
1.  Usare la proprietà <xref:Microsoft.Office.Interop.Word.Table.Style%2A> per applicare uno degli stili incorporati di Word a una tabella.  
  
     L'esempio di codice seguente usa il documento attivo.  Per usare questo esempio, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#88](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#88)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#88](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#88)]  
  
## Vedere anche  
 [Procedura: aggiungere testo e formattazione alle celle delle tabelle di Word a livello di codice](../vsto/how-to-programmatically-add-text-and-formatting-to-cells-in-word-tables.md)   
 [Procedura: aggiungere righe e colonne alle tabelle di Word a livello di codice](../vsto/how-to-programmatically-add-rows-and-columns-to-word-tables.md)   
 [Procedura: compilare tabelle di Word con le proprietà documento a livello di codice](../vsto/how-to-programmatically-populate-word-tables-with-document-properties.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  