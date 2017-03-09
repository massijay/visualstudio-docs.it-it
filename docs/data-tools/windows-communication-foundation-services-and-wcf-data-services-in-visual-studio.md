---
title: "Windows Communication Foundation Services and WCF Data Services in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "services, WCF Data"
  - "WCF services, binding to"
  - "WCF services, asynchronous service methods"
  - "service references [Visual Studio]"
  - "WCF Data Services"
  - "asynchronous calls"
  - "service references [Visual Studio], type sharing"
  - "endpoints [WCF]"
  - "asynchronous service methods"
  - "service references [Visual Studio] endpoints"
  - "WCF services, type sharing"
  - "Windows Communication Foundation, in Visual Studio"
  - "services, WCF"
  - "WCF service, Visual Studio"
  - "data services, WCF"
  - "services, in Visual Studio"
  - "data binding [Visual Studio], WCF"
  - "service endpoints [Visual Studio]"
  - "service references [Visual Studio], asynchronous calls"
  - "services, Windows Communication Foundation"
  - "type sharing in WCF services"
  - "WCF services, endpoints"
  - "service method, called asynchronously[Visual Studio]"
ms.assetid: d56f12cb-e139-4fec-b3e4-488383356642
caps.latest.revision: 26
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Communication Foundation Services and WCF Data Services in Visual Studio
In [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 2008 vengono forniti gli strumenti per utilizzare Windows Communication Foundation \(WCF\) e [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)], le tecnologie Microsoft per la creazione di applicazioni distribuite.  In questo argomento viene fornita un'introduzione ai servizi dalla prospettiva di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
## Cos'è WCF  
 [!INCLUDE[vsindigo](../data-tools/includes/vsindigo_md.md)] è un framework unificato per la creazione di applicazioni distribuite sicure, affidabili, transazionali e interoperabili.  Nelle versioni precedenti di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erano incluse diverse tecnologie utilizzabili per le comunicazioni tra applicazioni.  
  
 Se si desiderava condividere informazioni in modo da consentirne l'accesso da qualsiasi piattaforma, si utilizzava un servizio Web, noto anche come servizio Web ASMX.  Se si intendeva solo spostare i dati tra un client e un server che eseguiva il sistema operativo Windows, si utilizzava .NET Remoting.  Se si desiderava stabilire comunicazioni transazionali, si utilizzava Enterprise Services \(DCOM\), oppure se si desiderava un modello di accodamento si utilizzava Accodamento messaggi \(noto anche come MSMQ\).  
  
 WCF unisce le funzionalità di tutte quelle tecnologie in un modello di programmazione unificato,  semplificando l'esperienza dello sviluppo di applicazioni distribuite.  
  
