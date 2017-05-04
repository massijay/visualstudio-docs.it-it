---
title: "Procedura: utilizzare le finestre di dialogo di Word in modalit&#224; nascosta a livello di codice | Microsoft Docs"
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
  - "finestre di dialogo, modalità nascosta in Word"
  - "finestre di dialogo nascoste"
  - "Word [sviluppo per Office in Visual Studio], finestre di dialogo"
ms.assetid: a5619325-8b54-41f1-becb-3f6eae7e4a6b
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# Procedura: utilizzare le finestre di dialogo di Word in modalit&#224; nascosta a livello di codice
  È possibile eseguire operazioni complesse con una sola chiamata al metodo richiamando le finestre di dialogo incorporate di Microsoft Office Word senza visualizzarle all'utente.  A tale scopo, utilizzare il metodo <xref:Microsoft.Office.Interop.Word.Dialog.Execute%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Dialog> senza chiamare il metodo <xref:Microsoft.Office.Interop.Word.Dialog.Display%2A>.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Esempi  
 Negli esempi di codice seguenti viene dimostrato come utilizzare la finestra di dialogo **Imposta pagina** in modalità nascosta per configurare più proprietà di impostazione pagina senza input dell'utente.  Negli esempi viene utilizzato un oggetto <xref:Microsoft.Office.Interop.Word.Dialog> per configurare dimensioni di pagina personalizzate.  Le impostazioni specifiche per l'impostazione di pagina, come il margine superiore, il margine inferiore e così via, sono disponibili come proprietà ad associazione tardiva dell'oggetto <xref:Microsoft.Office.Interop.Word.Dialog>.  Queste proprietà vengono create in modo dinamico da Word in fase di esecuzione.  
  
 Nell'esempio seguente viene dimostrato come eseguire questa attività nei progetti di Visual Basic in cui **Option Strict** non è attiva e nei progetti di Visual C\# che hanno come destinazione [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)].  In questi progetti, è possibile utilizzare funzionalità di associazione tardiva nei compilatori di Visual Basic e Visual C\#.  Per utilizzare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` del progetto.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#123](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#123)]
 [!code-vb[Trin_VstcoreWordAutomation#123](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#123)]  
  
 L'esempio seguente illustra come eseguire questa attività nei progetti di Visual Basic. **Option Strict** dove è attiva.  In questi progetti, è necessario utilizzare la reflection per accedere alle proprietà ad associazione tardiva.  Per utilizzare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` del progetto.  
  
 [!code-vb[Trin_VstcoreWordAutomation#104](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#104)]  
  
## Vedere anche  
 [Procedura: Usare finestre di dialogo incorporate in Word a livello di codice](../vsto/how-to-programmatically-use-built-in-dialog-boxes-in-word.md)   
 [Panoramica del modello a oggetti di Word](../vsto/word-object-model-overview.md)   
 [Associazione tardiva nelle soluzioni Office](../vsto/late-binding-in-office-solutions.md)   
 [Reflection &#40;C&#35; e Visual Basic&#41;](../Topic/Reflection%20(C%23%20and%20Visual%20Basic).md)  
  
  