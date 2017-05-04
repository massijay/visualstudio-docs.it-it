---
title: "Procedura: aprire documenti esistenti a livello di codice | Microsoft Docs"
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
  - "documenti [sviluppo per Office in Visual Studio], apertura"
  - "Word [sviluppo per Office in Visual Studio], apertura di documenti"
ms.assetid: 08f7fe4b-d96d-4a0c-b32a-aa7fd7992316
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Procedura: aprire documenti esistenti a livello di codice
  Con il metodo <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> viene aperto il documento di Microsoft Office Word esistente specificato mediante un nome file e un percorso completo.  Questo metodo restituisce un oggetto <xref:Microsoft.Office.Interop.Word.Document> che rappresenta il documento aperto.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
### Per aprire un documento  
  
-   Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Documents.Open%2A> della raccolta <xref:Microsoft.Office.Interop.Word.Documents> e fornire un percorso per il documento.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#5](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#5)]
     [!code-vb[Trin_VstcoreWordAutomation#5](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#5)]  
  
### Per aprire un documento in sola lettura  
  
-   Chiamare il metodo <xref:Microsoft.Office.Interop.Word.Documents.Open%2A>, fornire un percorso per il documento e impostare l'argomento *ReadOnly* su **True** nella chiamata al metodo.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#6](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#6)]
     [!code-vb[Trin_VstcoreWordAutomation#6](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#6)]  
  
## Compilazione del codice  
 Di seguito sono indicati i requisiti di questo esempio di codice:  
  
-   Sull'unità C deve essere presente un documento denominato NewDocument.doc in una directory denominata Test.  
  
## Vedere anche  
 [Procedura: creare nuovi documenti a livello di codice](../vsto/how-to-programmatically-create-new-documents.md)   
 [Procedura: Chiudere documenti a livello di codice](../vsto/how-to-programmatically-close-documents.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  