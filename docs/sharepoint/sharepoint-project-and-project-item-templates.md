---
title: "Modelli di progetto e di elementi di progetto SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/22/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SPE.FirstWizardPage"
  - "VS.SharePointTools.SPE.ListInstance"
  - "VS.SharePointTools.SPE.ListDefinition"
  - "VS.SharePointTools.SPE.ListDefFromContentType"
  - "VS.SharePointTools.SPE.ContentType"
  - "SPE.Wizard"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sviluppo per SharePoint in Visual Studio, modelli di progetto e di elementi di progetto"
  - "sviluppo per SharePoint in Visual Studio, modelli"
ms.assetid: 54a7576f-d3f9-475d-8ed7-b675ad21cb53
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Modelli di progetto e di elementi di progetto SharePoint
  Le sezioni seguenti descrivono il progetto SharePoint disponibili e i modelli e le modalità di utilizzo dell'elemento di progetto.  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
##  <a name="project_items_templates_overview"></a> Cenni preliminari sui modelli di elemento di progetto e di progetto  
 Quando si crea un nuovo progetto di SharePoint in Visual Studio, un progetto SharePoint viene aggiunto alla soluzione insieme a tutti gli elementi di progetto richiesti da questo tipo di progetto.  Ad esempio, se si crea un progetto Web Part di Silverlight, Visual Studio crea una soluzione che contiene un elemento di progetto Web Part visiva e un elemento di progetto di applicazione Silverlight insieme a tutti i file necessari in base agli elementi di progetto.  Modelli di progetto consentono di aggiungere elementi di progetto per un progetto SharePoint esistente, ad esempio l'aggiunta di un ricevitore di eventi, una colonna del sito o un elenco.  
  
 Per informazioni sui principi fondamentali di SharePoint, vedere  [blocchi predefiniti di SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=179404).  Gli utenti avanzati possono creare progetti personalizzati e modelli di progetto.  Per ulteriori informazioni, vedere  [Extending the SharePoint Project System](../sharepoint/extending-the-sharepoint-project-system.md).  
  
##  <a name="project_templates"></a> Modelli di progetto  
 Di seguito è riportato un elenco di modelli di progetto SharePoint.  Per visualizzare i modelli di progetto SharePoint in Visual Studio, nel  **Nuovo progetto** finestra di dialogo espandere il  **SharePoint** nodo sotto  **Visual C\#** o  **di Visual Basic**e quindi scegliere  **2010**.  
  
### Progetto di SharePoint 2010  
 Il contenuto di un  *SharePoint 2010 progetto* sono inclusi in ciascun modello di progetto SharePoint.  Contiene un progetto di SharePoint 2010:  
  
-   Un file di progetto.  
  
-   Una pagina delle proprietà del progetto.  
  
-   A  **riferimenti** cartella elenco di tutti i riferimenti all'assembly nel progetto.  
  
-   A  **caratteristiche** cartella che contiene un file di configurazione con estensione feature, utilizzato per distribuire le funzionalità di SharePoint server.  
  
-   A  **pacchetto** cartella che contiene un file di package, utilizzato per distribuire la soluzione in SharePoint.  
  
-   Un file snk \(chiave con nome sicuro\) che viene utilizzato per firmare l'assembly con un nome sicuro, per una protezione avanzata.  
  
