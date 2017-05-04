---
title: "Procedura: Chiudere documenti a livello di codice | Microsoft Docs"
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
  - "documenti [sviluppo per Office in Visual Studio], chiusura"
  - "Word [sviluppo per Office in Visual Studio], chiusura di documenti"
ms.assetid: d5bee1dc-63d1-4307-828f-b7b077e20fb9
caps.latest.revision: 55
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 54
---
# Procedura: Chiudere documenti a livello di codice
  È possibile chiudere il documento attivo oppure specificare un documento da chiudere.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Chiusura del documento attivo  
 Esistono due procedure per chiudere il documento attivo: una per le personalizzazioni a livello di documento e una per i componenti aggiuntivi VSTO.  
  
#### Per chiudere il documento attivo in una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.Close%2A> della classe `ThisDocument` nel progetto per chiudere il documento associato alla personalizzazione. Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisDocument`.  
  
    > [!NOTE]  
    >  Questo esempio passa il valore <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> al parametro *SaveChanges* per chiudere il documento senza salvare le modifiche o chiedere conferma all'utente.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#3)]
     [!code-vb[Trin_VstcoreWordAutomation#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#3)]  
  
#### Per chiudere il documento attivo in un componente aggiuntivo VSTO  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.Close%2A> della proprietà <xref:Microsoft.Office.Interop.Word._Application.ActiveDocument%2A> per chiudere il documento attivo. Per usare l'esempio di codice seguente, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
    > [!NOTE]  
    >  Questo esempio passa il valore <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> al parametro *SaveChanges* per chiudere il documento senza salvare le modifiche o chiedere conferma all'utente.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#3](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#3)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#3](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#3)]  
  
## Chiusura di un documento specificato in base al nome  
 Il modo in cui viene chiuso un documento specificato in base al nome è identico per i componenti aggiuntivi VSTO e le personalizzazioni a livello di documento.  
  
#### Per chiudere un documento specificato in base al nome  
  
1.  Specificare il nome del documento come argomento per la raccolta <xref:Microsoft.Office.Interop.Word._Application.Documents%2A> e quindi chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.Close%2A>. L'esempio di codice seguente presuppone l'apertura in Word di un documento il cui nome è **NewDocument**.  
  
    > [!NOTE]  
    >  Questo esempio passa il valore <xref:Microsoft.Office.Interop.Word.WdSaveOptions.wdDoNotSaveChanges> al parametro *SaveChanges* per chiudere il documento senza salvare le modifiche o chiedere conferma all'utente.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#4](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#4)]
     [!code-vb[Trin_VstcoreWordAutomation#4](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#4)]  
  
## Vedere anche  
 [Procedura: aprire documenti esistenti a livello di codice](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Procedura: salvare documenti a livello di codice](../vsto/how-to-programmatically-save-documents.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  