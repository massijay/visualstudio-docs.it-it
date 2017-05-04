---
title: "Procedura: salvare documenti a livello di codice | Microsoft Docs"
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
  - "documenti [sviluppo per Office in Visual Studio], salvataggio"
  - "Word [sviluppo per Office in Visual Studio], salvataggio di documenti"
ms.assetid: a6225ae9-94f5-421a-9860-5299002d543d
caps.latest.revision: 44
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Procedura: salvare documenti a livello di codice
  Esistono molti modi per salvare i documenti di Microsoft Office Word.  È possibile salvare un documento senza modificarne il nome oppure con un nome nuovo.  
  
 [!INCLUDE[appliesto_wdalldocapp](../vsto/includes/appliesto-wdalldocapp-md.md)]  
  
## Salvataggio di un documento senza modificarne il nome  
  
#### Per salvare il documento associato a una personalizzazione a livello di documento  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.Save%2A> della classe <xref:Microsoft.Office.Tools.Word.Document>.  Per utilizzare questo esempio di codice, eseguirlo dalla classe `ThisDocument` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#7](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#7)]
     [!code-vb[Trin_VstcoreWordAutomation#7](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#7)]  
  
#### Per salvare il documento attivo  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.Save%2A> del documento attivo.  Per utilizzare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#8](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#8)]
     [!code-vb[Trin_VstcoreWordAutomation#8](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#8)]  
  
 Se non si è certi che il documento da salvare sia il documento attivo, è possibile farvi riferimento utilizzandone il nome.  
  
#### Per salvare un documento specificato mediante il nome  
  
1.  Utilizzare il nome del documento come argomento per la raccolta <xref:Microsoft.Office.Interop.Word.Documents>.  Per utilizzare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#9](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#9)]
     [!code-vb[Trin_VstcoreWordAutomation#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#9)]  
  
## Salvataggio di un documento con un nuovo nome  
 Utilizzare il metodo SaveAs per salvare un documento con un nuovo nome.  È possibile utilizzare questo metodo dell'elemento host <xref:Microsoft.Office.Tools.Word.Document> in un progetto Word a livello di documento o di un oggetto nativo <xref:Microsoft.Office.Interop.Word.Document> in qualsiasi progetto Word.  Questo metodo richiede che si specifichi il nuovo nome di file, mentre gli altri argomenti sono facoltativi.  
  
> [!NOTE]  
>  Se si visualizza la finestra di dialogo **SaveAs** all'interno del gestore eventi <xref:Microsoft.Office.Interop.Word.ApplicationEvents4_Event.DocumentBeforeSave> di `ThisDocument` e si imposta il parametro *Cancel* su **false**, l'applicazione potrebbe essere chiusa in modo imprevisto.  Se si imposta il parametro *Cancel* su **true**, un messaggio di errore indicherà che è stata disabilitata la funzione di salvataggio automatico.  
  
#### Per salvare il documento associato a una personalizzazione a livello di documento con un nuovo nome  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> della classe `ThisDocument` nel progetto utilizzando un nome file e un percorso completo.  Se nella stessa cartella è già presente un file con lo stesso nome, tale file verrà sovrascritto automaticamente.  Per utilizzare questo esempio di codice, eseguirlo dalla classe `ThisDocument`.  
  
    > [!NOTE]  
    >  Se la directory di destinazione non esiste o si verificano altri problemi durante il salvataggio di un file, il metodo <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> genera un'eccezione.  È opportuno utilizzare un blocco **try…catch** per racchiudere il metodo <xref:Microsoft.Office.Tools.Word.Document.SaveAs%2A> o all'interno di un metodo chiamante.  
  
     [!code-csharp[Trin_VstcoreWordAutomation#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#10)]
     [!code-vb[Trin_VstcoreWordAutomation#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#10)]  
  
#### Per salvare un documento nativo con un nuovo nome  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> dell'oggetto <xref:Microsoft.Office.Interop.Word.Document> che si desidera salvare, utilizzando un nome file e un percorso completo.  Se nella stessa cartella è già presente un file con lo stesso nome, tale file verrà sovrascritto automaticamente.  
  
     Nell'esempio di codice riportato di seguito viene salvato il documento attivo con un nuovo nome.  Per utilizzare questo esempio di codice, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` nel progetto.  
  
    > [!NOTE]  
    >  Se la directory di destinazione non esiste o si verificano altri problemi durante il salvataggio di un file, il metodo <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> genera un'eccezione.  È opportuno utilizzare un blocco **try…catch** per racchiudere il metodo <xref:Microsoft.Office.Interop.Word._Document.SaveAs%2A> o all'interno di un metodo chiamante.  
  
     [!code-csharp[Trin_VstcoreWordAutomationAddIn#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreWordAutomationAddIn#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomationAddIn/VB/ThisAddIn.vb#10)]  
  
## Compilazione del codice  
 Di seguito sono indicati i requisiti di questo esempio di codice:  
  
-   Per salvare un documento con il nome, è necessario che sull'unità C sia presente un documento denominato NewDocument.doc in una directory denominata Test.  
  
-   Per salvare un documento con un nuovo nome, è necessario che sull'unità C sia presente una directory denominata Test.  
  
## Vedere anche  
 [Procedura: Chiudere documenti a livello di codice](../vsto/how-to-programmatically-close-documents.md)   
 [Procedura: aprire documenti esistenti a livello di codice](../vsto/how-to-programmatically-open-existing-documents.md)   
 [Elemento host Document](../vsto/document-host-item.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  