### Web Part di SharePoint 2010 Silverlight  
 *Web Part di SharePoint 2010 Silverlight* progetti consentono di creare web part per SharePoint che consentono di visualizzare le applicazioni Silverlight.  Quando si crea questo progetto, è possibile specificare se aggiungere una nuova applicazione Silverlight o fare riferimento a uno esistente.  Per ulteriori informazioni, vedere  [Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)e   [Procedura dettagliata: creazione di una Web part Silverlight che visualizza il servizio OData per SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### Visual Web Part di SharePoint 2010  
 A  *Visual Web Part di SharePoint 2010* progetto include un file di definizione Elements. XML, un  **Web Part** voce e un  **Controllo utente** elemento.  È possibile progettare l'aspetto della parte di visual web trascinando o copiando i controlli dalla casella degli strumenti di Visual Studio per la superficie del controllo utente.  Per ulteriori informazioni, vedere  [Procedura: creare una web part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)e   [blocco predefinito: Web part](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### Importare il pacchetto della soluzione SharePoint 2010  
 *Importare il pacchetto della soluzione SharePoint 2010* progetti consentono di importare tutto o parte di un sito di SharePoint 2010 esistente, esportato in un file di soluzione \(con estensione wsp\) di SharePoint in Visual Studio.  Una volta importato in Visual Studio, è possibile personalizzarne gli elementi e ridistribuirli.  Per ulteriori informazioni, vedere  [Importazione di elementi da un sito di SharePoint esistente](../sharepoint/importing-items-from-an-existing-sharepoint-site.md).  
  
### Importare riutilizzabili flusso di lavoro SharePoint 2010  
 *Importare riutilizzabili flusso di lavoro SharePoint 2010* progetti consentono di importare un flusso di lavoro riutilizzabile e dichiarativo creato in SharePoint Designer 2010 in Visual Studio.  Il flusso di lavoro viene esportato dal sito di SharePoint come file con estensione wsp.  Una volta importato in Visual Studio, personalizzarlo, aggiungervi codice e quindi distribuito su un sito di SharePoint.  Per ulteriori informazioni, vedere  [Procedura dettagliata: Importare un flusso di lavoro riutilizzabile di SharePoint Designer in Visual Studio](../sharepoint/walkthrough-import-a-sharepoint-designer-reusable-workflow-into-visual-studio.md).  
  
##  <a name="project_item_templates"></a> Modelli di progetto  
 Di seguito è riportato un elenco di modelli di progetto SharePoint.  Modelli di progetto aggiungere file alla soluzione di SharePoint per supportare la funzionalità di SharePoint quali colonne del sito, gli elenchi e tipi di contenuto.  Ad esempio, una colonna del sito alla soluzione quando si aggiunge un progetto di colonna del sito che contiene un file di definizione Elements. Xml.  Aggiunta di una web part visiva consente di aggiungere un progetto di visual web part alla soluzione che contiene un file Elements. XML, un elemento del controllo utente e un elemento web part visiva.  
  
 Per visualizzare i modelli di progetto SharePoint, in  **Esplora**, aprire il menu di scelta rapida per un progetto SharePoint e quindi scegliere  **Aggiungi**,  **Nuovo elemento**.  Espandere il  **SharePoint** nodo sotto  **Visual C\#** o  **di Visual Basic**, quindi scegliere  **2010**.  
  
### Pagina dell'applicazione \(solo soluzione della Farm\)  
 Un  **Pagina dell'applicazione \(solo soluzione Farm\)** elemento consente di progettare un  [!INCLUDE[vstecasp](../sharepoint/includes/vstecasp-md.md)]pagina web per un sito di SharePoint.  Le pagine delle applicazioni può essere utilizzati in soluzioni farm.  È possibile aggiungere questo elemento di progetto solo per soluzioni farm.  Per ulteriori informazioni, vedere  [Procedura: creare una pagina applicazione](../sharepoint/how-to-create-an-application-page.md)e   [Layouts applicazione tipo pagina](http://go.microsoft.com/fwlink/?LinkId=179434).  
  
### Modello \(solo soluzione della Farm\)  
 A  **Modello \(solo soluzione Farm\)** elemento consente di integrare dati business in SharePoint.  Dati di business possono provenire da applicazioni server back\-end, ad esempio  [!INCLUDE[ssNoVersion](../sharepoint/includes/ssnoversion-md.md)], Siebel e Service Advertising Protocol \(SAP\).  Modelli di connettività dei dati possono essere utilizzati in soluzioni farm.  È possibile aggiungere questo elemento di progetto solo per soluzioni farm.  Per ulteriori informazioni, vedere  [Procedura: creare un modello di integrazione applicativa dei dati](../sharepoint/how-to-create-a-bdc-model.md),   [Procedura: utilizzare un file di risorse per specificare nomi localizzati, proprietà e autorizzazioni](../sharepoint/how-to-use-a-resource-file-to-specify-localized-names-properties-and-permissions.md), e   [Novità: Servizi di integrazione applicativa](http://go.microsoft.com/fwlink/?LinkId=179411).  
  
### Tipo di contenuto  
 *Tipo di contenuto* elementi consentono di creare tipi di contenuto personalizzati basati su un tipo di contenuto esistente \(base\), ad esempio un documento, un annuncio o un'attività.  Un tipo di contenuto personalizzato fornisce gli stessi attributi e campi come tipo di contenuto di base insieme a eventuali colonne \(campi\) del sito che definire.  Ad esempio, è possibile creare un tipo di contenuto contatto personalizzato basato sul tipo di base contatto contenuto è disponibile in SharePoint.  È possibile personalizzare il tipo di contenuto modificando le colonne del sito esistente o aggiunta di ulteriori colonne del sito a quelli già inclusi nel tipo di contenuto di base.  
  
> [!NOTE]  
>  A causa di una limitazione di SharePoint, è possibile creare un tipo di contenuto soluzione farm basato sul tipo di contenuto di una soluzione creata mediante sandbox.  
  
 Per ulteriori informazioni, vedere  [Procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)e   [blocco predefinito: Tipo di contenuto](http://go.microsoft.com/fwlink/?LinkId=179413).  
  
### Elemento vuoto  
 *Gli elementi vuoti* più spesso vengono utilizzati per definire gli elementi di progetto SharePoint che non dispongono di un progetto o un modello di elemento di progetto in Visual Studio.  Quando si aggiunge un elemento vuoto al progetto, un nodo denominato EmptyElement \[x\]\(dove \[x\] è un numero univoco\) viene creato.  EmptyElement \[x\] contiene un unico file denominato Elements. Xml.  Usa  [!INCLUDE[TLA2#tla_xml](../sharepoint/includes/tla2sharptla-xml-md.md)]le istruzioni per definire gli elementi desiderati in Elements. Xml.  
  
### Ricevitore di eventi  
 *Ricevitori di eventi* gestione degli eventi per gli articoli nel sito di SharePoint, ad esempio quando un elemento viene aggiunto a un elenco, quando viene eliminato un elemento web o all'avvio di un flusso di lavoro.  Il modello di elemento del progetto di ricevitore di eventi consente di gestire  
  
-   Elenco eventi  
  
-   Eventi elementi elenco  
  
-   Elenco degli eventi di posta elettronica  
  
-   Eventi Web  
  
-   Eventi del flusso di lavoro elenco  
  
 L'elemento di progetto ricevitore di eventi crea un  **Ricevitore di eventi** cartella con un singolo file di classe che contiene i gestori eventi per tutti gli eventi specificati quando si crea il progetto nel  **Personalizzazione guidata SharePoint**.  Il  event receiverclasse può gestire eventi che si verificano nel sito di SharePoint quando elementi quali file, campi, elementi, elenchi, allegati, web part e flussi di lavoro vengono aggiunti, aggiornati, eliminati o rimossi.  Per ulteriori informazioni, vedere  [Procedura: creare un ricevitore di eventi](../sharepoint/how-to-create-an-event-receiver.md)e   [blocco predefinito: La gestione degli eventi](http://go.microsoft.com/fwlink/?LinkId=179416).  
  
### Elenco  
 Un elenco è un'istanza di una riutilizzabili SharePoint elenco definizione di base, ad esempio un calendario o un elenco di attività.  Dopo aver aggiunto un elenco alla soluzione, la finestra di progettazione di elenco consente di aggiungere colonne del sito all'elenco e creare colonne di elenco personalizzato.  Ciò include le colonne del sito da tipi di contenuto.  È possibile specificare il  *visualizzazione* per l'elenco, che determina le colonne che verranno visualizzate nell'elenco.  Per ulteriori informazioni, vedere  [Procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)e   [blocco predefinito: Elenchi e raccolte documenti](http://go.microsoft.com/fwlink/?LinkId=179421).  
  
### Modulo  
 *Moduli* \(da non confondere con  [!INCLUDE[vbprvb](../sharepoint/includes/vbprvb-md.md)]moduli\) contiene file che si desidera distribuire in SharePoint server, ad esempio immagini o note.  L'elemento di progetto di modulo contiene un  **modulo** nodo.  Il nodo del modulo contiene due modelli di progetto: un file di definizione XML, che funge da un manifesto per il modulo, e un file Sample exe, un file segnaposto.  Per ulteriori informazioni, vedere  [Utilizzo di moduli per includere file nella soluzione](../sharepoint/using-modules-to-include-files-in-the-solution.md)e   [moduli](http://go.microsoft.com/fwlink/?LinkId=179425).  
  
### Flusso di lavoro sequenza \(solo soluzione della Farm\)  
 A  *flusso di lavoro sequenza* è una serie di passaggi di logica business, eseguiti in sequenza, fino al completamento dell'ultimo passaggio.  Flussi di lavoro sequenziali vengono utilizzati per gestire i processi che implicano elementi di SharePoint come elenchi e documenti.  È possibile creare flussi di lavoro a livello di sito \(globale\) o flussi di lavoro a livello di elenco \(locale\), ed è possibile scegliere se un flusso di lavoro viene avviato automaticamente o manualmente.  Questo elemento di progetto può essere utilizzato in soluzioni farm.  È possibile aggiungere questo elemento di progetto solo per soluzioni farm.  Per ulteriori informazioni, vedere  [Creazione di soluzioni flusso di lavoro SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md),   [flussi di lavoro in SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), e  [Novità: Miglioramenti del flusso di lavoro](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### Silverlight Web Part  
 *Web part Silverlight* gli elementi di progetto consentono di creare web part per SharePoint che consentono di visualizzare le applicazioni Silverlight.  Quando si aggiunge questo elemento di progetto alla soluzione, è possibile scegliere se aggiungere una nuova applicazione Silverlight o fare riferimento a uno esistente in un secondo momento.  Per ulteriori informazioni, vedere  [Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)e   [Procedura dettagliata: creazione di una Web part Silverlight che visualizza il servizio OData per SharePoint](../sharepoint/walkthrough-creating-a-silverlight-web-part-that-displays-odata-for-sharepoint.md).  
  
### Colonna del sito  
 A  *colonna del sito*, noto anche come un  *campo*, è uno degli elementi di base è possibile aggiungere a un progetto SharePoint.  Una colonna del sito rappresenta un tipo di dati, ad esempio un numero di telefono, un commento di testo o il nome della città di un contatto in un elenco di contatti.  Per ulteriori informazioni, vedere  [Creazione di colonne del sito, tipi di contenuto ed elenchi per SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)e   [colonne](http://go.microsoft.com/fwlink/?LinkId=226840).  
  
### Definizione del sito \(solo soluzione della Farm\)  
 *Definizione del sito*  gli elementi di progetto contengono una cartella di definizione del sito che include i seguenti file:  
  
-   Una pagina aspx di default, utilizzata come pagina web predefinita per il sito.  
  
-   Un file onet XML che definisce i componenti del sito.  
  
-   Un file webtemp xml che specifica le configurazioni di definizioni di sito vengono visualizzati nel  **Selezione modello** sezione della  **Nuovo sito di SharePoint** pagina.  
  
 Dopo aver aggiunto una definizione di sito, è possibile aggiungere codice e file per fornire funzionalità.  Questo elemento di progetto può essere utilizzato in soluzioni farm.  È possibile aggiungere questo elemento di progetto solo per soluzioni farm.  Per ulteriori informazioni, vedere  [Creazione di definizioni di sito per SharePoint](../sharepoint/creating-site-definitions-for-sharepoint.md)e   [configurazioni e definizioni di sito](http://go.microsoft.com/fwlink/?LinkId=260554).  
  
### Flusso di lavoro macchina a stati \(solo soluzione della Farm\)  
 A  *il flusso di lavoro di stato macchina* è un insieme di stati di logica di business, transizioni e azioni.  I passaggi di lavoro non vengono eseguiti in sequenza; al contrario, ma vengono attivati da azioni e stati.  Come un flusso di lavoro sequenza, flussi di lavoro di stato macchina sono associati gli elementi di SharePoint come elenchi e documenti.  Ancora una volta, è possibile creare flussi di lavoro a livello di sito \(globale\) o a livello di elenco \(locale\).  È anche possibile scegliere se un flusso di lavoro viene avviato automaticamente o manualmente.  Questo elemento di progetto può essere utilizzato in soluzioni farm.  È possibile aggiungere questo elemento di progetto solo per soluzioni farm.  Per ulteriori informazioni, vedere  [Creazione di soluzioni flusso di lavoro SharePoint](../sharepoint/creating-sharepoint-workflow-solutions.md),   [flussi di lavoro in SharePoint Server 2010](http://go.microsoft.com/fwlink/?LinkId=260555), e  [Novità: Miglioramenti del flusso di lavoro](http://go.microsoft.com/fwlink/?LinkId=179418).  
  
### Controllo utente \(solo soluzione della Farm\)  
 A  *controllo utente* è un controllo personalizzato riutilizzabile a cui è possibile aggiungere altri controlli ASP.NET e controlli di SharePoint.  Il controllo utente può essere aggiunto alle pagine di applicazioni e web part eseguite in SharePoint.  Questo elemento di progetto può essere utilizzato in soluzioni farm.  È possibile aggiungere questo elemento di progetto solo per soluzioni farm.  Per ulteriori informazioni, vedere  [Creazione di controlli riutilizzabili per Web part o le pagine dell'applicazione](http://go.microsoft.com/fwlink/?LinkId=226841).  
  
### Web Part visiva  
 A  *web part visiva* elemento di progetto include un file di definizione Elements. XML, un  **Web Part** voce e un  **Controllo utente** elemento.  È possibile progettare l'aspetto della parte di visual web trascinando o copiando i controlli dalla casella degli strumenti di Visual Studio per la superficie del controllo utente.  Per ulteriori informazioni, vedere  [Procedura: creare una web part di SharePoint tramite una finestra di progettazione](../sharepoint/how-to-create-a-sharepoint-web-part-by-using-a-designer.md)e   [blocco predefinito: Web part](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
### Web Part  
 A  *parte web* è un controllo lato server che viene eseguito all'interno di un tipo speciale di pagina chiamata una pagina Web Part.  Sono i blocchi predefiniti di pagine visualizzate in un sito di SharePoint.  L'elemento di web part fornisce file che consentono di progettare una web part per un sito di SharePoint.  Per ulteriori informazioni, vedere  [Procedura: creare una web part di SharePoint](../sharepoint/how-to-create-a-sharepoint-web-part.md)e   [blocco predefinito: Web part](http://go.microsoft.com/fwlink/?LinkId=179438).  
  
## Vedere anche  
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Prodotti e tecnologie SharePoint](http://go.microsoft.com/fwlink/?LinkId=178818)  
  
  