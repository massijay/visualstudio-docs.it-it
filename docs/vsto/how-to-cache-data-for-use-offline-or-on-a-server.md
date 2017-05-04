---
title: "Procedura: memorizzare dati nella cache per l&#39;utilizzo offline o su un server | Microsoft Docs"
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
  - "memorizzazione di dati nella cache [sviluppo per Office in Visual Studio], utilizzo offline"
  - "memorizzazione di dati nella cache [sviluppo per Office in Visual Studio], utilizzo del server"
  - "dataset [sviluppo per Office in Visual Studio], memorizzazione nella cache"
  - "Applicazioni Office [sviluppo per Office in Visual Studio], dati"
  - "dati offline [sviluppo per Office in Visual Studio]"
ms.assetid: 6246b187-9413-4336-821d-2259b1adec5a
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Procedura: memorizzare dati nella cache per l&#39;utilizzo offline o su un server
  È possibile contrassegnare un elemento dati per la memorizzazione nella cache del documento e quindi per il successivo utilizzo offline.  In questo modo, si favorisce anche la modifica dei dati del documento mediante altro codice quando il documento è memorizzato su un server.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 L'elemento dati può essere contrassegnato per la memorizzazione nella cache quando è dichiarato nel codice oppure, se si utilizza un oggetto <xref:System.Data.DataSet>, quando si imposta una proprietà nella finestra **Proprietà**.  Se si memorizza nella cache un elemento dati che non è un oggetto <xref:System.Data.DataSet> o <xref:System.Data.DataTable>, assicurarsi che soddisfi i criteri necessari per la memorizzazione nella cache del documento.  Per ulteriori informazioni, vedere [Memorizzazione di dati nella cache](../vsto/caching-data.md).  
  
> [!NOTE]  
>  I nomi dei DataSet creati con Visual Basic che sono contrassegnati come **Cached** e **WithEvents** \(compresi i DataSet trascinati dalla finestra **Origini dati** o **Casella degli strumenti** la cui proprietà **CacheInDocument** è impostata su **True**\) sono preceduti da un carattere di sottolineatura nella cache.  Se ad esempio si crea un DataSet e lo si denomina Customers, il nome <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> sarà \_Customers nella cache.  Quando si utilizza <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> per accedere a questo elemento memorizzato nella cache, è necessario specificare \_Customers anziché Customers.  
  
### Per memorizzare dati nella cache del documento utilizzando codice  
  
1.  Dichiarare una proprietà o un campo pubblico per l'elemento dati come un membro di una classe dell'elemento host del progetto, ad esempio la classe `ThisDocumen` in un progetto Word o la classe `ThisWorkbook` in un progetto Excel.  
  
2.  Applicare l'attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> al membro per contrassegnare l'elemento dati da memorizzare nella cache di dati del documento.  Nell'esempio seguente, questo attributo viene applicato a una dichiarazione di campo per un oggetto <xref:System.Data.DataSet>.  
  
     [!code-csharp[Trin_VstcoreDataExcel#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/CS/Sheet1.cs#11)]
     [!code-vb[Trin_VstcoreDataExcel#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreDataExcel/VB/Sheet1.vb#11)]  
  
3.  Aggiungere il codice per creare un'istanza dell'elemento dati e, se possibile, per caricarla dal database.  
  
     L'elemento dati viene caricato solo quando viene creato per la prima volta; di conseguenza, la cache resta associata al documento e sarà necessario scrivere altro codice per aggiornarla.  
  
### Per memorizzare un dataset nel documento tramite la finestra Proprietà  
  
1.  Aggiungere il dataset al progetto utilizzando gli strumenti della finestra di progettazione di Visual Studio, ad esempio, aggiungendo un'origine dati al progetto mediante la finestra **Origini dati**.  
  
2.  Creare un'istanza del DataSet se non ne è già disponibile una e selezionare l'istanza nella finestra di progettazione.  
  
3.  Nella finestra **Proprietà**, impostare la proprietà **CacheInDocument** su **True**.  
  
     Per ulteriori informazioni, vedere [Proprietà nei progetti di Office](../vsto/properties-in-office-projects.md).  
  
4.  Nella finestra **Proprietà**, modificare la proprietà **Modifiers** impostandola su **Public** \(per impostazione predefinita è impostata su **Internal**\).  
  
## Vedere anche  
 [Memorizzazione di dati nella cache](../vsto/caching-data.md)   
 [Procedura: memorizzare nella cache a livello di codice un'origine dati di un documento di Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Procedura: memorizzare dati nella cache di un documento protetto da password](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Accesso ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Salvataggio di dati](../data-tools/saving-data.md)  
  
  