---
title: "Progettazione di un modello di integrazione applicativa dei dati | Microsoft Docs"
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
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], progettazione di un modello"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], progettazione di un modello"
ms.assetid: 19cad8cf-8a82-4000-84cf-1e5aff54e5af
caps.latest.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 40
---
# Progettazione di un modello di integrazione applicativa dei dati
  È possibile sviluppare un modello per il servizio di integrazione applicativa dei dati aggiungendo entità e metodi a un file modello.  Un'entità descrive una raccolta di campi dati,  Ad esempio un'entità può rappresentare una tabella di un database.  Un metodo esegue un'attività quale l'aggiunta, l'eliminazione o l'aggiornamento dei dati rappresentati dalle entità.  Per ulteriori informazioni, vedere [Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md).  
  
## Aggiunta di entità  
 È possibile aggiungere un'entità trascinando o copiando un oggetto **Entità** dalla **Casella degli strumenti** di Visual Studio nella finestra di progettazione di integrazione applicativa dei dati.  Per ulteriori informazioni, vedere [Procedura: aggiungere un'entità al modello](../sharepoint/how-to-add-an-entity-to-a-model.md).  
  
 Definire i campi dell'entità in una classe,  ad esempio aggiungere un campo denominato `Address` a una classe `Customer`.  È possibile aggiungere una nuova classe al progetto o utilizzare una classe esistente creata tramite altri strumenti, ad esempio Progettazione relazionale oggetti.  Il nome dell'entità e il nome della classe che rappresenta l'entità non devono corrispondere.  La classe viene correlata all'entità durante la definizione dei metodi nel modello.  
  
## Aggiunta di metodi  
 Il servizio di integrazione applicativa dei dati chiama i metodi nel modello quando gli utenti visualizzano, aggiungono, aggiornano o eliminano informazioni in un elenco o una Web part basata sul modello.  È necessario aggiungere un metodo al modello per ogni attività che l'utente può eseguire.  Creare metodi selezionando uno dei cinque tipi di metodo di base nella finestra **Dettagli metodo di integrazione applicativa dei dati**.  Nella tabella riportata di seguito vengono descritti i cinque metodi di base di un modello di integrazione applicativa dei dati:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|Finder|Restituisce una raccolta di istanze di entità.  Viene chiamato quando l'utente apre l'elenco o la Web part.  Per ulteriori informazioni, vedere [Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md).|  
|Finder specifico|Restituisce un'istanza di entità specifica.  Viene chiamato quando un utente visualizza i dettagli di un elemento specifico in un elenco.  Per ulteriori informazioni, vedere [Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md).|  
|Creator|Aggiunge nuovi dati all'origine dati di un'entità.  Viene chiamato quando gli utenti fanno clic sul pulsante **Nuovo elemento** sulla barra multifunzione di un elenco basato sul modello.  Per ulteriori informazioni, vedere [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md).|  
|Updater|Modifica i dati in un elenco.  Viene chiamato quando gli utenti aggiornano le informazioni in un elenco.  Per ulteriori informazioni, vedere [Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md).|  
|Deleter|Rimuove i dati.  Viene chiamato quando gli utenti eliminano un elemento dall'elenco.  Per ulteriori informazioni, vedere [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md).|  
  
