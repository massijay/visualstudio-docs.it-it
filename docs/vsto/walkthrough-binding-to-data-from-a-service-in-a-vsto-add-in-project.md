---
title: "Procedura dettagliata: Associazione ai dati di un servizio in un progetto di componente aggiuntivo VSTO"
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
  - "database [sviluppo per Office in Visual Studio], scorrimento di record"
  - "record [sviluppo per Office in Visual Studio], scorrimento"
  - "dati [sviluppo per Office in Visual Studio], scorrimento di record di database"
ms.assetid: 9b008be4-06a3-4ffc-9f02-79dd6cfe00ab
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Procedura dettagliata: Associazione ai dati di un servizio in un progetto di componente aggiuntivo VSTO
  È possibile associare dati ai controlli host nei progetti di componente aggiuntivo VSTO. Questa procedura dettagliata illustra come aggiungere controlli a un documento di Microsoft Office Word, associare i controlli ai dati recuperati dal servizio per la gestione del contenuto MSDN e rispondere agli eventi in fase di esecuzione.  
  
 **Si applica a:** le informazioni contenute in questo argomento sono valide per i progetti a livello di applicazione per Word 2010. Per altre informazioni, vedere [Funzionalità disponibili in base ai tipi di progetto e applicazioni di Office](../vsto/features-available-by-office-application-and-project-type.md).  
  
 Questa procedura dettagliata illustra le attività seguenti:  
  
-   Aggiunta di un controllo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> a un documento in fase di esecuzione.  
  
-   Associazione del controllo <xref:Microsoft.Office.Tools.Word.RichTextContentControl> ai dati di un servizio Web.  
  
-   Risposta all'evento <xref:Microsoft.Office.Tools.Word.ContentControlBase.Entering> di un controllo <xref:Microsoft.Office.Tools.Word.RichTextContentControl>.  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   [!INCLUDE[vsto_vsprereq](../vsto/includes/vsto-vsprereq-md.md)]  
  
-   [!INCLUDE[Word_15_short](../vsto/includes/word-15-short-md.md)] o [!INCLUDE[Word_14_short](../vsto/includes/word-14-short-md.md)].  
  
## Creazione di un nuovo progetto  
 Il primo passaggio consiste nel creare un progetto di componente aggiuntivo VSTO per Word.  
  
#### Per creare un nuovo progetto  
  
1.  Creare un progetto di componente aggiuntivo VSTO di Word denominato **MTPS Content Service** usando Visual Basic o C\#.  
  
     Per altre informazioni, vedere [Procedura: creare progetti di Office in Visual Studio](../vsto/how-to-create-office-projects-in-visual-studio.md).  
  
     Visual Studio apre il file `ThisAddIn.vb` o `ThisAddIn.cs` e aggiunge il progetto a **Esplora soluzioni**.  
  
## Aggiunta di un servizio Web  
 Per questa procedura dettagliata usare un servizio Web denominato MTPS Content Service. Questo servizio Web restituisce le informazioni da un determinato articolo MSDN sotto forma di stringa XML o testo normale. In un passaggio successivo viene illustrato come visualizzare le informazioni restituite in un controllo contenuto.  
  
#### Per aggiungere MTPS Content Service al progetto  
  
1.  Scegliere **Aggiungi nuova origine dati** dal menu **Dati**.  
  
2.  Nella **Configurazione guidata origine dati** fare clic su **Servizio** e quindi fare clic su **Avanti**.  
  
3.  Nel campo **Indirizzo** digitare l'URL seguente:  
  
     **http:\/\/services.msdn.microsoft.com\/ContentServices\/ContentService.asmx**  
  
4.  Fare clic su **Vai**.  
  
5.  Nel campo **Spazio dei nomi** digitare **ContentService** e fare clic su **OK**.  
  
6.  Nella finestra di dialogo della procedura guidata **Aggiungi riferimento** fare clic su **Fine**.  
  
## Aggiunta di un controllo contenuto e associazione ai dati in fase di esecuzione  
 Nei progetti di componente aggiuntivo VSTO è possibile aggiungere e associare i controlli in fase di esecuzione. Per questa procedura dettagliata, configurare il controllo contenuto in modo che recuperi i dati dal servizio Web quando un utente fa clic all'interno del controllo.  
  
#### Per aggiungere un controllo contenuto ed eseguire l'associazione a dati  
  
1.  Nella classe `ThisAddIn` dichiarare le variabili per il servizio MTPS Content Service, il controllo contenuto e il data binding.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#2](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#2)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#2](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#2)]  
  
2.  Aggiungere il metodo seguente alla classe `ThisAddIn`. Questo metodo crea un controllo contenuto all'inizio del documento attivo.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#4)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#4)]  
  
3.  Aggiungere il metodo seguente alla classe `ThisAddIn`. Questo metodo inizializza gli oggetti necessari per creare e inviare una richiesta al servizio Web.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#6)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#6)]  
  
4.  Creare un gestore eventi per recuperare il documento di MSDN Library relativo ai controlli contenuto quando un utente fa clic all'interno del controllo contenuto e associa i dati al controllo contenuto.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#5)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#5)]  
  
5.  Chiamare i metodi `AddRichTextControlAtRange` e `InitializeServiceObjects` dal metodo `ThisAddIn_Startup`. Per i programmatori C\#, aggiungere un gestore eventi.  
  
     [!code-csharp[Trin_WordAddIn_BindingDataToContentControl#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_WordAddIn_BindingDataToContentControl#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_WordAddIn_BindingDataToContentControl/VB/ThisAddIn.vb#3)]  
  
## Test del componente aggiuntivo  
 Quando si apre Word, viene visualizzato il controllo <xref:Microsoft.Office.Tools.Word.RichTextContentControl>. Il testo del controllo cambia quando si fa clic al suo interno.  
  
#### Per testare il componente aggiuntivo VSTO  
  
1.  Premere **F5**.  
  
2.  Fare clic all'interno del controllo contenuto.  
  
     Le informazioni vengono scaricate da MTPS Content Service e visualizzate nel controllo contenuto.  
  
## Vedere anche  
 [Associazione di dati ai controlli nelle soluzioni Office](../vsto/binding-data-to-controls-in-office-solutions.md)  
  
  