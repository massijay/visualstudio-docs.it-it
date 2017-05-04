---
title: "Accesso ai dati dei documenti sul server | Microsoft Docs"
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
  - "dati [sviluppo per Office in Visual Studio], accesso su server"
  - "accesso ai dati [sviluppo per Office in Visual Studio]"
ms.assetid: 14a42e96-ed2f-48a1-a0c0-e19f9eba4956
caps.latest.revision: 32
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# Accesso ai dati dei documenti sul server
  È possibile programmare i dati in una personalizzazione a livello di documento senza dovere utilizzare il modello a oggetti di Microsoft Office Word o Microsoft Office Excel.  Ciò significa che è possibile accedere ai dati di un documento contenuto in un server in cui non è stato installato Word o Excel.  Ad esempio, un server può contenere codice, quale il codice di una pagina [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], in grado di personalizzare i dati di un documento e quindi inviare il documento personalizzato a un utente finale.  Quando l'utente finale apre il documento, il codice per l'associazione dati nell'assembly della soluzione consente di associare i dati personalizzati nel documento.  Ciò è possibile perché i dati del documento sono separatati dall'interfaccia utente.  Per ulteriori informazioni, vedere [Dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md).  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
## Memorizzazione dei dati nella cache per l'utilizzo su un server  
 Per memorizzare nella cache un oggetto dati di un documento, contrassegnarlo in fase di progettazione con l'attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> o utilizzare in fase di esecuzione il metodo `StartCaching` di un elemento host.  Quando si memorizza nella cache un oggetto dati in un documento, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializza l'oggetto in una stringa XML memorizzata nel documento.  Gli oggetti devono soddisfare determinati requisiti per essere idonei alla memorizzazione nella cache.  Per ulteriori informazioni, vedere [Memorizzazione di dati nella cache](../vsto/caching-data.md).  
  
 Il codice lato server può modificare qualsiasi oggetto dati contenuto nella cache di dati.  I controlli associati alle istanze di dati memorizzate nella cache sono sincronizzati con l'interfaccia utente, per cui le modifiche del lato server eseguite sui dati vengono mostrate automaticamente quando il documento viene aperto sul client.  
  
## Accesso ai dati contenuti nella cache  
 È possibile accedere ai dati presenti nella cache da applicazioni esterne a Office, ad esempio da un'applicazione console, un'applicazione Windows Form o una pagina Web.  L'applicazione che accede ai dati memorizzati nella cache deve essere completamente attendibile; un'applicazione Web parzialmente attendibile non potrà inserire, recuperare o modificare i dati memorizzati nella cache in un documento di Office.  
  
 La cache di dati è accessibile attraverso una gerarchia di raccolte esposte dalla proprietà <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> della classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument>:  
  
-   La proprietà <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> restituisce un oggetto <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> che contiene tutti i dati memorizzati nella cache di una personalizzazione a livello di documento.  
  
-   Ogni oggetto <xref:Microsoft.VisualStudio.Tools.Applications.CachedData> contiene uno o più oggetti <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem>.  L'oggetto <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contiene tutti gli oggetti dati memorizzati nella cache definiti all'interno di una singola classe.  
  
