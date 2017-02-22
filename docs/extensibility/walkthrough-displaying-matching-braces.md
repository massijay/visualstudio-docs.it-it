---
title: "Procedura dettagliata: Visualizzazione di parentesi graffe corrispondenti | Microsoft Docs"
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
  - "editor [Visual Studio SDK], nuovo, corrispondenza parentesi"
ms.assetid: 5af08ac7-1d08-4ccf-997e-01aa6cb3d3d7
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# Procedura dettagliata: Visualizzazione di parentesi graffe corrispondenti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile implementare funzionalità basate sul linguaggio, ad esempio definendo le parentesi graffe che si desidera cercare e quindi aggiungere un tag dell'indicatore di testo le parentesi graffe corrispondenti quando il cursore si trova su una delle parentesi graffe corrispondenza parentesi graffe. È possibile definire le parentesi graffe nel contesto di una lingua, è possibile definire il tipo di estensione e il contenuto di nome file e applicare i tag solo quel tipo o è possibile applicare i tag a un tipo di contenuto esistente \(ad esempio "text"\). La procedura riportata di seguito viene illustrato come applicare dei tag per il tipo di contenuto "text" corrispondenza parentesi graffe.  
  
## Prerequisiti  
 A partire da Visual Studio 2015, non installare Visual Studio SDK dall'area download. È incluso come funzionalità facoltativa nel programma di installazione di Visual Studio. È inoltre possibile installare il SDK di Visual Studio in un secondo momento. Per altre informazioni, vedere [L'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## Creazione di un progetto Managed Extensibility Framework \(MEF\)  
  
#### Per creare un progetto MEF  
  
1.  Creare un progetto di classificatore editor. Denominare la soluzione `BraceMatchingTest`.  
  
