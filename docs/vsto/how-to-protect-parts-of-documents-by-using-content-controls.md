---
title: "Procedura: proteggere parti di documenti mediante i controlli del contenuto | Microsoft Docs"
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
  - "controlli del contenuto [sviluppo per Office in Visual Studio], protezione di documenti"
  - "protezione di documenti [sviluppo per Office in Visual Studio]"
  - "GroupContentControl"
  - "protezione parziale di documenti [sviluppo per Office in Visual Studio]"
  - "autorizzazioni limitate [sviluppo per Office in Visual Studio]"
  - "Word [sviluppo per Office in Visual Studio], protezione parziale di documenti"
  - "Word [sviluppo per Office in Visual Studio], autorizzazioni limitate"
ms.assetid: 50d7286a-7746-446f-8eef-06ceeadc94d0
caps.latest.revision: 28
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 27
---
# Procedura: proteggere parti di documenti mediante i controlli del contenuto
  Quando si protegge parte di un documento, si impedisce agli utenti di modificare o eliminare il contenuto in quella parte del documento.  È possibile proteggere parti di un documento di Microsoft Office Word usando i controlli contenuto in diversi modi.  
  
-   È possibile proteggere un controllo del contenuto.  
  
-   È possibile proteggere una parte di un documento non presente in un controllo del contenuto.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
##  <a name="EditDeleteControl"></a> Protezione di un controllo del contenuto  
 È possibile impedire agli utenti di modificare o eliminare un controllo del contenuto impostando le proprietà del controllo in un progetto a livello di documento in fase di progettazione o di esecuzione.  
  
 È anche possibile proteggere i controlli del contenuto aggiunti a un documento in fase di esecuzione con un progetto di componente aggiuntivo VSTO.  Per altre informazioni, vedere [Procedura: aggiungere controlli del contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md).  
  
#### Per proteggere un controllo del contenuto in fase di progettazione  
  
1.  Nel documento contenuto nella finestra di progettazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], selezionare il controllo del contenuto da proteggere.  
  
2.  Nella finestra **Proprietà**, impostare una o entrambe le seguenti proprietà:  
  
    -   Per impedire agli utenti di modificare il controllo, impostare **LockContents** su **True**.  
  
    -   Per impedire agli utenti di eliminare il controllo, impostare **LockContentControl** su **True**.  
  
3.  Fare clic su **OK**.  
  
#### Per proteggere un controllo del contenuto in fase di esecuzione  
  