## Definizione dei parametri dei metodi  
 Quando si crea un metodo, in Visual Studio vengono aggiunti i parametri di input e di output adatti al tipo di metodo.  Tali parametri hanno solo una funzione di segnaposto.  Nella maggior parte dei casi è necessario modificarli in modo che passino o restituiscano il tipo corretto di dati.  Per impostazione predefinita, un metodo Finder restituisce ad esempio una stringa.  Nella maggior parte dei casi si desidera modificare il parametro restituito dal metodo Finder in modo che restituisca una raccolta di entità.  A tale scopo è necessario modificare il descrittore di tipo del parametro.  Un descrittore di tipo è una raccolta di attributi che descrive il tipo di dati di un parametro.  Per ulteriori informazioni, vedere [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 In Visual Studio è possibile copiare i descrittori di tipo tra i parametri del modello.  È ad esempio possibile definire un descrittore di tipo denominato `CustomerTD` per il parametro restituito dal metodo `GetCustomer`.  Il descrittore di tipo `CustomerTD` può quindi essere copiato in **Esplora integrazione applicativa dei dati** e incollato nel parametro di input del metodo `CreateCustomer`.  In questo modo si evita di definire lo stesso descrittore di tipo più volte.  
  
##  <a name="MethodInstances"></a> Istanze di metodo  
 In Visual Studio quando si crea un metodo viene aggiunta un'istanza di metodo predefinita.  Un'istanza di metodo è un riferimento a un metodo, con i valori predefiniti per i parametri.  Un singolo metodo può includere più istanze di metodo.  Ogni istanza è una combinazione di firma del metodo e set di valori predefiniti.  Per ulteriori informazioni, vedere [How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
 Quando si esegue il progetto, vengono visualizzate istanze del metodo in un elenco a discesa sopra l'elenco di SharePoint.  Gli utenti possono selezionare istanze del metodo per visualizzare i dati.  
  
 Per aggiungere valori predefiniti all'istanza del metodo, è necessario modificare direttamente il codice XML del modello.  Per ulteriori informazioni, vedere [ValorePredefinito](http://go.microsoft.com/fwlink/?LinkID=169279).  
  
## Aggiunta di descrittori di filtro  
 I consumer del modello potrebbero desiderare di recuperare le istanze di un'entità che corrispondono ad alcuni criteri.  Per abilitare questa funzionalità, è possibile aggiungere un descrittore di filtro a un metodo.  I descrittori di filtro consentono ai consumer del modello di filtrare set di risultati del metodo passando valori ai metodi prima che vengano eseguiti.  Per ulteriori informazioni, vedere [Procedura: aggiungere parametri di filtro alle operazioni per limitare le istanze del sistema esterno](http://go.microsoft.com/fwlink/?LinkID=169267).  
  
 In SharePoint sono disponibili diverse funzionalità che consentono agli utenti di specificare valori di filtro.  Le Web part di integrazione applicativa dei dati offrono, ad esempio, una casella di testo di filtro.  Gli utenti possono limitare i dati in un elenco digitando un valore nella casella di testo.  Per ulteriori informazioni sull'aggiunta di un descrittore di filtro a un metodo, vedere [Procedura: aggiungere un descrittore di filtro a un metodo Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
### Proprietà del descrittore di filtro  
 È necessario impostare il valore delle proprietà **Descrittori di tipo associati**, **Nome** e **Tipo** di un descrittore di filtro.  Tutte le altre proprietà sono facoltative.  
  
 La proprietà **Descrittori di tipo associati** mette in relazione il descrittore di filtro con un parametro di input.  Quando un utente specifica un valore di filtro, il servizio di integrazione applicativa dei dati passa tale valore nel metodo tramite il parametro di input.  
  
 La proprietà **Tipo** descrive il criterio di filtro da utilizzare.  In SharePoint il criterio di filtro selezionato influisce sul testo visualizzato nell'interfaccia utente.  Per un criterio di filtro Criteri di confronto, ad esempio, il testo **è uguale a** viene visualizzato come controllo di una Web part di integrazione applicativa dei dati.  Per ulteriori informazioni su ogni modello di filtro, vedere [Tipi di filtri supportati da BDC](http://go.microsoft.com/fwlink/?LinkId=169287).  
  
 Per ulteriori informazioni sulle proprietà di un descrittore di filtro, vedere [FilterDescriptor](http://go.microsoft.com/fwlink/?LinkID=169280).  
  
### Specifica dei valori predefiniti  
 In alcuni casi l'utente potrebbe non specificare un valore di filtro.  È possibile specificare un valore predefinito aggiungendolo all'istanza del metodo o impostandolo nel codice del metodo.  Per ulteriori informazioni su come aggiungere un valore predefinito all'istanza di metodo, vedere [MethodInstance](http://go.microsoft.com/fwlink/?LinkID=169282).  Per un esempio di come impostare il valore predefinito di un parametro di input nel codice del metodo, vedere [Procedura: aggiungere un descrittore di filtro a un metodo Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md).  
  
## Convalida del modello  
 È possibile convalidare il modello durante lo sviluppo.  In Visual Studio vengono identificati i problemi che possono impedire il comportamento previsto del modello.  Tali problemi vengono visualizzati nell'**Elenco errori** di Visual Studio.  
  
 È possibile convalidare un modello dal menu di scelta rapida per la finestra di progettazione di integrazione applicativa dei dati e scegliendo **Convalida**.  Se il modello contiene eventuali errori, vengono visualizzati in **Elenco errori**.  È possibile spostare rapidamente il cursore sul codice che contiene un errore facendo doppio clic sull'errore nell'elenco.  In alternativa, è possibile scegliere ripetutamente le chiavi F8 o Shift\+F8 per spostarsi avanti o indietro negli errori nell'elenco.  
  
 Possono verificarsi errori di convalida quando le regole del modello vengono violate in qualche modo.  Se, ad esempio, la proprietà **IsCollection** di un descrittore di tipo viene impostata su **true**, ma non esistono descrittori di tipo figlio, verrà visualizzato un errore di convalida.  Per comprendere alcuni errori visualizzati nell'**Elenco errori** di Visual Studio potrebbe essere necessario fare riferimento alle regole di un modello di integrazione applicativa dei dati.  Per ulteriori informazioni sulle regole del modello BDC, vedere [Schema di BDCMetadata](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## Debug della soluzione contenente il modello  
 È possibile eseguire il debug del codice procedendo come per qualsiasi codice in Visual Studio.  Per eseguire il debug del codice, impostare punti di interruzione nelle posizioni desiderate all'interno del codice, quindi avviare il debugger.  Verrà aperto il sito di SharePoint.  In SharePoint creare un elenco o una Web part che utilizzi i dati di integrazione applicativa.  Sarà quindi possibile eseguire il codice un'istruzione alla volta.  Per ulteriori informazioni sul debug di progetti SharePoint, vedere [Risoluzione dei problemi relativi alle soluzioni SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  
  
 È possibile inoltre eseguire il debug del codice negli assembly personalizzati che si aggiungono al progetto.  Tuttavia, per eseguire il debug del codice in un assembly personalizzato, è necessario aggiungere l'assembly al pacchetto della soluzione.  Per ulteriori informazioni, vedere [Procedura: Aggiungere e rimuovere assembly aggiuntivi](../sharepoint/how-to-add-and-remove-additional-assemblies.md).  
  
 Per ulteriori informazioni sull'aggiunta di un assembly personalizzato al progetto, vedere [Procedura: includere un assembly personalizzato in una funzionalità di integrazione applicativa dei dati](../sharepoint/how-to-include-a-custom-assembly-in-a-bdc-feature.md).  
  
### Configurazione della sicurezza del servizio di integrazione applicativa dei dati  
 Può essere necessario modificare le impostazioni di sicurezza in SharePoint prima di eseguire il debug della soluzione.  A tale scopo, aprire l'applicazione del servizio di integrazione applicativa dei dati nel sito Web di Amministrazione centrale SharePoint 2010.  Nella finestra di dialogo **Imposta autorizzazioni archivio metadati** aggiungere l'account utente, quindi selezionare una delle opzioni seguenti:  
  
|Attività|Opzione|  
|--------------|-------------|  
|Distribuire modelli nel servizio di integrazione applicativa dei dati|Edit|  
|Creare elenchi e Web part tramite tipi di contenuto esterni \(entità\) nel modello.|Selezione nei client|  
|Creare, leggere, aggiornare ed eliminare dati di entità.|Execute|  
  
 Per ulteriori informazioni su queste impostazioni, vedere [Business Data Connectivity service management](http://go.microsoft.com/fwlink/?LinkID=178883).  
  
 È inoltre possibile impostare autorizzazioni di sicurezza per singoli modelli o per tipi di contenuto esterni.  Per ulteriori informazioni su come impostare le autorizzazioni di sicurezza di un modello, vedere [Gestione del modello BDC](http://go.microsoft.com/fwlink/?LinkID=178884).  Per ulteriori informazioni su come impostare le autorizzazioni di sicurezza di un tipo di contenuto esterno, vedere [Gestione del tipo di contenuto esterno](http://go.microsoft.com/fwlink/?LinkID=178885).  
  
> [!NOTE]  
>  Utilizzare queste impostazioni per eseguire il debug di una soluzione sul server SharePoint locale.  Per ulteriori informazioni su come configurare le impostazioni di sicurezza relative all'integrazione applicativa dei dati sul server SharePoint di produzione, vedere [Cenni preliminari sulla sicurezza dei servizi di integrazione applicativa dei dati](http://go.microsoft.com/fwlink/?LinkID=178886).  
  
### Ritrazione dei modelli danneggiati  
 Quando il debugger viene avviato per la prima volta, in Visual Studio l'intero modello viene distribuito in SharePoint.  Successivamente il modello verrà aggiornato ogni volta in SharePoint con le eventuali modifiche apportate tra le varie distribuzioni.  
  
 In determinate circostanze potrebbe essere necessario ritrarre completamente il modello da SharePoint,  ad esempio quando viene danneggiato.  Per ridistribuire il modello in SharePoint, impostare la proprietà **Aggiornamento incrementale** del modello su **False**, quindi avviare il debugger.  La proprietà **Aggiornamento incrementale** viene visualizzata nella finestra **Proprietà** quando si seleziona il nodo che rappresenta il modello in **Esplora integrazione applicativa dei dati**.  Per impostazione predefinita, il nome del modello è **BdcModel1**.  
  
### Modifica dei nomi dell'identificatore di entità nel modello  
 Se si modifica il nome di un identificatore dopo avere distribuito il modello, è possibile che venga restituito un errore di distribuzione.  Non è possibile correggere questo errore impostando la proprietà **Aggiornamento incrementale** del modello su **False**.  È necessario recuperare manualmente il modello, quindi distribuire nuovamente la soluzione.  Per ulteriori informazioni, vedere [Risoluzione dei problemi relativi alle soluzioni SharePoint](../sharepoint/troubleshooting-sharepoint-solutions.md).  È possibile evitare questo errore impostando la proprietà **Aggiornamento incrementale** su **False** prima di distribuire inizialmente il modello.  
  
## Individuazione di documentazione per gli elementi del modello di integrazione applicativa dei dati  
 In Visual Studio viene aggiunto un elemento XML al modello di ogni entità, metodo o altro elemento creato.  Gli attributi degli elementi vengono visualizzati come proprietà nella finestra **Proprietà**.  Per informazioni sugli elementi e sugli attributi generati in Visual Studio durante la progettazione del modello, vedere [Schema BDCMetadata](http://go.microsoft.com/fwlink/?LinkID=169275).  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)|Vengono descritti gli strumenti che è possibile utilizzare per progettare visivamente un modello per l'integrazione applicativa dei dati.|  
|[Procedura: aggiungere un'entità al modello](../sharepoint/how-to-add-an-entity-to-a-model.md)|Viene mostrato come aggiungere tipi di contenuto o entità esterne al modello.|  
|[Procedura: aggiungere un metodo Finder](../sharepoint/how-to-add-a-finder-method.md)|Viene descritto come aggiungere un metodo che consente agli utenti di visualizzare un elenco di entità in un elenco o una Web part.|  
|[Procedura: aggiungere un metodo Finder specifico](../sharepoint/how-to-add-a-specific-finder-method.md)|Viene illustrato come aggiungere un metodo che consente agli utenti di visualizzare i dettagli di un'entità specifica.|  
|[Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md)|Viene descritto come aggiungere un metodo che consente agli utenti di aggiungere record a un'origine dati direttamente da un elenco o una Web part.|  
|[Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md)|Viene descritto come aggiungere un metodo che consente agli utenti di rimuovere dati da un'origine dati tramite le opzioni dell'interfaccia utente di un elenco o di una Web part.|  
|[Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md)|Viene descritto come aggiungere un metodo che consente agli utenti di modificare i record di dati in un'origine dati direttamente da un elenco o una Web part.|  
|[Procedura: aggiungere un parametro a un metodo](../sharepoint/how-to-add-a-parameter-to-a-method.md)|Viene illustrato come utilizzare la finestra dei dettagli del metodo di Visual Studio per aggiungere parametri restituiti e di input in un metodo.|  
|[How to: Define the Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)|Viene descritto come definire i tipi di dati dei parametri nel modello.|  
|[Procedura: definire un'istanza di metodo](../sharepoint/how-to-define-a-method-instance.md)|Viene illustrato come creare un'istanza di un metodo eseguita dall'integrazione applicativa dei dati.|  
|[Procedura: aggiungere un descrittore di filtro a un metodo Finder](../sharepoint/how-to-add-a-filter-descriptor-to-a-finder-method.md)|Viene illustrato come consentire agli utenti di limitare il numero di istanze restituite da un metodo Finder.|  
|[Creazione di un'associazione tra entità](../sharepoint/creating-an-association-between-entities.md)|Viene descritto come definire relazioni tra entità nel modello.  Le Web part di integrazione applicativa dei dati, gli elenchi esterni e le applicazioni personalizzate possono visualizzare queste relazioni tra i dati in un'interfaccia utente.|  
|[Procedura: creare un'associazione tra entità](../sharepoint/how-to-create-an-association-between-entities.md)|Viene descritto come definire relazioni tra entità nel modello.|  
|[Procedura dettagliata: creazione di un elenco esterno in SharePoint tramite il servizio di integrazione applicativa dei dati](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)|Vengono fornite istruzioni dettagliate che mostrano come creare e testare un modello che visualizza contatti in un elenco esterno di SharePoint.|  
|[Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)|Vengono forniti cenni preliminari sulla creazione e la progettazione di modelli per il servizio di integrazione applicativa dei dati.|  
  
  