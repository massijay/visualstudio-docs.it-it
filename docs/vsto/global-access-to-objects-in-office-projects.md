---
title: "Accesso globale a oggetti nei progetti di Office"
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
  - "ThisDocument_Shutdown"
  - "ThisDocument_Startup"
  - "classi globali, accesso globale agli oggetti"
  - "fogli di lavoro [sviluppo per Office in Visual Studio], accesso globale"
  - "documenti [sviluppo per Office in Visual Studio], accesso globale"
  - "gestori eventi [sviluppo per Office in Visual Studio]"
  - "ThisWorkbook_Startup"
  - "componenti aggiuntivi a livello di applicazione [sviluppo per Office in Visual Studio]"
  - "componenti aggiuntivi [sviluppo per Office in Visual Studio], eventi"
  - "cartelle di lavoro [sviluppo per Office in Visual Studio], accesso globale"
  - "ThisWorkbook_Shutdown"
  - "personalizzazioni a livello di documento [sviluppo per Office in Visual Studio]"
  - "Startup (evento)"
  - "Shutdown (evento)"
  - "progetti [sviluppo per Office in Visual Studio], accesso globale"
  - "documenti di Office [sviluppo per Office in Visual Studio], accesso globale"
  - "ThisAddin_Startup"
  - "eventi [sviluppo per Office in Visual Studio]"
  - "ThisAddIn_Shutdown"
ms.assetid: f6a7f0ef-75d0-4a9b-9aec-be95ffa26adf
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Accesso globale a oggetti nei progetti di Office
  Quando si crea un progetto di Office, Visual Studio genera automaticamente una classe denominata `Globals` nel progetto. È possibile usare la classe `Globals` per accedere ai diversi elementi del progetto in fase di esecuzione da qualsiasi codice del progetto.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
## Come usare la classe Globals  
 `Globals` è una classe statica che mantiene i riferimenti ad alcuni elementi del progetto. Usando la `Globals`, è possibile accedere agli elementi seguenti da qualsiasi codice del progetto in fase di esecuzione:  
  
-   Le classi `ThisWorkbook` e `Sheet`*n* in un progetto modello o cartella di lavoro di Excel. È possibile accedere a questi oggetti usando le proprietà `Globals.ThisWorkbook` e `Sheet`*n*.  
  
-   La classe `ThisDocument` in un progetto modello o documento di Word. È possibile accedere a questo oggetto stato usando la proprietà `Globals.ThisDocument`.  
  
-   La classe `ThisAddIn` in un progetto di componente aggiuntivo VSTO. È possibile accedere a questo oggetto stato usando la proprietà `Globals.ThisAddIn`.  
  
-   Tutte le barre multifunzione del progetto che sono state personalizzate usando la finestra di progettazione della barra multifunzione. È possibile accedere alle barre multifunzione usando la proprietà `Globals.Ribbons`. Per altre informazioni, vedere [Accesso alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md).  
  
-   Tutte le aree del modulo di Outlook in un progetto di componente aggiuntivo VSTO di Outlook. È possibile accedere alle aree del modulo usando la proprietà `Globals.FormRegions`. Per altre informazioni, vedere [Accesso a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md).  
  
-   L'oggetto factory che consente di creare controlli della barra multifunzione e ospitare elementi in fase di esecuzione nei progetti destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)]. È possibile accedere a questo oggetto stato usando la proprietà `Globals.Factory`. Questo oggetto è l'istanza di una classe che implementa una le interfacce seguenti:  
  
    -   <xref:Microsoft.Office.Tools.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Excel.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Outlook.Factory>  
  
    -   <xref:Microsoft.Office.Tools.Word.Factory>  
  
 Ad esempio, è possibile usare la proprietà `Globals.Sheet1` per inserire testo in un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> in `Sheet1` quando un utente fa clic su un pulsante del riquadro delle azioni in un progetto livello di documento per Excel.  
  
 [!code-csharp[Trin_VstcoreProgramming#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/Sheet1.cs#1)]
 [!code-vb[Trin_VstcoreProgramming#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#1)]  
  
## Inizializzazione della classe Globals  
 Il codice che prova a usare la classe `Globals` prima che il documento o il componente aggiuntivo VSTO sia completamente inizializzato potrebbe generare un'eccezione in fase di esecuzione. Ad esempio, l'utilizzo di `Globals` per la dichiarazione di una variabile a livello di classe potrebbe avere esito negativo perché la classe `Globals` potrebbe non essere inizializzata con i riferimenti a tutti gli elementi host prima della creazione di un'istanza dell'oggetto dichiarato.  
  
> [!NOTE]  
>  La classe `Globals` non viene mai inizializzata in fase di progettazione, ma vengono create istanze di controllo nella finestra di progettazione. Ciò significa che se si crea un controllo utente che usa una proprietà della classe `Globals` all'interno di una classe del controllo utente, è necessario verificare se la proprietà restituisce **null** prima di provare a usare l'oggetto restituito.  
  
## Vedere anche  
 [Accesso alla barra multifunzione in fase di esecuzione](../vsto/accessing-the-ribbon-at-run-time.md)   
 [Accesso a un'area del modulo in fase di esecuzione](../vsto/accessing-a-form-region-at-run-time.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Elemento host Document](../vsto/document-host-item.md)   
 [Elemento host Workbook](../vsto/workbook-host-item.md)   
 [Elemento host Worksheet](../vsto/worksheet-host-item.md)   
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)  
  
  