-   Ogni oggetto <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataHostItem> contiene uno o più oggetti <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem>.  Un oggetto <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> rappresenta un solo oggetto dati memorizzato nella cache.  
  
 Nell'esempio di codice seguente viene illustrato come accedere a una stringa memorizzata nella cache contenuta nella classe `Sheet1` di un progetto Cartella di lavoro di Excel.  Questo esempio fa parte di un esempio più esteso fornito per il metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>.  
  
 [!code-csharp[Trin_ServerDocument#12](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ServerDocument/CS/Form1.cs#12)]
 [!code-vb[Trin_ServerDocument#12](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ServerDocument/VB/Form1.vb#12)]  
  
## Modifica dei dati nella cache  
 Per modificare un oggetto dati memorizzato nella cache in genere si eseguono i passaggi seguenti:  
  
1.  Deserializzare la rappresentazione XML dell'oggetto memorizzato nella cache in una nuova istanza dell'oggetto.  Per accedere al codice XML è possibile utilizzare la proprietà <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A> dell'oggetto <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem> che rappresenta l'oggetto dati memorizzato nella cache.  
  
2.  Apportare le modifiche a questa copia.  
  
3.  Serializzare l'oggetto modificato nella cache di dati tramite una delle opzioni seguenti:  
  
    -   Se si desidera serializzare automaticamente le modifiche, utilizzare il metodo <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A>.  Questo metodo utilizza il formato **DiffGram** per serializzare gli oggetti <xref:System.Data.DataSet>, <xref:System.Data.DataTable> e gli oggetti DataSet tipizzati nella cache di dati.  Il formato **DiffGram** garantisce che le modifiche apportate alla cache di dati in un documento offline vengano inviate al server correttamente.  
  
    -   Se si desidera eseguire la serializzazione personalizzata per le modifiche ai dati memorizzati, è possibile scrivere direttamente nella proprietà <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.Xml%2A>.  Specificare il formato **DiffGram** se si utilizza un oggetto <xref:System.Data.Common.DataAdapter> per aggiornare un database con modifiche apportate ai dati in un oggetto <xref:System.Data.DataSet>, <xref:System.Data.DataTable> o in un dataset tipizzato.  In caso contrario, il database verrà aggiornato dall'oggetto <xref:System.Data.Common.DataAdapter> tramite l'aggiunta di nuove righe anziché la modifica delle righe esistenti.  
  
### Modifica dei dati senza deserializzare il valore corrente  
 In alcuni casi è necessario modificare il valore dell'oggetto memorizzato nella cache senza prima deserializzare il valore corrente.  Ad esempio, questo approccio è utile quando si modifica il valore di un oggetto che presenta un tipo semplice, quale una stringa o un numero intero, o quando si inizializza un oggetto <xref:System.Data.DataSet> memorizzato nella cache e appartenente a un documento contenuto in un server.  In questi casi è possibile utilizzare il metodo <xref:Microsoft.VisualStudio.Tools.Applications.CachedDataItem.SerializeDataInstance%2A> senza prima deserializzare il valore corrente dell'oggetto memorizzato nella cache.  
  
 Nell'esempio di codice seguente viene illustrato come modificare il valore di una stringa memorizzata nella cache contenuta nella classe `Sheet1` di un progetto Cartella di lavoro di Excel.  Questo esempio fa parte di un esempio più esteso fornito per il metodo <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.Save%2A>.  
  
 [!code-csharp[Trin_ServerDocument#11](../snippets/csharp/VS_Snippets_OfficeSP/Trin_ServerDocument/CS/Form1.cs#11)]
 [!code-vb[Trin_ServerDocument#11](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_ServerDocument/VB/Form1.vb#11)]  
  
### Modifica di valori null contenuti nella cache di dati  
 La cache di dati non memorizza oggetti che presentano il valore **null** quando il documento viene salvato e chiuso.  Questa limitazione comporta diverse conseguenze quando si modificano i dati memorizzati nella cache:  
  
-   Se uno degli oggetti contenuti nella cache di dati viene impostato sul valore **null**, all'apertura del documento tutti gli oggetti nella cache di dati vengono impostati automaticamente su **null**. Inoltre, l'intera cache di dati viene cancellata quando il documento viene salvato e chiuso.  In altre parole, tutti gli oggetti memorizzati nella cache vengono rimossi dalla cache di dati e la raccolta <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument.CachedData%2A> è vuota.  
  
-   Se si compila una soluzione che presenta oggetti **null** nella cache di dati e si desidera inizializzare questi oggetti tramite la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> prima che il documento venga aperto per la prima volta, è necessario assicurarsi di inizializzare tutti gli oggetti contenuti nella cache di dati.  Se invece si inizializzano soltanto alcuni di essi, all'apertura del documento tutti gli oggetti vengono impostati su **null** e l'intera cache di dati viene cancellata quando il documento viene salvato e chiuso.  
  
## Accesso ai DataSet tipizzati nella cache  
 Se si desidera accedere ai dati in un dataset tipizzato sia da una soluzione Office sia da un'applicazione esterna ad Office, , ad esempio un'applicazione Windows Form o un progetto [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)], il dataset tipizzato deve essere definito in un assembly distinto a cui si fa riferimento in entrambi i progetti.  Se il DataSet tipizzato viene aggiunto a ogni progetto utilizzando la **Configurazione guidata origine dati** o **Progettazione DataSet**, i DataSet tipizzati dei due progetti verranno considerati da .NET Framework come due tipi diversi.  Per ulteriori informazioni sulla creazione di dataset tipizzati, vedere [Procedura: creare un dataset tipizzato](../Topic/Creating%20and%20configuring%20datasets%20in%20Visual%20Studio.md).  
  
## Vedere anche  
 [Accessing Data in Documents on the Server](../vsto/accessing-data-in-documents-on-the-server.md)   
 [Dati memorizzati nella cache nelle personalizzazioni a livello di documento](../vsto/cached-data-in-document-level-customizations.md)  
  
  