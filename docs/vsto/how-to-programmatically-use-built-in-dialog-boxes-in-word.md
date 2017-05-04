---
title: "Procedura: Usare finestre di dialogo incorporate in Word a livello di codice | Microsoft Docs"
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
  - "Word [Office sviluppo per Office in Visual Studio], finestre di dialogo"
  - "finestre di dialogo, Word"
ms.assetid: 0c7e4338-dead-4444-868b-3b0212368455
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Procedura: Usare finestre di dialogo incorporate in Word a livello di codice
  Quando si utilizza Microsoft Office Word, è talvolta necessario visualizzare finestre di dialogo per l'input dell'utente.  Sebbene sia possibile creare finestre di dialogo personalizzate, può rivelarsi opportuno utilizzare le finestre di dialogo incorporate in Word, esposte nella raccolta <xref:Microsoft.Office.Interop.Word.Dialogs> dell'oggetto <xref:Microsoft.Office.Interop.Word.Application>.  In questo modo si può accedere a oltre 200 finestre di dialogo incorporate, rappresentate come enumerazioni.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Visualizzazione delle finestre di dialogo  
 Per visualizzare una finestra di dialogo, utilizzare uno dei valori dell'enumerazione <xref:Microsoft.Office.Interop.Word.WdWordDialog> per creare un oggetto <xref:Microsoft.Office.Interop.Word.Dialog> che rappresenta la finestra di dialogo da visualizzare.  Quindi, chiamare il metodo <xref:Microsoft.Office.Interop.Word.Dialog.Show%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Dialog>.  
  
 Nell'esempio di codice riportato di seguito viene illustrato come visualizzare la finestra di dialogo **Apri file**.  Per utilizzare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` del progetto.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#100](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#100)]
 [!code-vb[Trin_VstcoreWordAutomation#100](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#100)]  
  
### Accesso ai membri della finestra di dialogo disponibili tramite associazione tardiva  
 Alcune proprietà e metodi delle finestre di dialogo di Word sono disponibili solo tramite associazione tardiva.  Nei progetti di Visual Basic. **Option Strict** dove è attiva, è necessario utilizzare la reflection per accedere a questi membri.  Per ulteriori informazioni, vedere [Associazione tardiva nelle soluzioni Office](../vsto/late-binding-in-office-solutions.md).  
  
 Nell'esempio di codice seguente viene illustrato come utilizzare la proprietà di **Name** la finestra di dialogo **Apri file** nei progetti di Visual Basic. in cui **Option Strict** è attiva o in Visual c destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)].  Per utilizzare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` del progetto.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#122](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#122)]
 [!code-vb[Trin_VstcoreWordAutomation#122](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#122)]  
  
 Nell'esempio di codice seguente viene illustrato come utilizzare la reflection per accedere alla proprietà di **Name** la finestra di dialogo **Apri file** nei progetti di Visual Basic. in cui **Option Strict** è attivata.  Per utilizzare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` del progetto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#102)]  
  
## Vedere anche  
 [Procedura: utilizzare le finestre di dialogo di Word in modalità nascosta a livello di codice](../vsto/how-to-programmatically-use-word-dialog-boxes-in-hidden-mode.md)   
 [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflection &#40;C&#35; e Visual Basic&#41;](../Topic/Reflection%20(C%23%20and%20Visual%20Basic).md)  
  
  