#### Cosa sono i servizi dati WCF  
 [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] sono servizi che interagiscono direttamente con un database, consentendo di restituire i dati utilizzando verbi HTTP standard quali GET, POST, PUT o DELETE.  In generale [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] sono una buona scelta per le applicazioni utilizzate per creare, aggiornare o eliminare i record in un database.  Per ulteriori informazioni, vedere [Framework di ADO.NET Data Services](http://go.microsoft.com/fwlink/?LinkID=119952) \(la pagina potrebbe essere in inglese\).  
  
### Modello di programmazione di WCF  
 Il modello di programmazione di WCF si basa sulla comunicazione tra due entità: un servizio WCF e un client WCF.  Il modello di programmazione è incapsulato nello spazio dei nomi <xref:System.ServiceModel> in [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
#### Servizio WCF  
 Un servizio WCF si basa su un'interfaccia che definisce un contratto tra il servizio e il client  ed è contrassegnato con un attributo <xref:System.ServiceModel.ServiceContractAttribute>, come indicato nel codice seguente:  
  
 [!code-cs[WCFWalkthrough#6](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.cs)]
 [!code-vb[WCFWalkthrough#6](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_1.vb)]  
  
 [!code-cs[WCFWalkthrough#1](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.cs)]
 [!code-vb[WCFWalkthrough#1](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_2.vb)]  
  
 Si definiscono le funzioni o i metodi esposti da un servizio WCF contrassegnandoli con un attributo <xref:System.ServiceModel.OperationContractAttribute>.  Inoltre è possibile esporre dati serializzati contrassegnando un tipo composto con un attributo <xref:System.Runtime.Serialization.DataContractAttribute>,  così da consentire l'associazione dati in un client.  
  
 Dopo essere stati definiti, l'interfaccia e i relativi metodi vengono incapsulati in una classe che implementa l'interfaccia.  Una singola classe di servizio WCF può implementare più contratti di servizio.  
  
 Un servizio WCF viene esposto per l'utilizzo tramite un *endpoint*,  che fornisce la sola modalità di comunicazione con il servizio. Non è infatti possibile accedere al servizio tramite un riferimento diretto come accade con le altre classi.  
  
 Un endpoint è costituito da un indirizzo, un'associazione e un contratto.  L'indirizzo definisce dove si trova il servizio: può trattarsi di un URL, di un indirizzo FTP o di un percorso di rete o locale.  Un'associazione definisce la modalità di comunicazione con il servizio.  Le associazioni WCF forniscono un modello versatile per specificare un protocollo, ad esempio HTTP o FTP, un meccanismo di sicurezza, ad esempio Autenticazione di Windows o nomi utente e password e molto altro ancora.  Un contratto include le operazioni esposte dalla classe del servizio WCF.  
  
 Per un servizio WCF possono essere esposti più endpoint.  Ciò consente a client diversi di comunicare in modi differenti con lo stesso servizio.  Ad esempio, un servizio tecnico bancario potrebbe fornire un endpoint per i dipendenti e un altro per i clienti esterni, con ogni endopint che utilizza un indirizzo, un'associazione e\/o un contratto diversi.  
  
#### Client WCF  
 Un client WCF è costituito da un *proxy* che consente a un'applicazione di comunicare con un servizio WCF e da un endpoint che corrisponde a un endpoint definito per il servizio.  Il proxy viene generato sul lato client nel file app.config e include informazioni sui tipi e sui metodi esposti dal servizio.  Nel caso di servizi che espongono più endpoint, il client può selezionare quello più adatto alle proprie necessità, ad esempio per comunicare su HTTP e utilizzare l'Autenticazione di Windows.  
  
 Dopo avere creato un client WCF, si fa riferimento al servizio nel codice proprio come avviene per qualsiasi altro oggetto.  Ad esempio, per chiamare il metodo `GetData` mostrato precedentemente, si scrive del codice analogo al seguente:  
  
 [!code-cs[WCFWalkthrough#3](../data-tools/codesnippet/CSharp/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.cs)]
 [!code-vb[WCFWalkthrough#3](../data-tools/codesnippet/VisualBasic/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio_3.vb)]  
  
## Strumenti WCF in Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] 2008 fornisce gli strumenti utili per creare servizi WCF e client WCF.  Per la procedura dettagliata che illustra tali strumenti, vedere [Walkthrough: Creating and Accessing WCF Services](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md).  
  
### Creazione e test dei servizi WCF  
 È possibile utilizzare i modelli WCF di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] come base per creare rapidamente il proprio servizio.  È quindi possibile utilizzare l'host automatico dei servizi WCF e il client di prova WCF per eseguire il debug e il test del servizio.  Questi strumenti offrono congiuntamente un ciclo di debug e test rapido e comodo, ed eliminano la necessità di adottare un modello di hosting già nelle prime fasi.  
  
#### Modelli WCF  
 I modelli WCF di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] forniscono una struttura di classe di base per lo sviluppo di servizi.  Nella finestra di dialogo **Aggiungi nuovo progetto** sono disponibili vari modelli WCF,  tra cui i progetti Libreria di servizi di WCF nonché i modelli di siti Web di servizi WCF e i modelli di elemento di servizi WCF.  
  
 Quando si seleziona un modello, vengono aggiunti i file per un contratto di servizio, un'implementazione del servizio e una configurazione del servizio.  Tutti gli attributi necessari sono già presenti, così da avere a disposizione un tipo di servizio semplice per il quale non occorre scrivere il codice.  Se lo si desidera, chiaramente, è possibile aggiungere codice per fornire funzioni e metodi per il servizio effettivo, ma i modelli forniscono la base.  
  
 Per ulteriori informazioni sui modelli WCF, vedere [Modelli di Visual Studio WCF](../Topic/WCF%20Visual%20Studio%20Templates.md).  
  
#### Host dei servizi WCF  
 Quando si avvia il debugger di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] \(premendo F5\) per un progetto di servizi WCF, lo strumento dell'host dei servizi WCF viene avviato automaticamente per ospitare localmente il servizio.  L'host dei servizio WCF enumera i servizi in un progetto di servizi WCF, carica la configurazione del progetto e crea un'istanza di un host per ogni servizio trovato.  
  
 Utilizzando l'host dei servizi WCF è possibile testare un servizio WCF senza scrivere codice aggiuntivo o adottare un host specifico durante lo sviluppo.  
  
 Per ulteriori informazioni sull'host dei servizi WCF, vedere [Host servizio WCF \(WcfSvcHost.exe\)](../Topic/WCF%20Service%20Host%20\(WcfSvcHost.exe\).md).  
  
#### Client di prova WCF  
 Lo strumento Client di prova WCF consente di immettere i parametri di prova, inviare tale input a un servizio WCF e visualizzare la risposta che il servizio restituisce.  Lo strumento offre una efficiente modalità di testing dei servizi se abbinato all'host dei servizi WCF.  
  
 Quando si preme F5 per eseguire il debug di un progetto di servizi WCF, il client di prova WCF si apre e visualizza un elenco di endpoint dei servizi definiti nel file di configurazione.  È possibile testare i parametri e avviare il servizio e ripetere questo processo per testare e convalidare continuamente il servizio.  
  
 Per ulteriori informazioni sul client di prova WCF, vedere [Client di test WCF \(WcfTestClient.exe\)](../Topic/WCF%20Test%20Client%20\(WcfTestClient.exe\).md).  
  
### Accesso ai servizi WCF in Visual Studio  
 [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] semplifica l'attività di creazione dei client WCF, viene automaticamente generato un proxy e un endpoint per i servizi aggiunti tramite  **Aggiungere il riferimento al servizio** finestra di dialogo.  Tutte le informazioni di configurazione necessarie vengono aggiunte al file app.config. Nella maggior parte dei casi è sufficiente creare un'istanza del servizio per utilizzarlo.  
  
 La finestra di dialogo **Aggiungi riferimento al servizio** consente di immettere l'indirizzo per un servizio o cercare un servizio definito nella soluzione.  La finestra di dialogo restituisce l'elenco dei servizi e delle operazioni fornite da tali servizi.  Consente inoltre di definire lo spazio dei nomi mediante il quale si farà riferimento ai servizi nel codice.  
  
 La finestra di dialogo **Configura riferimento a servizio** consente di personalizzare la configurazione di un servizio.  È possibile modificare l'indirizzo di un servizio, specificare il livello di accesso, il comportamento asincrono e i tipi di contratto di messaggio nonché configurare il riutilizzo dei tipi.  
  
## Procedura: Selezionare un endpoint di servizi  
 Alcuni servizi WCF \(Windows Communication Foundation\) espongono più endpoint tramite i quali un client può comunicare con il servizio.  È possibile ad esempio che un servizio esponga un endpoint che utilizza un'associazione HTTP e la sicurezza del nome utente\/password e un secondo endpoint che utilizza FTP e Autenticazione di Windows.  Il primo può essere utilizzato da applicazioni che accedono al servizio dall'esterno di un firewall, mentre il secondo può essere impiegato su una rete Intranet.  
  
 In un caso del genere, è possibile specificare `endpointConfigurationName` come parametro al costruttore per un riferimento al servizio.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Per selezionare un endpoint di servizio  
  
1.  Aggiungere un riferimento a un servizio WCF.  Per ulteriori informazioni, vedere [How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md).  
  
2.  Nell'editor di codice aggiungere un costruttore per il riferimento al servizio.  
  
    ```vb#  
    Dim proxy As New ServiceReference.Service1Client(  
    ```  
  
    ```c#  
    ServiceReference.Service1Client proxy = new ServiceReference.Service1Client(  
    ```  
  
    > [!NOTE]
    >  Sostituire *RiferimentoServizio* con lo spazio dei nomi del riferimento al servizio e sostituire *ClientServizio1* con il nome del servizio.  
  
3.  Verrà visualizzato un elenco IntelliSense con gli overload per il costruttore.  Selezionare l'overload `endpointConfigurationName As String`.  
  
4.  Subito dopo l'overload, digitare `=` *NomeConfigurazione*, dove *NomeConfigurazione* è il nome dell'endpoint che si desidera utilizzare  
  
    > [!NOTE]
    >  Se non si conoscono i nomi degli endpoint disponibili, è possibile trovarli nel file app.config.  
  
#### Per trovare gli endpoint disponibili per un servizio WCF  
  
1.  In **Esplora soluzioni** fare clic con il pulsante destro del mouse sul file app.config del progetto che contiene il riferimento al servizio, quindi scegliere **Apri**.  Il file verrà visualizzato nell'editor di codice.  
  
2.  Cercare il tag `<Client>` nel file.  
  
3.  Cercare al di sotto del tag `<Client>` un tag che inizi con `<Endpoint>`.  
  
     Se il riferimento al servizio fornisce più endpoint, saranno presenti due o più tag `<Endpoint`.  
  
4.  All'interno del tag `<EndPoint>` è disponibile un parametro `name="`*NomeServizio*`"` \(dove *NomeServizio* rappresenta un nome dell'endpoint\).  Si tratta del nome per l'endpoint che può essere passato all'overload `endpointConfigurationName As String` di un costruttore per un riferimento al servizio.  
  
## Procedura: Per chiamare un metodo di servizio in modo asincrono  
 La maggior parte dei metodi nei servizi Windows Communication Foundation \(WCF\) possono essere chiamati in modo sincrono o asincrono.  Quando si chiama un metodo in modo asincrono, è possibile continuare ad eseguire l’applicazione purché si utilizzi una connessione lenta.  
  
 Per impostazione predefinita, quando si aggiunge un riferimento a un servizio a un progetto, questo è configurato per chiamare i metodi in maniera asincrona.  È possibile modificare il comportamento di chiamata asincrona ai metodi modificando un'impostazione nella finestra di dialogo **Configura riferimento a servizio**.  
  
> [!NOTE]
>  Questa opzione viene impostata in base al servizio.  Se uno metodo di un servizio viene chiamato in modo asincrono, tutti i metodi dovranno essere chiamati in modo asincrono.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Per chiamare un metodo di servizio in modo asincrono  
  
1.  In **Esplora soluzioni** selezionare il riferimento al servizio.  
  
2.  Scegliere **Configura riferimento a servizio** dal menu **Progetto**.  
  
3.  Nella finestra di dialogo **Configura riferimento a servizio** selezionare la casella di controllo **Genera operazioni asincrone**.  
  
## Procedura: Associare i dati restituiti da un servizio  
 È possibile associare i dati restituiti da un servizio Windows Communication Foundation \(WCF\) a un controllo come qualsiasi altra origine dati.  Quando si aggiunge un riferimento a un servizio WCF contenente tipi compositi che restituiscono dati, questi vengono aggiunti automaticamente alla finestra **Origini dati**.  
  
#### Per associare un controllo a un singolo campo dati restituito da un servizio WCF  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**.  Verrà visualizzata la finestra **Origini dati**.  
  
2.  Nella finestra **Origini dati** espandere il nodo relativo al riferimento al servizio.  Verranno visualizzati tutti i tipi compositi restituiti dal servizio.  
  
3.  Espandere un nodo per un tipo.  Verranno visualizzati i campi di dati relativi a questo tipo.  
  
4.  Selezionare un campo e fare clic sulla freccia a discesa per visualizzare un elenco di controlli disponibili per il tipo di dati.  
  
5.  Fare clic sul tipo di controllo a cui si desidera effettuare l’associazione.  
  
6.  Trascinare il campo su un form.  Il controllo verrà aggiunto al form insieme a un componente <xref:System.Windows.Forms.BindingSource> e un componente <xref:System.Windows.Forms.BindingNavigator>.  
  
7.  Ripetere i passaggi da 4 a 6 per ogni campo che si desidera associare.  
  
#### Per associare un controllo a un tipo composito restituito da un servizio WCF  
  
1.  Scegliere **Mostra origini dati** dal menu **Dati**.  Verrà visualizzata la finestra **Origini dati**.  
  
2.  Nella finestra **Origini dati** espandere il nodo relativo al riferimento al servizio.  Verranno visualizzati tutti i tipi compositi restituiti dal servizio.  
  
3.  Selezionare un nodo per tipo e fare clic sulla freccia a discesa per visualizzare un elenco di opzioni disponibili.  
  
4.  Fare clic su **DataGridView** per visualizzare i dati in una griglia oppure su **Dettagli** per visualizzare i dati in singoli controlli.  
  
5.  Trascinare il nodo nel form.  I controlli verranno aggiunti al form insieme a un componente <xref:System.Windows.Forms.BindingSource> e un componente <xref:System.Windows.Forms.BindingNavigator>.  
  
## Procedura: configurare un servizio riutilizzare i tipi esistenti  
 Quando si aggiunge un riferimento al servizio a un progetto, tutti i tipi definiti nel servizio verranno generati nel progetto locale.  Quando un servizio utilizza tipi [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] comuni o quando i tipi sono definiti in una libreria condivisa, vengono spesso creati tipi duplicati.  
  
 Per evitare questo problema, i tipi negli assembly a cui si fa riferimento vengono condivisi per impostazione predefinita.  Se si desidera disabilitare la condivisione dei tipi per uno o più assembly, utilizzare la finestra di dialogo **Configura riferimenti a servizio**.  
  
#### Per disabilitare la condivisione dei tipi in un solo assembly  
  
1.  In **Esplora soluzioni** selezionare il riferimento al servizio.  
  
2.  Scegliere **Configura riferimento a servizio** dal menu **Progetto**.  
  
3.  Nella finestra di dialogo **Configura riferimenti a servizio** selezionare **Riutilizza tipi negli assembly di riferimento specificati**.  
  
4.  Selezionare la casella di controllo relativa a ogni assembly in cui si desidera abilitare la divisione dei tipi.  Per disabilitare la condivisione dei tipi per un assembly, lasciare la casella di controllo deselezionata.  
  
#### Per disabilitare la condivisione dei tipi in tutti gli assembly  
  
1.  In **Esplora soluzioni** selezionare il riferimento al servizio.  
  
2.  Scegliere **Configura riferimento a servizio** dal menu **Progetto**.  
  
3.  Nella finestra di dialogo **Configura riferimenti a servizio** deselezionare la casella di controllo **Riutilizza tipi negli assembly di riferimento specificati**.  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Walkthrough: Creating and Accessing WCF Services](../data-tools/walkthrough-creating-a-simple-wcf-service-in-windows-forms.md)|Viene fornita una spiegazione dettagliata della procedura di creazione e utilizzo dei servizi WCF in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Walkthrough: Creating and Accessing a WCF Data Service in Visual Studio](../data-tools/walkthrough-creating-a-wcf-data-service-with-wpf-and-entity-framework.md)|Viene fornita una spiegazione dettagliata sulla creazione e sull'utilizzo di [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[Utilizzo degli strumenti di sviluppo WCF](../Topic/Using%20the%20WCF%20Development%20Tools.md)|Viene descritta la modalità di creazione ed esecuzione di test dei servizi WCF in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[How to: Add, Update, or Remove a Service Reference](../Topic/How%20to:%20Add,%20Update,%20or%20Remove%20a%20Service%20Reference.md)|Viene descritto come aggiungere, aggiornare o rimuovere servizi WCF da un progetto.|  
|[How to: Add, Update, or Remove a WCF Data Service Reference](../data-tools/how-to-add-update-or-remove-a-wcf-data-service-reference.md)|Viene illustrato come fare riferimento e utilizzare [!INCLUDE[ssAstoria](../data-tools/includes/ssastoria_md.md)] in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|[How to: Add a Reference to a Web Service](../Topic/How%20to:%20Add%20a%20Reference%20to%20a%20Web%20Service.md)|Viene illustrato come aggiungere a un progetto un riferimento a un servizio Web XML \(ASMX\).|  
|[Troubleshooting Service References](../data-tools/troubleshooting-service-references.md)|Vengono presentati alcuni errori comuni che possono verificarsi nei riferimenti ai servizi e viene spiegato come evitarli.|  
|[Debug dei servizi WCF](../debugger/debugging-wcf-services.md)|Vengono descritti alcuni problemi di debug comuni e vengono illustrate varie tecniche per il debug di servizi WCF.|  
|[Windows Communication Foundation Authentication Service Overview](../Topic/Windows%20Communication%20Foundation%20Authentication%20Service%20Overview.md)|Viene descritto come utilizzare WCF per fornire un servizio ruolo di un sito Web.|  
|[Messaging in the .NET Compact Framework](http://msdn.microsoft.com/it-it/fb74d82c-f81e-46f9-aceb-f875c5c6be4f)|Viene descritto il supporto per il livello d messaggistica WCF in .NET Compact Framework.|  
|[Procedura dettagliata: creazione di un'applicazione dati a più livelli](../data-tools/walkthrough-creating-an-n-tier-data-application.md)|Vengono fornite istruzioni dettagliate per la creazione di un dataset tipizzato e la separazione del codice dei TableAdapter e dei dataset in più progetti.|  
|[Add Service Reference Dialog Box](../Topic/Add%20Service%20Reference%20Dialog%20Box.md)|Vengono descritti gli elementi dell'interfaccia utente della finestra di dialogo **Aggiungi riferimento al servizio**.|  
|[Finestra di dialogo Configura riferimento a servizio](../data-tools/configure-service-reference-dialog-box.md)|Vengono descritti gli elementi dell'interfaccia utente della finestra di dialogo **Configura riferimento a servizio**.|  
  
## Riferimento  
 <xref:System.ServiceModel>  
  
 <xref:System.Data.Services>