2.  Aggiungere un modello di elemento di Editor classificatore al progetto. Per altre informazioni, vedere [Creazione di un'estensione con un modello di elemento di Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
3.  Eliminare i file di classe esistenti.  
  
## Implementazione di una parentesi graffa corrispondente Tagger  
 Per ottenere un'effetto simile a quello utilizzato in Visual Studio di evidenziazione parentesi graffe, è possibile implementare un tagger del tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>. Il codice seguente viene illustrato come definire il tagger per le coppie di parentesi graffa a qualsiasi livello di annidamento. In questo esempio, la parentesi graffa coppie \[\]. \[\], {} sono definiti nel costruttore tagger, ma in un'implementazione completa del linguaggio le coppie di parentesi graffa pertinente deve essere definite nella specifica del linguaggio.  
  
#### Per implementare una parentesi graffa corrispondente tagger  
  
1.  Aggiungere un file di classe e denominarla corrispondenza parentesi graffe.  
  
2.  Importare gli spazi dei nomi seguenti.  
  
     [!code-cs[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_1.cs)]
     [!code-vb[VSSDKBraceMatchingTest#1](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_1.vb)]  
  
3.  Definire una classe `BraceMatchingTagger` che eredita da <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> di tipo <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-cs[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_2.cs)]
     [!code-vb[VSSDKBraceMatchingTest#2](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_2.vb)]  
  
4.  Aggiungere le proprietà per la visualizzazione di testo, il buffer di origine e il punto dello snapshot corrente e anche un set di coppie di parentesi graffe.  
  
     [!code-cs[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_3.cs)]
     [!code-vb[VSSDKBraceMatchingTest#3](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_3.vb)]  
  
5.  Nel costruttore tagger, impostare le proprietà e sottoscrivere gli eventi di modifica della visualizzazione <xref:Microsoft.VisualStudio.Text.Editor.ITextCaret.PositionChanged> e <xref:Microsoft.VisualStudio.Text.Editor.ITextView.LayoutChanged>. In questo esempio, solo a scopo illustrativo, le coppie corrispondenti sono definite anche nel costruttore.  
  
     [!code-cs[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_4.cs)]
     [!code-vb[VSSDKBraceMatchingTest#4](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_4.vb)]  
  
6.  Come parte di <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601> implementazione, dichiarare un evento TagsChanged.  
  
     [!code-cs[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_5.cs)]
     [!code-vb[VSSDKBraceMatchingTest#5](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_5.vb)]  
  
7.  I gestori eventi aggiornano la posizione corrente del cursore della `CurrentChar` proprietà e generare l'evento TagsChanged.  
  
     [!code-cs[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_6.cs)]
     [!code-vb[VSSDKBraceMatchingTest#6](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_6.vb)]  
  
8.  Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.ITagger%601.GetTags%2A> metodo per la corrispondenza parentesi graffe di apertura sia quando il carattere corrente è una parentesi graffa aperta o quando il carattere precedente è una parentesi graffa di chiusura, come in Visual Studio. Quando viene trovata la corrispondenza, questo metodo crea un'istanza di due tag, uno per la parentesi graffa di apertura e uno per la parentesi graffa di chiusura.  
  
     [!code-cs[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_7.cs)]
     [!code-vb[VSSDKBraceMatchingTest#7](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_7.vb)]  
  
9. I seguenti metodi privati trovare la parentesi graffa corrispondente a qualsiasi livello di annidamento. Il primo metodo rileva il carattere di chiuso che corrisponda al carattere aperto:  
  
     [!code-cs[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_8.cs)]
     [!code-vb[VSSDKBraceMatchingTest#8](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_8.vb)]  
  
10. Il seguente metodo helper rileva il carattere aperto che corrisponde a un carattere di chiuso:  
  
     [!code-cs[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_9.cs)]
     [!code-vb[VSSDKBraceMatchingTest#9](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_9.vb)]  
  
## Implementazione di una parentesi graffa corrispondente Tagger Provider  
 Oltre all'implementazione un tagger, è inoltre necessario implementare ed esportare un provider tagger. In questo caso, il tipo di contenuto del provider è "text". Ciò significa che con parentesi graffe corrispondenti verranno visualizzati tutti i tipi di file di testo, ma un'implementazione completa è applicabile solo a un tipo di contenuto specifico corrispondenza parentesi graffe.  
  
#### Implementare un provider tagger corrispondente parentesi graffa  
  
1.  Dichiarare un provider tagger che eredita da <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider>, denominarla BraceMatchingTaggerProvider e l'esportazione con un <xref:Microsoft.VisualStudio.Utilities.ContentTypeAttribute> di "text" e un <xref:Microsoft.VisualStudio.Text.Tagging.TagTypeAttribute> di <xref:Microsoft.VisualStudio.Text.Tagging.TextMarkerTag>.  
  
     [!code-cs[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_10.cs)]
     [!code-vb[VSSDKBraceMatchingTest#10](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_10.vb)]  
  
2.  Implementare il <xref:Microsoft.VisualStudio.Text.Tagging.IViewTaggerProvider.CreateTagger%2A> metodo per creare un'istanza di un BraceMatchingTagger.  
  
     [!code-cs[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/CSharp/walkthrough-displaying-matching-braces_11.cs)]
     [!code-vb[VSSDKBraceMatchingTest#11](../extensibility/codesnippet/VisualBasic/walkthrough-displaying-matching-braces_11.vb)]  
  
## Compilazione e testing del codice  
 Per testare questo codice, compilare la soluzione BraceMatchingTest ed eseguirlo nell'istanza sperimentale.  
  
#### Per compilare e testare soluzioni BraceMatchingTest  
  
1.  Compilare la soluzione.  
  
2.  Quando si esegue questo progetto nel debugger, viene creata una seconda istanza di Visual Studio.  
  
3.  Creare un file di testo e digitare un testo che include parentesi graffe corrispondenti.  
  
    ```  
    hello {  
    goodbye}  
  
    {}  
  
    {hello}  
    ```  
  
4.  Quando si posiziona il punto di inserimento prima di una parentesi graffa aperta, sia la parentesi graffa e la parentesi graffa di chiusura corrispondente dovrebbe essere evidenziata. Quando si posiziona il cursore subito dopo la parentesi graffa di chiusura, dovrebbe essere evidenziata sia la parentesi graffa e la corrispondente parentesi graffa aperta.  
  
## Vedere anche  
 [Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione nome File](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)