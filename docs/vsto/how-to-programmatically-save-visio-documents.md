---
title: "Procedura: Salvare documenti di Visio a livello di codice | Microsoft Docs"
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
  - "documenti [sviluppo per Office in Visual Studio], salvataggio di documenti Visio"
  - "Visio [sviluppo per Office in Visual Studio], salvataggio di documenti di Visio"
ms.assetid: 1a29ac7e-1da4-4c7a-87a5-d3d16897fe7c
caps.latest.revision: 20
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 19
---
# Procedura: Salvare documenti di Visio a livello di codice
  Esistono varie modalità per salvare documenti di Microsoft Office Visio:  
  
-   Salvare le modifiche in un documento esistente.  
  
-   Salvare un nuovo documento oppure salvare un documento con un nuovo nome.  
  
-   Salvare un documento con gli argomenti specificati.  
  
 Per altre informazioni, vedere la documentazione di riferimento di VBA per i metodi [Microsoft.Office.Interop.Visio.Document.Save](HV10071468), [Microsoft.Office.Interop.Visio.Document.SaveAs](HV10071469) e [Microsoft.Office.Interop.Visio.Document.SaveAsEx](HV10071470).  
  
## Salvataggio un documento esistente  
  
#### Per salvare un documento  
  
-   Chiamare il metodo Microsoft.Office.Interop.Visio.Document.Save della classe Microsoft.Office.Tools.Visio.Document di un documento salvato in precedenza.  
  
     Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
    > [!NOTE]  
    >  Il metodo Microsoft.Office.Interop.Visio.Document.Save genera un'eccezione se non è stato ancora salvato un nuovo documento di Visio.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#11)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#11)]  
  
## Salvataggio di un documento con un nuovo nome  
 Usare il metodo Microsoft.Office.Interop.Visio.Document.SaveAs per salvare un nuovo documento oppure un documento che ha un nuovo nome. Con questo metodo è necessario specificare il nuovo nome del file.  
  
#### Per salvare il documento attivo con un nuovo nome  
  
-   Chiamare il metodo Microsoft.Office.Interop.Visio.Document.SaveAs di Microsoft.Office.Tools.Visio.Document che si vuole salvare usando un percorso completo che include un nome file. Se un file con quel nome già esiste in quella cartella, viene sovrascritto senza avvisare.  
  
     Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#10)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#10)]  
  
## Salvataggio di un documento con un nuovo nome e argomenti specificati  
 Usare il metodo Microsoft.Office.Interop.Visio.Document.SaveAsEx per salvare un documento con un nuovo nome e specificare qualsiasi argomento applicabile da applicare al documento.  
  
#### Per salvare un documento con un nuovo nome e argomenti specificati  
  
-   Chiamare il metodo Microsoft.Office.Interop.Visio.Document.SaveAsEx di Microsoft.Office.Tools.Visio.Document che si vuole salvare usando un percorso completo che include un nome file. Se un file con quel nome già esiste in quella cartella, viene generata un'eccezione.  
  
     L'esempio di codice seguente salva il documento attivo con un nuovo nome, lo contrassegna come di sola lettura e visualizza il documento nell'elenco di documenti Usati di recente. Per usare questo esempio di codice, eseguirlo dalla classe `ThisAddIn` nel progetto.  
  
     [!code-csharp[Trin_VstcoreVisioAutomationAddIn#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/CS/ThisAddIn.cs#12)]
     [!code-vb[Trin_VstcoreVisioAutomationAddIn#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreVisioAutomationAddIn/VB/ThisAddIn.vb#12)]  
  
## Compilazione del codice  
 Questo esempio di codice presenta i requisiti seguenti:  
  
-   Per salvare un documento con un nuovo nome, una directory denominata `Test` deve trovarsi nella cartella Documenti \(per Windows XP e versioni precedenti\) oppure nella cartella Documenti \(per Windows Vista\).  
  
## Vedere anche  
 [Soluzioni Visio](../vsto/visio-solutions.md)   
 [Panoramica del modello a oggetti di Visio](../vsto/visio-object-model-overview.md)   
 [Procedura: Creare nuovi documenti di Visio a livello di codice](../vsto/how-to-programmatically-create-new-visio-documents.md)   
 [Procedura: Aprire documenti di Visio a livello di codice](../vsto/how-to-programmatically-open-visio-documents.md)   
 [Procedura: Chiudere documenti di Visio a livello di codice](../vsto/how-to-programmatically-close-visio-documents.md)   
 [Procedura: Stampare documenti di Visio a livello di codice](../vsto/how-to-programmatically-print-visio-documents.md)  
  
  