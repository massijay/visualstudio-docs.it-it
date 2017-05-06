---
title: "Procedura: memorizzare dati nella cache di un documento protetto da password"
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
  - "dati [sviluppo per Office in Visual Studio], memorizzazione nella cache"
  - "memorizzazione di dati nella cache [sviluppo per Office in Visual Studio], documenti protetti"
  - "dataset [sviluppo per Office in Visual Studio], memorizzazione nella cache"
ms.assetid: 91b865fc-bd01-438f-ac63-2fe3175bc2e8
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 23
---
# Procedura: memorizzare dati nella cache di un documento protetto da password
  Se si aggiungono dati alla cache dei dati in un documento o una cartella di lavoro protetta con password, le modifiche ai dati memorizzati nella cache non vengono salvate automaticamente.  È possibile salvare le modifiche ai dati memorizzati nella cache eseguendo l'override di due metodi nel progetto.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Memorizzazione nella cache di documenti di Word  
  
#### Per memorizzare dati nella cache di un documento di Word protetto da password  
  
1.  Nella classe `ThisDocument`, contrassegnare una proprietà o un campo pubblico da memorizzare nella cache.  Per ulteriori informazioni, vedere [Memorizzazione di dati nella cache](../vsto/caching-data.md).  
  
2.  Eseguire l'override del metodo <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A> nella classe `ThisDocument` e rimuovere la protezione del documento.  
  
     Quando il documento viene salvato, attraverso il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] viene chiamato questo metodo per poter rimuovere la protezione del documento.  Questa operazione consente il salvataggio delle modifiche apportate ai dati memorizzati nella cache.  
  
3.  Eseguire l'override del metodo <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A> nella classe `ThisDocument` e riapplicare la protezione al documento.  
  
     Dopo avere salvato il documento, attraverso il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] viene chiamato questo metodo per poter riapplicare la protezione al documento.  
  
### Esempio  
 Nell'esempio di codice seguente viene illustrato come memorizzare dati nella cache di un documento di Word protetto con una password.  Prima di rimuovere la protezione attraverso il metodo <xref:Microsoft.Office.Tools.Word.DocumentBase.UnprotectDocument%2A>, il codice salva il valore <xref:Microsoft.Office.Tools.Word.Document.ProtectionType%2A> corrente, in modo che, tramite il metodo <xref:Microsoft.Office.Tools.Word.DocumentBase.ProtectDocument%2A>, sia possibile riapplicare lo stesso tipo di protezione.  
  
 [!code-csharp[Trin_CachedDataProtectedDocument#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataProtectedDocument/CS/ThisDocument.cs#1)]
 [!code-vb[Trin_CachedDataProtectedDocument#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataProtectedDocument/VB/ThisDocument.vb#1)]  
  
### Compilazione del codice  
 Aggiungere questo codice alla classe `ThisDocument` del progetto.  In questo codice si presuppone che la password sia memorizzata in un campo denominato `securelyStoredPassword`.  
  
## Memorizzazione nella cache delle cartelle di lavoro di Excel  
 Nei progetti Excel, questa procedura è necessaria solo quando si protegge l'intera cartella di lavoro con una password tramite il metodo <xref:Microsoft.Office.Tools.Excel.Workbook.Protect%2A>.  Questa procedura non è necessaria se si protegge solo un foglio di lavoro specifico con una password tramite il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Protect%2A>.  
  
#### Per memorizzare dati nella cache di una cartella di lavoro di Excel protetta da password  
  
1.  Nella classe `ThisWorkbook` o in una delle classi `Sheet`*n*, contrassegnare una proprietà o un campo pubblico da memorizzare nella cache.  Per ulteriori informazioni, vedere [Memorizzazione di dati nella cache](../vsto/caching-data.md).  
  
2.  Eseguire l'override del metodo <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A> nella classe `ThisWorkbook` e rimuovere la protezione della cartella di lavoro.  
  
     Quando la cartella di lavoro viene salvata, attraverso il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] viene chiamato questo metodo per poter rimuovere la protezione della cartella di lavoro.  Questa operazione consente il salvataggio delle modifiche apportate ai dati memorizzati nella cache.  
  
3.  Eseguire l'override del metodo <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A> nella classe `ThisWorkbook` e riapplicare la protezione al documento.  
  
     Dopo avere salvato la cartella di lavoro, attraverso il [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] viene chiamato questo metodo per poter riapplicare la protezione alla cartella di lavoro.  
  
### Esempio  
 Nell'esempio di codice seguente viene illustrato come memorizzare dati nella cache di una cartella di lavoro di Excel protetta con una password.  Prima di rimuovere la protezione attraverso il metodo <xref:Microsoft.Office.Tools.Excel.WorkbookBase.UnprotectDocument%2A>, il codice salva i valori <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectStructure%2A> e <xref:Microsoft.Office.Tools.Excel.Workbook.ProtectWindows%2A> correnti, in modo che, tramite il metodo <xref:Microsoft.Office.Tools.Excel.WorkbookBase.ProtectDocument%2A>, sia possibile riapplicare lo stesso tipo di protezione.  
  
 [!code-csharp[Trin_CachedDataProtectedWorkbook#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_CachedDataProtectedWorkbook/CS/ThisWorkbook.cs#1)]
 [!code-vb[Trin_CachedDataProtectedWorkbook#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_CachedDataProtectedWorkbook/VB/ThisWorkbook.vb#1)]  
  
### Compilazione del codice  
 Aggiungere questo codice alla classe `ThisWorkbook` del progetto.  In questo codice si presuppone che la password sia memorizzata in un campo denominato `securelyStoredPassword`.  
  
## Vedere anche  
 [Memorizzazione di dati nella cache](../vsto/caching-data.md)   
 [Procedura: memorizzare dati nella cache per l'utilizzo offline o su un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Procedura: memorizzare nella cache a livello di codice un'origine dati di un documento di Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)  
  
  