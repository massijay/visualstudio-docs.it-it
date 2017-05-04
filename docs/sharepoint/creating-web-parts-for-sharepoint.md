---
title: "Creazione di web part per SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Microsoft.SharePoint.WebControls.DateTimeControl"
  - "Microsoft.SharePoint.WebControls.CssLink"
  - "Microsoft.SharePoint.WebControls.RssLink"
  - "Microsoft.SharePoint.WebControls.Theme"
  - "Microsoft.SharePoint.WebControls.AspMenu"
  - "Microsoft.SharePoint.WebControls.ListProperty"
  - "Microsoft.SharePoint.WebControls.ProjectProperty"
  - "Microsoft.SharePoint.WebControls.FormsDigest"
  - "Microsoft.SharePoint.WebControls.ScriptLink"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sviluppo per SharePoint in Visual Studio, Web part"
  - "Web part [sviluppo per SharePoint in Visual Studio], progettazione"
ms.assetid: a6349e85-45cf-4766-b856-e25c9f1ffd34
caps.latest.revision: 42
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 41
---
# Creazione di web part per SharePoint
  Utilizzando Web part, è possibile modificare il contenuto, l'aspetto e il comportamento delle pagine di un sito di SharePoint tramite un browser.  Le web part sono controlli sul lato server eseguiti in un tipo speciale di pagina detta pagina web part, ovvero blocchi predefiniti di pagine che vengono visualizzati in un sito SharePoint.  Vedere [Elemento di documento: Web part](http://go.microsoft.com/fwlink/?LinkID=182097).  
  
 È possibile creare web part ed eseguirne il debug in un sito SharePoint utilizzando i modelli di Visual Studio.  
  
## Creazione di una web part in Visual Studio  
 Per creare una Web part, aggiungere un elemento **Web part** a un progetto SharePoint qualsiasi.  È possibile utilizzare un elemento **Web part** in una soluzione creata mediante sandbox o una soluzione farm.  
  
 Se si desidera progettare visivamente una Web part tramite una finestra di progettazione, creare un progetto **Web part visiva** o aggiungere un elemento **Web part visiva** a un qualsiasi progetto SharePoint.  È possibile utilizzare un elemento **Web part visiva** solo in una soluzione farm.  
  
### Elemento web part  
 Un elemento **Web part** fornisce i file che è possibile utilizzare per progettare una Web part per un sito di SharePoint.  Quando si aggiunge un elemento **web part**, in Visual Studio viene creata una cartella nel progetto, quindi vengono aggiunti alcuni file alla cartella.  Nella tabella riportata di seguito viene descritto ogni file.  
  
|File|Descrizione|  
|----------|-----------------|  
|Elements.xml|Contiene informazioni utilizzate dal file di definizione della funzionalità nel progetto per distribuire la Web part.|  
|File con estensione webpart|Vengono fornite informazioni richieste da SharePoint per visualizzare la web part in una raccolta web part.|  
|File di codice|Contiene metodi che aggiungono controlli alla Web part e generano contenuto personalizzato all'interno della Web part.|  
  
 Per ulteriori informazioni, vedere [Procedura: creare una web part di SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md).  
  
