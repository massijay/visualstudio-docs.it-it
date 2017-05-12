---
title: "Procedura: impostare opzioni di ricerca in Word a livello di codice"
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
  - "documenti [sviluppo per Office in Visual Studio], opzioni di ricerca"
  - "ricerca, opzioni di Word"
  - "impostazioni, opzioni di ricerca di Word"
  - "Word, opzioni di ricerca"
ms.assetid: 4412b4e8-2868-4afb-a593-983603ef9b02
caps.latest.revision: 46
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 45
---
# Procedura: impostare opzioni di ricerca in Word a livello di codice
  Esistono due metodi per impostare le opzioni di ricerca delle selezioni nei documenti di Microsoft Office Word:  
  
-   Impostare singole proprietà di un oggetto <xref:Microsoft.Office.Interop.Word.Find>.  
  
-   Utilizzare gli argomenti del metodo <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Find>.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Utilizzo delle proprietà di un oggetto Find  
 Nel codice riportato di seguito vengono impostate le proprietà di un oggetto <xref:Microsoft.Office.Interop.Word.Find> per ricercare un testo all'interno della selezione corrente.  I criteri di ricerca, come la direzione della ricerca, il ritorno a capo e l'indicazione del testo da ricercare, rappresentano proprietà dell'oggetto <xref:Microsoft.Office.Interop.Word.Find>.  
  
 L'impostazione delle singole proprietà dell'oggetto <xref:Microsoft.Office.Interop.Word.Find> risulta di scarsa utilità quando si scrive codice C\#, in quanto è necessario specificare le stesse proprietà come parametri nel metodo <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>.  In questo esempio è quindi contenuto solo codice di Visual Basic.  
  
#### Per impostare opzioni di ricerca mediante un oggetto Find  
  
1.  Impostare le proprietà di un oggetto <xref:Microsoft.Office.Interop.Word.Find> per la ricerca del testo **find me** all'interno di una selezione.  
  
     [!code-vb[Trin_VstcoreWordAutomation#76](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#76)]  
  
## Utilizzo degli argomenti del metodo Execute  
 Nel codice riportato di seguito viene utilizzato il metodo <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> di un oggetto <xref:Microsoft.Office.Interop.Word.Find> per ricercare un testo all'interno della selezione corrente.  I criteri di ricerca, come la direzione della ricerca, il ritorno a capo e l'indicazione del testo da ricercare, sono passati come parametri del metodo <xref:Microsoft.Office.Interop.Word.Find.Execute%2A>.  
  
#### Per impostare opzioni di ricerca mediante gli argomenti del metodo Execute  
  
1.  Passare i criteri di ricerca come parametri del metodo <xref:Microsoft.Office.Interop.Word.Find.Execute%2A> per eseguire la ricerca del testo **find me** all'interno di una selezione.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#77](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#77)]
     [!code-vb[Trin_VstcoreWordAutomation#77](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#77)]  
  
## Vedere anche  
 [Procedura: cercare e sostituire testo nei documenti a livello di codice](../vsto/how-to-programmatically-search-for-and-replace-text-in-documents.md)   
 [Procedura: Scorrere in ciclo gli elementi trovati nei documenti a livello di codice](../vsto/how-to-programmatically-loop-through-found-items-in-documents.md)   
 [Procedura: ripristinare le selezioni dopo le ricerche a livello di codice](../vsto/how-to-programmatically-restore-selections-after-searches.md)  
  
  