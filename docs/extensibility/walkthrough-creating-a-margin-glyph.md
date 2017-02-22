---
title: "Procedura dettagliata: Creazione di un glifo del margine | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], new - margine del glifo"
ms.assetid: 814185db-24f9-417f-b3b1-7c5aabb42b45
caps.latest.revision: 29
caps.handback.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura dettagliata: Creazione di un glifo del margine
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile personalizzare l'aspetto dei margini di editor utilizzando le estensioni di editor personalizzato. Questa procedura dettagliata consente di inserire un'icona personalizzata sul margine indicatore ogni volta che la parola "todo" viene visualizzata in un commento del codice.  
  
## Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [L'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Creazione di un progetto MEF  
  
1.  Creare un progetto VSIX in c\#. \(Nel **Nuovo progetto** finestra di dialogo, selezionare **Visual c\# \/ Extensibility**, quindi **progetto VSIX**.\) Denominare la soluzione `TodoGlyphTest`.  
  
2.  Aggiungere un elemento di progetto classificatore Editor. Per altre informazioni, vedere [Creazione di un'estensione con un modello di elemento di Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
## Definire il glifo  
 Definire un glifo mediante l'implementazione di <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory> interfaccia.  
  
#### Per definire il glifo  
  
1.  Aggiungere un file di classe e denominarla `TodoGlyphFactory`.  
  
2.  Aggiungere le seguenti dichiarazioni.  
  
     [!code-cs[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_1.cs)]
     [!code-vb[VSSDKTodoGlyphTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_1.vb)]  
  
3.  Aggiungere una classe denominata `TodoGlyphFactory` che implementa <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactory>.  
  
     [!code-cs[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_2.cs)]
     [!code-vb[VSSDKTodoGlyphTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_2.vb)]  
  
4.  Aggiungere un campo privato che definisce le dimensioni dell'icona.  
  
     [!code-cs[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_3.cs)]
     [!code-vb[VSSDKTodoGlyphTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_3.vb)]  
  
5.  Implementare `GenerateGlyph` definendo il glifo elemento interfaccia utente \(UI\).`TodoTag` viene definito più avanti in questa procedura dettagliata.  
  
     [!code-cs[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_4.cs)]
     [!code-vb[VSSDKTodoGlyphTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_4.vb)]  
  
6.  Aggiungere una classe denominata `TodoGlyphFactoryProvider` che implementa <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider>. Esportare questa classe con un <xref:Microsoft.VisualStudio.Utilities.NameAttribute> di "TodoGlyph", un <xref:Microsoft.VisualStudio.Utilities.OrderAttribute> di VsTextMarker dopo un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "code" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di TodoTag.  
  
     [!code-cs[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_5.cs)]
     [!code-vb[VSSDKTodoGlyphTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_5.vb)]  
  
7.  Implementare il <xref:Microsoft.VisualStudio.Text.Editor.IGlyphFactoryProvider.GetGlyphFactory%2A> metodo creando un'istanza di `TodoGlyphFactory`.  
  
     [!code-cs[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_6.cs)]
     [!code-vb[VSSDKTodoGlyphTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_6.vb)]  
  
## Definire un Tag di attività e ne  
 Definire la relazione tra l'elemento dell'interfaccia utente definiti nei passaggi precedenti e il margine indicatore creando un tipo di tag e tagger e l'esportazione tramite un provider tagger.  
  
#### Per definire un tag todo e tagger  
  
1.  Aggiungere un nuovo file di classe al progetto e denominarlo `TodoTagger`.  
  
2.  Aggiungere le seguenti istruzioni imports.  
  
     [!code-cs[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_7.cs)]
     [!code-vb[VSSDKTodoGlyphTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_7.vb)]  
  
3.  Aggiungere una classe denominata `TodoTag`.  
  
     [!code-cs[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_8.cs)]
     [!code-vb[VSSDKTodoGlyphTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_8.vb)]  
  
4.  Modificare la classe denominata `TodoTagger` che implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> di tipo `TodoTag`.  
  
     [!code-cs[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_9.cs)]
     [!code-vb[VSSDKTodoGlyphTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_9.vb)]  
  
5.  Per la `TodoTagger` classe, aggiungere campi privati per un <xref:Microsoft.VisualStudio.Text.Classification.IClassifier> e per il testo da trovare nella classificazione si estende.  
  
     [!code-cs[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_10.cs)]
     [!code-vb[VSSDKTodoGlyphTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_10.vb)]  
  
6.  Aggiungere un costruttore che imposta la funzione di classificazione.  
  
     [!code-cs[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_11.cs)]
     [!code-vb[VSSDKTodoGlyphTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_11.vb)]  
  
7.  Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodo individuando tutti la classificazione si estende i cui nomi includono la parola "commenti" e il cui testo include il testo di ricerca. Ogni volta che il testo di ricerca viene trovato, tornare producono un nuovo <xref:Microsoft.VisualStudio.Text.Tagging.TagSpan%601> di tipo `TodoTag`.  
  
     [!code-cs[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_12.cs)]
     [!code-vb[VSSDKTodoGlyphTest#12](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_12.vb)]  
  
8.  Dichiarare un `TagsChanged` evento.  
  
     [!code-cs[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_13.cs)]
     [!code-vb[VSSDKTodoGlyphTest#13](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_13.vb)]  
  
9. Aggiungere una classe denominata `TodoTaggerProvider` che implementa <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider>, ed esportarlo con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "code" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di TodoTag.  
  
     [!code-cs[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_14.cs)]
     [!code-vb[VSSDKTodoGlyphTest#14](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_14.vb)]  
  
10. Importazione di <xref:Microsoft.VisualStudio.Text.Classification.IClassifierAggregatorService>.  
  
     [!code-cs[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_15.cs)]
     [!code-vb[VSSDKTodoGlyphTest#15](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_15.vb)]  
  
11. Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITaggerProvider.CreateTagger%2A> metodo creando un'istanza di `TodoTagger`.  
  
     [!code-cs[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/CSharp/walkthrough-creating-a-margin-glyph_16.cs)]
     [!code-vb[VSSDKTodoGlyphTest#16](../extensibility/codesnippet/VisualBasic/walkthrough-creating-a-margin-glyph_16.vb)]  
  
## Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione TodoGlyphTest ed eseguirlo nell'istanza sperimentale.  
  
#### Per compilare e testare la soluzione TodoGlyphTest  
  
1.  Compilare la soluzione.  
  
2.  Eseguire il progetto premendo F5. Viene creata un'istanza di una seconda istanza di Visual Studio.  
  
3.  Assicurarsi che venga visualizzato il margine indicatore. \(Nel **strumenti** menu, fare clic su **Opzioni**. Scegliere il **Editor di testo** pagina, assicurarsi che **margine indicatore** è selezionata.\)  
  
4.  Aprire un file di codice con commenti. Aggiungere la parola "todo" a una delle sezioni di commento.  
  
5.  Nel margine indicatore a sinistra della finestra del codice dovrebbe essere visualizzato un cerchio blu chiaro con un contorno blu scuro.