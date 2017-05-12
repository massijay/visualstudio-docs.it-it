---
title: "Procedura: definire e selezionare intervalli nei documenti a livello di codice"
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
  - "documenti [sviluppo per Office in Visual Studio], intervalli"
  - "documenti [sviluppo per Office in Visual Studio], selezione di frasi"
  - "intervalli, definizione nei documenti"
  - "intervalli, selezione nei documenti"
  - "frasi, selezione nei documenti"
ms.assetid: 0727c1cb-d44c-4f1c-a699-4365dd13be5d
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Procedura: definire e selezionare intervalli nei documenti a livello di codice
  È possibile definire un intervallo in un documento di Microsoft Office Word usando un oggetto <xref:Microsoft.Office.Interop.Word.Range>.  È possibile selezionare l'intero documento in diversi modi, ad esempio usando il metodo <xref:Microsoft.Office.Interop.Word.Range.Select%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Range> oppure usando la proprietà Content della classe <xref:Microsoft.Office.Tools.Word.Document> \(in una personalizzazione a livello di documento\) o della classe <xref:Microsoft.Office.Interop.Word.Document> \(in un componente aggiuntivo VSTO\).  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Definizione di un intervallo  
 L'esempio seguente illustra come creare un nuovo oggetto <xref:Microsoft.Office.Interop.Word.Range> che include i primi sette caratteri nel documento attivo, inclusi i caratteri non stampabili.  Viene quindi selezionato il testo incluso nell'intervallo.  
  
#### Per definire un intervallo in una personalizzazione a livello di documento  
  
1.  Aggiungere l'intervallo al documento passando un carattere di inizio e di fine al metodo <xref:Microsoft.Office.Tools.Word.Document.Range%2A> della classe <xref:Microsoft.Office.Tools.Word.Document>.  Per usare questo esempio di codice, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#18)]
     [!code-vb[Trin_VstcoreWordAutomation#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#18)]  
  
#### Per definire un intervallo mediante un componente aggiuntivo VSTO  
  
1.  Aggiungere l'intervallo al documento passando un carattere di inizio e di fine al metodo <xref:Microsoft.Office.Interop.Word._Document.Range%2A> della classe <xref:Microsoft.Office.Interop.Word.Document>.  L'esempio di codice seguente aggiunge un intervallo al documento attivo.  Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#18)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#18)]  
  
## Selezione di un intervallo in una personalizzazione a livello di documento  
 Gli esempi seguenti illustrano come selezionare l'intero documento usando il metodo <xref:Microsoft.Office.Interop.Word.Range.Select%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Range> oppure usando la proprietà <xref:Microsoft.Office.Tools.Word.Document.Content%2A> della classe <xref:Microsoft.Office.Tools.Word.Document>.  
  
#### Per selezionare l'intero documento come un intervallo mediante il metodo Select  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Range.Select%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Range> che contiene l'intero documento.  Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#19)]
     [!code-vb[Trin_VstcoreWordAutomation#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#19)]  
  
#### Per selezionare l'intero documento come un intervallo mediante la proprietà Content  
  
1.  Usare la proprietà <xref:Microsoft.Office.Tools.Word.Document.Content%2A> per definire un intervallo che include l'intero documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#20)]
     [!code-vb[Trin_VstcoreWordAutomation#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#20)]  
  
 È anche possibile usare i metodi e le proprietà di altri oggetti per definire un intervallo.  
  
#### Per selezionare una frase nel documento attivo  
  
1.  Configurare l'intervallo usando la raccolta <xref:Microsoft.Office.Interop.Word.Sentences>.  Usare l'indice della frase da selezionare.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#21)]
     [!code-vb[Trin_VstcoreWordAutomation#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#21)]  
  
 Un altro modo per selezionare una frase consiste nel configurare manualmente i valori di inizio e di fine per l'intervallo.  
  
#### Per selezionare una frase configurando manualmente i valori di inizio e di fine  
  
1.  Creare una variabile di intervallo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#23)]
     [!code-vb[Trin_VstcoreWordAutomation#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#23)]  
  
2.  Verificare se il documento include almeno due frasi, configurare gli argomenti *Start* e *End* dell'intervallo e quindi selezionare l'intervallo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#24)]
     [!code-vb[Trin_VstcoreWordAutomation#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#24)]  
  
## Selezione di un intervallo mediante un componente aggiuntivo VSTO  
 Gli esempi seguenti illustrano come selezionare l'intero documento usando il metodo <xref:Microsoft.Office.Interop.Word.Range.Select%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Range> oppure usando la proprietà <xref:Microsoft.Office.Interop.Word._Document.Content%2A> della classe <xref:Microsoft.Office.Interop.Word.Document>.  
  
#### Per selezionare l'intero documento come un intervallo mediante il metodo Select  
  
1.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Range.Select%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Range> che contiene l'intero documento.  L'esempio di codice seguente seleziona i contenuti del documento attivo.  Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#19](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#19)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#19](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#19)]  
  
#### Per selezionare l'intero documento come un intervallo mediante la proprietà Content  
  
1.  Usare la proprietà <xref:Microsoft.Office.Interop.Word._Document.Content%2A> per definire un intervallo che include l'intero documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#20](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#20)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#20](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#20)]  
  
 È anche possibile usare i metodi e le proprietà di altri oggetti per definire un intervallo.  
  
#### Per selezionare una frase nel documento attivo  
  
1.  Configurare l'intervallo usando la raccolta <xref:Microsoft.Office.Interop.Word.Sentences>.  Usare l'indice della frase da selezionare.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#21](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#21](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#21)]  
  
 Un altro modo per selezionare una frase consiste nel configurare manualmente i valori di inizio e di fine per l'intervallo.  
  
#### Per selezionare una frase configurando manualmente i valori di inizio e di fine  
  
1.  Creare una variabile di intervallo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#23](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#23)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#23](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#23)]  
  
2.  Verificare se il documento include almeno due frasi, configurare gli argomenti *Start* e *End* dell'intervallo e quindi selezionare l'intervallo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#24](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#24)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#24](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#24)]  
  
## Vedere anche  
 [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)   
 [Procedura: Estendere gli intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Procedura: Recuperare i caratteri iniziale e finale negli intervalli a livello di codice](../vsto/how-to-programmatically-retrieve-start-and-end-characters-in-ranges.md)   
 [Procedura: Estendere gli intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Procedura: Reimpostare gli intervalli nei documenti di Word a livello di codice](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Procedura: Comprimere intervalli o selezioni in documenti a livello di codice](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Procedura: Escludere i segni di paragrafo durante l'inserimento di intervalli a livello di codice](../vsto/how-to-programmatically-exclude-paragraph-marks-when-creating-ranges.md)  
  
  