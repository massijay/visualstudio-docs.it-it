---
title: "Procedura: Escludere i segni di paragrafo durante l&#39;inserimento di intervalli a livello di codice | Microsoft Docs"
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
  - "documenti [sviluppo per Office in Visual Studio], esclusione di paragrafi"
  - "intervalli, esclusione di segni di paragrafo in Word"
  - "documenti [sviluppo per Office in Visual Studio], segni di paragrafo"
  - "paragrafi, controllo della struttura"
ms.assetid: 6d563834-34bd-4462-a556-4339d9277eee
caps.latest.revision: 50
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 49
---
# Procedura: Escludere i segni di paragrafo durante l&#39;inserimento di intervalli a livello di codice
  Ogni volta che si crea un oggetto <xref:Microsoft.Office.Interop.Word.Range> basato su un paragrafo, tutti i caratteri non stampabili, ad esempio i segni di paragrafo, vengono inclusi nell'intervallo. Può essere necessario inserire testo da un paragrafo di origine in un paragrafo di destinazione. Se non si vuole suddividere il paragrafo di destinazione i paragrafi distinti, è necessario prima rimuovere i segni di paragrafo dal paragrafo di origine. Dal momento che all'interno del segno di paragrafo sono memorizzate le informazioni sulla formattazione dei paragrafi, può anche essere necessario escludere tali informazioni durante l'inserimento dell'intervallo in un paragrafo esistente.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
 La procedura di esempio riportata di seguito dichiara due variabili stringa, recupera il contenuto del primo e del secondo paragrafo nel documento attivo e ne scambia i contenuti. L'esempio quindi illustra come rimuovere il marcatore di paragrafo dall'intervallo usando il metodo <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> e inserendo testo all'interno del paragrafo.  
  
### Per controllare la struttura dei paragrafi durante l'inserimento di testo  
  
1.  Creare due variabili intervallo per il primo e il secondo paragrafo e recuperarne il contenuto usando la proprietà <xref:Microsoft.Office.Interop.Word.Range.Text%2A>.  
  
     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#27)]
     [!code-vb[Trin_VstcoreWordAutomation#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#27)]  
  
     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO a livello di applicazione. Questo codice usa il documento attivo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#27](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#27)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#27](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#27)]  
  
2.  Assegnare la proprietà <xref:Microsoft.Office.Interop.Word.Range.Text%2A>, scambiando il testo tra i due paragrafi.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#28](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#28)]
     [!code-vb[Trin_VstcoreWordAutomation#28](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#28)]  
  
3.  Selezionare uno per volta tutti gli intervalli e sospendere l'esecuzione del codice per visualizzare i risultati in una finestra di messaggio.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#29](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#29)]
     [!code-vb[Trin_VstcoreWordAutomation#29](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#29)]  
  
4.  Modificare `firstRange` usando il metodo <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> in modo che il marcatore di paragrafo non sia più incluso in `firstRange`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#30](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#30)]
     [!code-vb[Trin_VstcoreWordAutomation#30](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#30)]  
  
5.  Sostituire la parte restante del testo nel primo paragrafo assegnando una nuova stringa alla proprietà <xref:Microsoft.Office.Interop.Word.Range.Text%2A> dell'intervallo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#31](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#31)]
     [!code-vb[Trin_VstcoreWordAutomation#31](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#31)]  
  
6.  Sostituire il testo in `secondRange`, incluso il segno di paragrafo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#32](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#32)]
     [!code-vb[Trin_VstcoreWordAutomation#32](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#32)]  
  
7.  Selezionare `firstRange` e sospendere l'esecuzione del codice per visualizzare i risultati in una finestra di messaggio, quindi eseguire la stessa operazione con `secondRange`.  
  
     Dal momento che `firstRange` è stato ridefinito in modo da escludere il segno di paragrafo, è stata mantenuta la formattazione originale del paragrafo. È stata tuttavia inserita una frase al posto del segno di paragrafo in `secondRange`, rimuovendo di fatto il paragrafo separato.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#33](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#33)]
     [!code-vb[Trin_VstcoreWordAutomation#33](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#33)]  
  
     Dal momento che il contenuto originale di entrambi gli intervalli è stato salvato come stringa, è possibile ripristinare la condizione originale del documento.  
  
8.  Modificare nuovamente `firstRange` in modo da includere il segno di paragrafo usando il metodo <xref:Microsoft.Office.Interop.Word.Range.MoveEnd%2A> per una posizione di carattere.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#34](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#34)]
     [!code-vb[Trin_VstcoreWordAutomation#34](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#34)]  
  
9. Eliminare `secondRange`. In questo modo, il terzo paragrafo verrà ripristinato nella posizione originale.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#35](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#35)]
     [!code-vb[Trin_VstcoreWordAutomation#35](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#35)]  
  
10. Ripristinare il testo originale del paragrafo in `firstRange`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#36](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#36)]
     [!code-vb[Trin_VstcoreWordAutomation#36](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#36)]  
  
11. Usare il metodo <xref:Microsoft.Office.Interop.Word.Range.InsertAfter%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Range> per inserire il contenuto originale del secondo paragrafo dopo `firstRange`, quindi selezionare `firstRange`.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#37](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#37)]
     [!code-vb[Trin_VstcoreWordAutomation#37](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#37)]  
  
## Esempio di personalizzazione a livello di documento  
  
#### Per controllare la struttura dei paragrafi durante l'inserimento di testo nelle personalizzazioni a livello di documento  
  
1.  L'esempio seguente illustra il metodo completo per una personalizzazione a livello di documento. Per usare questo codice, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#26)]
     [!code-vb[Trin_VstcoreWordAutomation#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#26)]  
  
## Esempio di componente aggiuntivo VSTO  
  
#### Per controllare la struttura dei paragrafi durante l'inserimento di testo in un componente aggiuntivo VSTO  
  
1.  L'esempio seguente illustra il metodo completo per un componente aggiuntivo VSTO. Per usare questo codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#26](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#26)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#26](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#26)]  
  
## Vedere anche  
 [Procedura: Estendere gli intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-extend-ranges-in-documents.md)   
 [Procedura: Comprimere intervalli o selezioni in documenti a livello di codice](../vsto/how-to-programmatically-collapse-ranges-or-selections-in-documents.md)   
 [Procedura: inserire testo nei documenti di Word a livello di codice](../vsto/how-to-programmatically-insert-text-into-word-documents.md)   
 [Procedura: Reimpostare gli intervalli nei documenti di Word a livello di codice](../vsto/how-to-programmatically-reset-ranges-in-word-documents.md)   
 [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  