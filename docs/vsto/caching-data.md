---
title: "Memorizzazione di dati nella cache | Microsoft Docs"
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
  - "memorizzazione di dati nella cache [sviluppo per Office in Visual Studio]"
  - "memorizzazione di dati nella cache [sviluppo per Office in Visual Studio], informazioni sulla memorizzazione di dati nella cache"
ms.assetid: 6f34251e-7d31-4f2b-ac17-42fd2837c626
caps.latest.revision: 36
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# Memorizzazione di dati nella cache
  Gli oggetti dati possono essere memorizzati nella cache di una personalizzazione a livello di documento in modo da poter accedere ai dati anche in modalità offline o senza dover aprire Microsoft Office Word o Microsoft Office Excel.  Un oggetto, per poter essere memorizzato nella cache, deve disporre di un tipo di dati che soddisfa alcuni requisiti.  Molti tipi di dati comuni in .NET Framework soddisfano questi requisiti, compresi <xref:System.String>, <xref:System.Data.DataSet> e <xref:System.Data.DataTable>.  
  
 [!INCLUDE[appliesto_alldoc](../vsto/includes/appliesto-alldoc-md.md)]  
  
 Un oggetto può essere aggiunto alla cache di dati in due modi:  
  
-   Per aggiungere un oggetto alla cache di dati durante la compilazione della soluzione, applicare l'attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> alla dichiarazione dell'oggetto.  Per ulteriori informazioni, vedere [Procedura: memorizzare dati nella cache per l'utilizzo offline o su un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md).  
  
-   Per aggiungere a livello di codice un oggetto alla cache di dati in fase di esecuzione, utilizzare il metodo `StartCaching` di un elemento host, ad esempio le classi `ThisDocument` o `ThisWorkbook`.  Per ulteriori informazioni, vedere [Procedura: memorizzare nella cache a livello di codice un'origine dati di un documento di Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md).  
  
 Dopo aver aggiunto un oggetto alla cache di dati, è possibile accedere e modificare i dati memorizzati nella cache senza dover avviare Word o Excel.  Per ulteriori informazioni, vedere [Accesso ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## Requisiti per gli oggetti dati da memorizzare nella cache  
 Per memorizzare nella cache un oggetto dati nella soluzione, l'oggetto deve soddisfare alcuni requisiti:  
  
-   Essere un campo pubblico di lettura\/scrittura o una proprietà di un elemento host, ad esempio le classi `ThisDocument` o `ThisWorkbook`.  
  
-   Non deve essere un indicizzatore o un altro tipo di proprietà con parametri.  
  
 In aggiunta, l'oggetto dati deve essere serializzabile dalla classe <xref:System.Xml.Serialization.XmlSerializer>, il che indica che il tipo dell'oggetto deve avere le caratteristiche seguenti:  
  
-   Deve essere di tipo pubblico.  
  
-   Deve avere un costruttore pubblico senza parametri.  
  
-   Non deve eseguire codice che richieda privilegi di sicurezza aggiuntivi.  
  
-   Deve esporre solo proprietà di lettura\/scrittura pubbliche \(le altre proprietà verranno ignorate\).  
  
-   Non deve esporre matrici multidimensionali \(sono accettate le matrici annidate\).  
  
-   Non deve restituire interfacce da proprietà e campi.  
  
-   Non deve implementare <xref:System.Collections.IDictionary>, se si tratta di una raccolta.  
  
 Quando si memorizza nella cache un oggetto dati, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] serializza l'oggetto in una stringa XML archiviata in una *parte XML personalizzata* nel documento.  Per ulteriori informazioni, vedere [Cenni preliminari sulle web part XML personalizzate](../vsto/custom-xml-parts-overview.md).  
  
## Limiti di dimensione dei dati memorizzati nella cache  
 Esistono alcuni limiti alla quantità totale di dati che è possibile aggiungere alla cache in un documento e alla dimensione di qualsiasi oggetto singolo nella cache di dati.  Se questi limiti vengono superati, l'applicazione potrebbe chiudersi in modo imprevisto quando i dati vengono salvati nella cache di dati.  
  
 Per evitare questi limiti, attenersi a queste linee guida:  
  
-   Non aggiungere alcun oggetto di dimensioni superiori a 10 MB alla cache di dati.  
  
-   Non aggiungere più di 100 MB di dati totali alla cache di dati in un singolo documento.  
  
 Si tratta di valori approssimativi.  I limiti esatti dipendono da diversi fattori, tra cui la RAM disponibile e il numero di processi in esecuzione.  
  
## Controllo del comportamento degli oggetti memorizzati nella cache  
 Per ottenere un maggiore controllo sul comportamento di un oggetto memorizzato nella cache, è possibile implementare l'interfaccia <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType> nel tipo dell'oggetto memorizzato nella cache.  Questa interfaccia, ad esempio, può essere implementata quando si desidera controllare la modalità di notifica degli utenti al variare dell'oggetto.  Per esempi di codice in cui viene illustrato come implementare <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.ICachedType>, vedere la classe `ControlCollection` in Esempio di controlli dinamici di Excel e Esempio di controlli dinamici di Word in [Procedure dettagliate ed esempi di sviluppo di applicazioni per Microsoft Office](../vsto/office-development-samples-and-walkthroughs.md).  
  
## Salvataggio permanente delle modifiche apportate ai dati memorizzati nella cache dei documenti protetti da password  
 Se si memorizzano nella cache oggetti dati in un documento protetto con password, le modifiche ai dati memorizzati nella cache non vengono salvati.  È possibile salvare le modifiche ai dati memorizzati nella cache eseguendo l'override di due metodi.  Eseguire l'override di questi metodi per rimuovere temporaneamente la protezione durante il salvataggio del documento, quindi riapplicare la protezione al termine dell'operazione di salvataggio.  
  
 Per ulteriori informazioni, vedere [Procedura: memorizzare dati nella cache di un documento protetto da password](../vsto/how-to-cache-data-in-a-password-protected-document.md).  
  
## Esclusione della perdita di dati in caso di aggiunta di valori null alla cache di dati  
 Gli oggetti aggiunti alla cache di dati devono essere inizializzati su un valore non **null** prima che il documento venga salvato e chiuso.  Se qualsiasi oggetto memorizzato nella cache dispone di un valore **null** quando il documento viene salvato e chiuso, [!INCLUDE[vsto_runtime](../vsto/includes/vsto-runtime-md.md)] rimuoverà automaticamente tutti gli oggetti memorizzati dalla cache di dati.  
  
 Se si aggiunge un oggetto con un valore **null** alla cache di dati mediante l'attributo <xref:Microsoft.VisualStudio.Tools.Applications.Runtime.CachedAttribute> in fase di progettazione, è possibile utilizzare la classe <xref:Microsoft.VisualStudio.Tools.Applications.ServerDocument> per inizializzare gli oggetti dati contenuti nella cache prima che il documento venga aperto.  Tale operazione si rivela utile se si desidera inizializzare i dati memorizzati nella cache in un server senza avere a disposizione Word o Excel, prima che il documento venga aperto da un utente finale.  Per ulteriori informazioni, vedere [Accesso ai dati dei documenti sul server](../vsto/accessing-data-in-documents-on-the-server.md).  
  
## Vedere anche  
 [Procedura: memorizzare dati nella cache per l'utilizzo offline o su un server](../vsto/how-to-cache-data-for-use-offline-or-on-a-server.md)   
 [Procedura: memorizzare nella cache a livello di codice un'origine dati di un documento di Office](../vsto/how-to-programmatically-cache-a-data-source-in-an-office-document.md)   
 [Procedura: memorizzare dati nella cache di un documento protetto da password](../vsto/how-to-cache-data-in-a-password-protected-document.md)   
 [Procedura dettagliata: creazione di una relazione master-dettagli mediante un DataSet memorizzato nella cache](../vsto/walkthrough-creating-a-master-detail-relation-using-a-cached-dataset.md)  
  
  