### Elemento web part visiva  
 Una Web part visiva è una Web part creata tramite la finestra di progettazione di Visual Web Developer in Visual Studio.  Vedere [Visual Studio Web Development Content Map](http://msdn.microsoft.com/it-it/9c31f93b-c8fb-4599-9b14-6194ec8c7539).  
  
 Una web part visiva funziona come qualsiasi altra web part.  Per aggiungere controlli, come pulsanti e caselle di testo, a una Web part, è necessario aggiungere il codice a un file XML.  Tuttavia, i controlli vengono aggiunti a una web part trascinandoli o copiandoli nella web part dalla **Casella degli strumenti**di Visual Studio.  La finestra di progettazione genera quindi il codice richiesto nel file XML.  Vedere [Procedura: creare una web part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md).  
  
## Controlli di SharePoint  
 Visual Studio fornisce alcuni controlli per creare pagine di SharePoint, ad esempio le pagine di applicazione.  Questi controlli sono disponibili nella **Casella degli strumenti** sotto **Controlli di SharePoint**.  La funzionalità per questi controlli deriva dallo spazio dei nomi [Microsoft.SharePoint.WebControls](http://go.microsoft.com/fwlink/?LinkId=235315), che contiene i controlli server ASP.NET utilizzati nel sito di SharePoint e nelle pagine di elenco.  
  
|Nome del controllo|Descrizione|  
|------------------------|-----------------|  
|[AspMenu](http://go.microsoft.com/fwlink/?LinkId=235307)|Inserisce un menu ASP.  Per ulteriori informazioni, vedere [Panoramica controllo Menu](http://go.microsoft.com/fwlink/?LinkId=235316).|  
|[CssLink](http://go.microsoft.com/fwlink/?LinkId=235308)|Inserisce un elemento **LINK** nella pagina con estensione aspx e applica uno o più fogli di stile esterni definiti da **CssRegistration**.|  
|[DateTimeControl](http://go.microsoft.com/fwlink/?LinkId=235306)|Inserisce un controllo DateTime nella pagina con estensione aspx.|  
|[FormDigest](http://go.microsoft.com/fwlink/?LinkId=235309)|Inserisce una convalida di sicurezza nella pagina con estensione aspx.|  
|[ListProperty](http://go.microsoft.com/fwlink/?LinkId=235310)|Restituisce una proprietà di un elenco specificato.|  
|[ProjectProperty](http://go.microsoft.com/fwlink/?LinkId=235311)|Restituisce una proprietà globale del sito Web corrente.|  
|[Classe RssLink](http://go.microsoft.com/fwlink/?LinkId=235312)|Inserisce un collegamento a un feed RSS nella pagina con estensione aspx.|  
|[Classe ScriptLink](http://go.microsoft.com/fwlink/?LinkId=235313)|Fornisce proprietà e metodi per registrare le risorse, ad esempio script, in una pagina affinché possano essere richieste durante il rendering della pagina.|  
|[Tema](http://go.microsoft.com/fwlink/?LinkId=235314)|Applica un tema alla pagina .aspx.|  
  
## Debug di una web part  
 È possibile eseguire il debug di un progetto SharePoint contenente una web part procedendo come per qualsiasi altro progetto di Visual Studio.  Quando si avvia il debugger di Visual Studio, viene aperto il sito di SharePoint.  
  
 Per iniziare a eseguire il debug del codice, aggiungere la web part a una pagina web part in SharePoint.  
  
 Per ulteriori informazioni sul debug di progetti SharePoint, vedere [Risoluzione dei problemi relativi alle soluzioni SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
## Limitazioni della web part visiva  
 A partire da Visual Studio, è possibile aggiungere Web part visive alle soluzioni di SharePoint con sandbox e alle soluzioni farm.  Tuttavia, le web part visive hanno le seguenti limitazioni:  
  
-   Le Web part visive non supportano i parametri sostituibili.  Per ulteriori informazioni, vedere [Parametri sostituibili](../sharepoint/replaceable-parameters.md).  
  
-   I controlli utente o le web part visive non possono essere trascinati e rilasciati o copiati su Web part visive.  Questa operazione causa un errore di compilazione.  
  
-   Le Web part visive non supportano direttamente i token del server SharePoint come $SPUrl.  Per ulteriori informazioni, vedere "Restrizioni dei token nelle web part visive create mediante sandbox" in [Risoluzione dei problemi relativi alle soluzioni SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
-   Le Web part visive in una soluzione creata mediante sandbox ricevono occasionalmente l'errore "La richiesta di esecuzione di codice in modalità sandbox è stata rifiutata perché il relativo servizio host era troppo occupato per gestirla". Per ulteriori informazioni su questo errore, vedere il post nel [Blog del team di sviluppo di SharePoint](http://go.microsoft.com/fwlink/?LinkId=225932).  
  
-   Il debug JavaScript sul lato server non è supportato in Visual Studio, ma il debug JavaScript su lato client è supportato.  
  
     Sebbene sia possibile aggiungere JavaScript inline a un file di markup lato server, il debug non è supportato per i punti di interruzione aggiunti a tale markup.  Per eseguire il debug di JavaScript, fare riferimento a un file JavaScript esterno nel file di markup e impostare i punti di interruzione nel file JavaScript.  
  
-   Il debug del codice [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] inline deve essere eseguito nel file di codice generato anziché nel file di markup.  
  
-   Le web part visive non supportano l'utilizzo della direttiva `<@ Assembly Src=`.  
  
-   I controlli Web di SharePoint e alcuni controlli [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] non sono supportati nell'ambiente con sandbox di SharePoint.  Se i controlli non supportati vengono utilizzati in una web part visiva in una soluzione creata mediante sandbox, viene visualizzato l'errore "Il tipo o il nome dello spazio nome 'Theme' non esiste nello spazio nome 'Microsoft.SharePoint.WebControls'".  
  
 Per ulteriori informazioni sulle soluzioni create mediante sandbox, vedere [Differenze tra soluzioni create mediante sandbox e soluzioni farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md).  
  
## Creazione di web part basate su SharePoint nello stile di versioni precedenti  
 È possibile utilizzare i modelli disponibili in Visual Studio per creare web part [!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] personalizzate per SharePoint.  Le web part[!INCLUDE[vstecasplong](../sharepoint/includes/vstecasplong-md.md)] vengono compilate sull'infrastruttura di web part [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)] e corrispondono al tipo consigliato per i nuovi progetti.  
  
 In pochi casi potrebbe essere necessario creare una Web part utilizzando la Web part basata su SharePoint nello stile di versioni precedenti.  È possibile utilizzare Visual Studio per creare questi tipi di web part, ma in Visual Studio non sono disponibili modelli appositamente progettati per semplificarne la creazione.  
  
 Per ulteriori informazioni sui casi in cui è possibile che si desideri creare una web part basata su SharePoint, vedere la pagina sull'[infrastruttura delle web part in Windows SharePoint Services](http://go.microsoft.com/fwlink/?LinkId=169290).  Per ulteriori informazioni sulla creazione di una web part utilizzando la web part basata su SharePoint nello stile di versioni precedenti, vedere la [procedura dettagliata di creazione di una web part di SharePoint di base](http://go.microsoft.com/fwlink/?LinkId=169288).  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Procedura: creare una web part di SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)|Mostra come creare web part per pagine di SharePoint.|  
|[Procedura: creare una web part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)|Mostra come creare web part per SharePoint tramite un'area di progettazione visiva.|  
|[Procedura: creare un controllo utente per una web part o una pagina applicazione di SharePoint](../sharepoint/how-to-create-a-user-control-for-a-sharepoint-application-page-or-web-part.md)|Mostra come creare controlli riutilizzabili e personalizzati che possono essere utilizzati nelle pagine applicazione e nelle web part eseguite in SharePoint.|  
|[Procedura dettagliata: creazione di una web part per SharePoint](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint.md)|Viene descritto come progettare una web part per SharePoint.|  
|[Procedura dettagliata: creazione di una web part per SharePoint tramite una finestra di progettazione](../sharepoint/walkthrough-creating-a-web-part-for-sharepoint-by-using-a-designer.md)|Viene descritto come progettare una web part per SharePoint trascinando i controlli in un'area di progettazione visiva.|  
|[Procedura dettagliata: creazione di una Web part Silverlight che visualizza il servizio OData per SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md)|Viene descritto come progettare una web part per SharePoint che ospita un'applicazione Silverlight e visualizza i dati dagli elenchi di SharePoint.|  
|[Utilizzo di Visual Web Developer](http://msdn.microsoft.com/it-it/9c31f93b-c8fb-4599-9b14-6194ec8c7539)|Viene descritto come utilizzare la finestra di progettazione visualizzata quando si apre una pagina Web nel progetto.|  
  
  