1.  Impostare la proprietà `LockContents` del controllo del contenuto su **true** per impedire agli utenti di modificare il controllo e impostare la proprietà `LockContentControl` su **true** per impedire agli utenti di eliminare il controllo.  
  
     L'esempio di codice seguente illustra l'uso delle proprietà <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> e <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> di due oggetti <xref:Microsoft.Office.Tools.Word.RichTextContentControl> diversi in un progetto a livello di documento.  Per eseguire il codice, aggiungerlo alla classe `ThisDocument` nel progetto e chiamare il metodo `AddProtectedContentControls` dal gestore eventi `ThisDocument_Startup`.  
  
     [!code-csharp[Trin_ContentControlHowToProtect#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/CS/ThisDocument.cs#2)]
     [!code-vb[Trin_ContentControlHowToProtect#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/VB/ThisDocument.vb#2)]  
  
     L'esempio di codice seguente illustra l'uso delle proprietà <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContents%2A> e <xref:Microsoft.Office.Tools.Word.RichTextContentControl.LockContentControl%2A> di due oggetti <xref:Microsoft.Office.Tools.Word.RichTextContentControl> diversi in un progetto di componente aggiuntivo VSTO.  Per eseguire il codice, aggiungerlo alla classe `ThisAddIn` nel progetto e chiamare il metodo `AddProtectedContentControls` dal gestore eventi `ThisAddIn_Startup`.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#14)]
     [!code-vb[Trin_WordAddInDynamicControls#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#14)]  
  
## Protezione di una parte di un documento non presente in un controllo del contenuto  
 È possibile impedire agli utenti di modificare un'area di un documento inserendo l'area in un controllo <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  Questa operazione è utile negli scenari seguenti:  
  
-   Si vuole proteggere un'area che non contiene i controlli del contenuto.  
  
-   Si vuole proteggere un'area che contiene i controlli del contenuto, ma il testo o gli altri elementi da proteggere non sono nei controlli del contenuto.  
  
> [!NOTE]  
>  Se si crea un oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> che include controlli contenuto incorporati, questi non vengono automaticamente protetti.  Per impedire agli utenti di modificare un controllo del contenuto incorporato, usare la proprietà **LockContents** del controllo.  
  
#### Per proteggere un'area di un documento in fase di progettazione  
  
1.  Nel documento contenuto nella finestra di progettazione di [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], selezionare l'area da proteggere.  
  
2.  Sulla barra multifunzione fare clic sulla scheda **Sviluppatore**.  
  
    > [!NOTE]  
    >  Se la scheda **Sviluppatore** non è visibile, è necessario prima di tutto visualizzarla.  Per altre informazioni, vedere [Procedura: visualizzare la scheda Sviluppo nella barra multifunzione](../vsto/how-to-show-the-developer-tab-on-the-ribbon.md).  
  
3.  Nel gruppo **Controlli** fare clic sul pulsante a discesa **Gruppo** e fare clic su **Gruppo**.  
  
     L'oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl> contenente l'area protetta viene automaticamente generato nella classe `ThisDocument` del progetto.  Un bordo che rappresenta il controllo di gruppo è visibile in fase di progettazione, ma non esiste alcun bordo visibile in fase di esecuzione.  
  
#### Per proteggere un'area di un documento in fase di esecuzione  
  
1.  Selezionare a livello di codice l'area da proteggere, quindi chiamare il metodo <xref:Microsoft.Office.Tools.Word.ControlCollection.AddGroupContentControl%2A> per creare un oggetto <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  
  
     L'esempio di codice seguente per un progetto a livello di documento aggiunge del testo al primo paragrafo del documento, seleziona il primo paragrafo e quindi crea un'istanza di <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  Per eseguire il codice, aggiungerlo alla classe `ThisDocument` nel progetto e chiamare il metodo `ProtectFirstParagraph` dal gestore eventi `ThisDocument_Startup`.  
  
     [!code-csharp[Trin_ContentControlHowToProtect#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/CS/ThisDocument.cs#1)]
     [!code-vb[Trin_ContentControlHowToProtect#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ContentControlHowToProtect/VB/ThisDocument.vb#1)]  
  
     L'esempio di codice seguente per un progetto di componente aggiuntivo VSTO aggiunge del testo al primo paragrafo del documento attivo, seleziona il primo paragrafo e quindi crea un'istanza di <xref:Microsoft.Office.Tools.Word.GroupContentControl>.  Per eseguire il codice, aggiungerlo alla classe `ThisAddIn` nel progetto e chiamare il metodo `ProtectFirstParagraph` dal gestore eventi `ThisAddIn_Startup`.  
  
     [!code-csharp[Trin_WordAddInDynamicControls#15](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/CS/ThisAddIn.cs#15)]
     [!code-vb[Trin_WordAddInDynamicControls#15](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddInDynamicControls/VB/ThisAddIn.vb#15)]  
  
## Vedere anche  
 [Automazione di Word usando oggetti estesi](../vsto/automating-word-by-using-extended-objects.md)   
 [Controlli del contenuto](../vsto/content-controls.md)   
 [Procedura: aggiungere controlli del contenuto ai documenti di Word](../vsto/how-to-add-content-controls-to-word-documents.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Aggiunta di controlli ai documenti di Office in fase di esecuzione](../vsto/adding-controls-to-office-documents-at-run-time.md)  
  
  