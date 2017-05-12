---
title: "Procedura: cercare e sostituire testo nei documenti a livello di codice"
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
  - "documenti [sviluppo per Office in Visual Studio], ricerca"
  - "testo [sviluppo per Office in Visual Studio], ricerca in documenti"
  - "testo [sviluppo per Office in Visual Studio], ricerche di testo"
  - "ricerche di testo, documenti"
  - "ricerche di testo, sostituzione di testo"
ms.assetid: a66962f5-eeb9-4dc6-a70f-9039ab437a63
caps.latest.revision: 51
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 50
---
# Procedura: cercare e sostituire testo nei documenti a livello di codice
  L'oggetto <xref:Microsoft.Office.Interop.Word.Find> è un membro degli oggetti <xref:Microsoft.Office.Interop.Word.Selection> e <xref:Microsoft.Office.Interop.Word.Range>, ognuno dei quali può essere usato per cercare testo in documenti di Microsoft Office Word.  Il comando di sostituzione è un'estensione del comando di ricerca.  
  
 Usare un oggetto <xref:Microsoft.Office.Interop.Word.Find> per scorrere in ciclo un documento di Microsoft Office Word e cercare testo, formattazione o uno stile specifico e quindi usare la proprietà <xref:Microsoft.Office.Interop.Word.Find.Replacement%2A> per sostituire tutti gli elementi trovati.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Uso di un oggetto Selection  
 Quando si usa un oggetto <xref:Microsoft.Office.Interop.Word.Selection> per trovare testo, tutti i criteri di ricerca specificati vengono applicati solo in base al testo attualmente selezionato.  Se <xref:Microsoft.Office.Interop.Word.Selection> è un punto di inserimento, la ricerca viene eseguita nel documento.  Quando viene trovato un elemento che corrisponde ai criteri di ricerca, l'elemento viene automaticamente selezionato.  
  
 È importante notare che i criteri <xref:Microsoft.Office.Interop.Word.Find> sono cumulativi, ovvero vengono aggiunti a criteri di ricerca precedenti.  Cancellare la formattazione dalle ricerche precedenti usando il metodo <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> prima della ricerca.  
  
#### Per trovare testo usando un oggetto Selection  
  
1.  Assegnare una stringa di ricerca a una variabile.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#68](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#68)]
     [!code-vb[Trin_VstcoreWordAutomation#68](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#68)]  
  
2.  Cancellare la formattazione dalle ricerche precedenti.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#69](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#69)]
     [!code-vb[Trin_VstcoreWordAutomation#69](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#69)]  
  
3.  Eseguire la ricerca e visualizzare una finestra di messaggio con i risultati.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#70](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#70)]
     [!code-vb[Trin_VstcoreWordAutomation#70](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#70)]  
  
 L'esempio seguente mostra il metodo completo.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#67](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#67)]
 [!code-vb[Trin_VstcoreWordAutomation#67](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#67)]  
  
## Uso di un oggetto Range  
 L'uso di un oggetto <xref:Microsoft.Office.Interop.Word.Range> permette di cercare testo senza alcuna visualizzazione nell'interfaccia utente.  L'oggetto <xref:Microsoft.Office.Interop.Word.Find> restituisce **True** se viene trovato testo che corrisponde ai criteri di ricerca e **False** in caso contrario.  Ridefinisce inoltre l'oggetto <xref:Microsoft.Office.Interop.Word.Range> in modo che corrisponda ai criteri di ricerca se viene trovato testo.  
  
#### Per trovare testo usando un oggetto Range  
  
1.  Definire un oggetto <xref:Microsoft.Office.Interop.Word.Range> costituito dal secondo paragrafo del documento.  
  
     L'esempio di codice seguente può essere usato in una personalizzazione a livello di documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#72](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#72)]
     [!code-vb[Trin_VstcoreWordAutomation#72](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#72)]  
  
     L'esempio di codice seguente può essere usato in un componente aggiuntivo VSTO.  L'esempio usa il documento attivo.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#72](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#72)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#72](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#72)]  
  
2.  Usando la proprietà <xref:Microsoft.Office.Interop.Word.Range.Find%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Range>, cancellare prima di tutto qualsiasi opzione di formattazione esistente e quindi cercare la stringa **find me**.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#73](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#73)]
     [!code-vb[Trin_VstcoreWordAutomation#73](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#73)]  
  
3.  Visualizzare i risultati della ricerca in una finestra di messaggio e selezionare l'oggetto <xref:Microsoft.Office.Interop.Word.Range> per renderla visibile.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#74](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#74)]
     [!code-vb[Trin_VstcoreWordAutomation#74](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#74)]  
  
     Se la ricerca non riesce, viene selezionato il secondo paragrafo, altrimenti vengono visualizzati i criteri di ricerca.  
  
 L'esempio seguente mostra il codice completo per una personalizzazione a livello di documento.  Per usare questo esempio, eseguire il codice dalla classe `ThisDocument` nel progetto.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#71](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#71)]
 [!code-vb[Trin_VstcoreWordAutomation#71](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#71)]  
  
 L'esempio seguente mostra il codice completo per un componente aggiuntivo VSTO.  Per usare questo esempio, eseguire il codice dalla classe `ThisAddIn` nel progetto.  
  
 [!code-csharp[Trin_VstcoreWordAutomationAddIn#71](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#71)]
 [!code-vb[Trin_VstcoreWordAutomationAddIn#71](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#71)]  
  
## Ricerca e sostituzione di testo in documenti  
 Il codice seguente cerca la selezione corrente e sostituisce tutte le occorrenze della stringa **find me** con la stringa **Found**.  
  
#### Per cercare e sostituire testo in documenti  
  
1.  Aggiungere il codice di esempio seguente alla classe `ThisDocument` o `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#75](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#75)]
     [!code-vb[Trin_VstcoreWordAutomation#75](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#75)]  
  
     La classe <xref:Microsoft.Office.Interop.Word.Find> ha un metodo <xref:Microsoft.Office.Interop.Word.Find.ClearFormatting%2A> e anche la classe <xref:Microsoft.Office.Interop.Word.Replacement> ha il proprio metodo <xref:Microsoft.Office.Interop.Word.Replacement.ClearFormatting%2A>.  Quando si eseguono operazioni di ricerca e sostituzione, è necessario usare il metodo ClearFormatting di entrambi gli oggetti.  Se si usa solo il metodo per l'oggetto <xref:Microsoft.Office.Interop.Word.Find>, il testo di sostituzione potrebbe restituire risultati imprevisti.  
  
2.  Usare il metodo <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Find> per sostituire ogni elemento trovato.  Per specificare gli elementi da sostituire, usare il parametro *Replace*.  Questo parametro può avere uno dei valori <xref:Microsoft.Office.Interop.Word.WdReplace> seguenti:  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceAll> sostituisce tutti gli elementi trovati.  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceNone> non sostituisce alcun elemento trovato.  
  
    -   <xref:Microsoft.Office.Interop.Word.WdReplace.wdReplaceOne> sostituisce il primo elemento trovato.  
  
## Vedere anche  
 [Procedura: impostare opzioni di ricerca in Word a livello di codice](../vsto/how-to-programmatically-set-search-options-in-word.md)   
 [Procedura: Scorrere in ciclo gli elementi trovati nei documenti a livello di codice](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Procedura: ripristinare le selezioni dopo le ricerche a livello di codice](../vsto/how-to-programmatically-restore-selections-after-searches.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  