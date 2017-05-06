---
title: "Procedura: eseguire il controllo ortografico nei documenti a livello di codice"
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
  - "documenti [sviluppo per Office in Visual Studio], controllo dell'ortografia"
  - "controllo ortografico, documenti"
ms.assetid: 5bbe3a8d-fc65-4f57-bd63-5bb549dbc4bd
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# Procedura: eseguire il controllo ortografico nei documenti a livello di codice
  Per controllare l'ortografia in un documento, utilizzare il metodo <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A>.  Questo metodo restituisce un valore Boolean che indica se il parametro fornito è stato digitato correttamente.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Per eseguire il controllo ortografico e visualizzare i risultati in una finestra di messaggio  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Application.CheckSpelling%2A> e passare un intervallo di testo in cui verificare la presenza di errori ortografici.  Per utilizzare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#113](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#113)]
     [!code-vb[Trin_VstcoreWordAutomation#113](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#113)]  
  
## Vedere anche  
 [Procedura: definire e selezionare intervalli nei documenti a livello di codice](../vsto/how-to-programmatically-define-and-select-ranges-in-documents.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  