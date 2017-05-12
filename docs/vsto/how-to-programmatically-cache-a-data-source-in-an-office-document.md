---
title: "Procedura: memorizzare nella cache a livello di codice un&#39;origine dati di un documento di Office"
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
  - "memorizzazione di dati nella cache [sviluppo per Office in Visual Studio], a livello di codice"
  - "dataset [sviluppo per Office in Visual Studio], memorizzazione nella cache"
  - "Applicazioni Office [sviluppo per Office in Visual Studio], dati"
  - "StartCaching (metodo)"
ms.assetid: 70b3fc06-7534-407e-898b-36f84e9a7516
caps.latest.revision: 43
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 43
---
# Procedura: memorizzare nella cache a livello di codice un&#39;origine dati di un documento di Office
  È possibile aggiungere un oggetto dati a livello di codice alla cache di dati in un documento chiamando il metodo `StartCaching` di un elemento host, come <xref:Microsoft.Office.Tools.Word.Document>, <xref:Microsoft.Office.Tools.Excel.Workbook> o <xref:Microsoft.Office.Tools.Excel.Worksheet>.  Rimuovere un oggetto dati dalla cache di dati chiamando il metodo `StopCaching` di un elemento host.  
  
 Il metodo `StartCaching` e il metodo `StopCaching` sono entrambi privati, ma vengono visualizzati in IntelliSense.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Quando si utilizza il metodo `StartCaching` per aggiungere un oggetto dati alla cache di dati, non è necessario dichiarare l'oggetto dati con l'attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute>.  Tuttavia, l'oggetto dati deve soddisfare alcuni requisiti per poter essere aggiunto alla cache di dati.  Per ulteriori informazioni, vedere [Memorizzazione di dati nella cache](../vsto/caching-data.md).  
  
### Per memorizzare un oggetto dati nella cache a livello di codice  
  
1.  Dichiarare l'oggetto dati come livello di classe, non all'interno di un metodo.  In questo esempio si presume che venga dichiarato un oggetto <xref:System.Data.DataSet> denominato `dataSet1` che si intende memorizzare nella cache a livello di codice.  
  
     [!code-csharp[Trin_VstcoreDataExcel#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#12)]
     [!code-vb[Trin_VstcoreDataExcel#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#12)]  
  
2.  Creare l'istanza dell'oggetto dati, quindi chiamare il metodo `StartCaching` dell'istanza di documento o foglio di lavoro e passare il nome dell'oggetto dati.  
  
     [!code-csharp[Trin_VstcoreDataExcel#13](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#13)]
     [!code-vb[Trin_VstcoreDataExcel#13](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#13)]  
  
### Per interrompere la memorizzazione di un oggetto dati nella cache  
  
1.  Chiamare il metodo `StopCaching` dell'istanza di documento o foglio di lavoro e passare il nome dell'oggetto dati.  In questo esempio si presume che sia disponibile un <xref:System.Data.DataSet> denominato `dataSet1` di cui si intende interrompere la memorizzazione nella cache.  
  
     [!code-csharp[Trin_VstcoreDataExcel#14](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#14)]
     [!code-vb[Trin_VstcoreDataExcel#14](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#14)]  
  
    > [!NOTE]  
    >  Non chiamare `StopCaching` gestore eventi per l'evento `Shutdown` di un documento o foglio di lavoro.  Nel momento in cui viene generato l'evento `Shutdown`, non è più possibile modificare la cache dei dati.  Per ulteriori informazioni sull'evento `Shutdown`, vedere [Eventi nei progetti di Office](../vsto/events-in-office-projects.md).  
  
## Vedere anche  
 [Memorizzazione di dati nella cache](../vsto/caching-data.md)   
 [Procedura: memorizzare dati nella cache per l'utilizzo offline o su un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Procedura: memorizzare dati nella cache di un documento protetto da password](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Accesso ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)  
  
  