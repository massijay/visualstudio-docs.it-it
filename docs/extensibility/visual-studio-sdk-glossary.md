---
title: "Glossario di Visual Studio SDK | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Glossario [Visual Studio SDK]"
ms.assetid: b64d432b-c39b-4904-ad18-3c3218b6e3aa
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Glossario di Visual Studio SDK
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo glossario vengono fornite le definizioni dei termini utilizzati nel [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] documentazione.  
  
## Termini  
 componente aggiuntivo  
 Un'applicazione di utilità, driver o altro software aggiunti a un'applicazione principale. Nell'ambiente di sviluppo integrato \(IDE\) di Visual Studio, un componente aggiuntivo è un'applicazione basata su automazione che estende le funzionalità dell'IDE.  
  
 modello di automazione  
 Il modello di automazione, noto in versioni precedenti di Visual Studio come modello di estensibilità, è un'interfaccia di programmazione che consente di accedere alle routine sottostanti tale unità IDE. Macro, componenti aggiuntivi e procedure guidate utilizzano oggetti nel modello di automazione per controllare o estendono le funzionalità dell'IDE.  
  
 contesto dell'interfaccia utente di comando  
 Associazione di un GUID con la visibilità di un comando dell'interfaccia utente o un elemento, ad esempio una barra degli strumenti. Contesto dell'interfaccia utente del comando è diversa dalla scelta di selezione in quanto non è collegato a una finestra.  
  
 Contesto dell'interfaccia utente del comando può essere utilizzato per:  
  
-   Assegnare un GUID a una barra degli strumenti visualizzata quando viene attivata una particolare finestra.  
  
-   Assegnare un GUID per la disponibilità di un comando senza la necessità di caricare o eseguire un VSPackage.  
  
-   Assegnare un GUID per influire sul tasto di scelta rapida attiva.  
  
-   Assegnare un GUID per attivare la registrazione macro.  
  
-   Assegnare un GUID per attivare la modalità di debug o per passare dalla progettazione alla modalità di esecuzione in un editor.  
  
 component  
 Componente software che può essere apportato parte delle funzionalità di un'applicazione senza l'applicazione con le informazioni sull'implementazione del software pre\-esistente. Comunicazione tra un componente e un'applicazione è esclusivamente tramite interfacce OLE.  
  
 gestione dei componenti  
 Un servizio, `SOleComponentManager`, che fornisce servizi di coordinamento di interfaccia utente non per i componenti di livello superiori. Il `SOleComponentManager` servizio implementa il `IOleComponentManager` interfaccia.  
  
 gestione dei componenti dell'interfaccia utente  
 Un servizio, `SOleComponentUIManager`, che fornisce servizi di coordinamento dell'interfaccia utente. Il `SOleComponentUIManager` servizio implementa il `IOleComponentUIManager` e `IOleInPlaceComponentUIManager` interfacce.  
  
 contenitore del contesto  
 Un `IVsUserContext` oggetto \(COM\) collegato a un componente di ambiente. Questo oggetto contiene parole chiave di ricerca, le parole chiave F1 e gli attributi relativi al componente. Contenitori di contesto inoltre puntare a eventuali contenitori sottocontesto che a loro collegati.  
  
 provider di contesto  
 Un componente nell'IDE che dispone di un elenco di contesto è associato. Tali componenti includono una finestra degli strumenti, editor o la gerarchia di progetto.  
  
 finestra di progettazione  
 Un'interfaccia di programmazione che consente agli utenti di modificare gli elementi dell'interfaccia utente \(Form, pulsanti e altri controlli\).  
  
 Oggetto DocData  
 Un oggetto COM che incapsula i dati sottostanti di un documento in un mondo in cui è presente una separazione documento\/visualizzazione \(ad esempio, nel caso di editor di testo, questo sarebbe il buffer di testo sottostante tutte le visualizzazioni di editor di testo\). Se il EditorFactory non fornisce questo oggetto, l'IDE verrà produrre uno per suo conto. La responsabilità di questo oggetto consiste nel gestire la persistenza dei dati e la semantica di condivisione di più visualizzazioni su questo stesso `DocData`. Se il `DocData` oggetto supporta la `IOleCommandTarget` interfaccia, verrà inclusa nel routing dei comandi di UIShell..  
  
 DocObject  
 Tecnologia utilizzata per ospitare l'interfaccia utente in un intervallo fornito dall'host. In particolare, questo termine si riferisce a qualsiasi incorporamento che supporta il `IOleDocument` e relative interfacce. Questa tecnologia ha molte applicazioni potenziali, ad esempio un dettaglio di implementazione di documenti di COM, finestre degli strumenti in Visual Basic 5.0, finestre di progettazione ActiveX in Visual Basic 6.0 e così via.  
  
 documento  
 Consente di fare riferimento in modo generico per il documento nel suo complesso, ovvero sia il `DocData` e `DocView`. Ad esempio, contiene un DocumentFrame un `DocView`, ma anche mantiene un riferimento a di `DocData` per gestire la persistenza.  
  
 DocView  
 DocObject\/Embedding\/finestra con cui l'utente interagisce per visualizzare e manipolare sottostante `DocData`. Si noti che gli utenti non usufruire di separazione che fa parte di documento\/visualizzazione di `DocObject` Progettazione di interfacce. Gli utenti utilizzano un intero DocObject per fungere da una vista anziché una nozione più astratti \(e meno formalizzato\) di dati sottostante, noto come `DocData`.`DocView` gli oggetti sono sempre incorporati con gli oggetti di cornice di documento \(finestre figlio MDI\) dell'IDE.  
  
 DTE  
 Il `DTE` oggetto \(estensibilità degli strumenti di sviluppo\) è il punto di accesso superiore nel modello di automazione di Visual Studio, che consente di automatizzare ed estendere l'IDE a livello di codice.  
  
 Finestra Guida dinamica  
 Finestra degli strumenti che viene implementato dall'IDE e visualizza un elenco di argomenti della Guida F1 o parola chiave di ricerca.  
  
 Editor  
 Codice \(CLSID classe\) che implementa il `DocView`. Implementa inoltre `DocData` Se la separazione di dati\/visualizzazione è supportata.  
  
 estensione  
 Una funzionalità che consente di modificare, consente di personalizzare o aggiunge un ambiente di sviluppo integrato. Si creano estensioni utilizzando il modello di automazione o di un package VS.  
  
 editor esterno  
 Un editor che non è specifico dell'IDE, ad esempio Microsoft Word. È stato registrato tramite i proprio meccanismi e può essere utilizzata all'esterno dell'IDE. Se questo editor può essere incorporato, viene visualizzato all'interno di una finestra nell'IDE. Se non può essere incorporato, viene creata una finestra di primo livello separata.  
  
 gerarchia  
 Struttura ad albero di nodi, ogni nodo associato a un set di proprietà.  
  
 componente di primo livello indipendente  
 Un componente che utilizza una finestra non modale di primo livello e può operare in modo efficace come una finestra dell'applicazione autonoma, ma viene implementato come un oggetto in\-process. Pertanto, un componente di livello superiore indipendente deve coordinare modalità e i servizi di ciclo di messaggi con l'IDE. Gli oggetti in\-process non sono proprio ciclo di messaggi.  
  
 provider di informazioni  
 Il provider di informazioni è un modulo che può cercare le parole chiave e restituire un elenco di argomenti, sotto forma di `IVsUserContextItem` oggetti. Per fornire elementi di parola chiave F1 e ricerca per il provider di informazioni, registrare il file della Guida compilato \(. HxS\) con il sistema. Gli argomenti della Guida in questi file vengono utilizzati per fornire l'elenco di argomenti visualizzati nella finestra Guida dinamica e indicato se un utente preme F1.  
  
 componente sul posto  
 Un oggetto package VS che implementa il `IOleInPlaceComponent` interfaccia per gestire una finestra visivamente contenuta all'interno di una finestra del documento dell'IDE di proprietà. I componenti sul posto non partecipano standard OLE\-unione di menu; ma i relativi elementi dell'interfaccia utente vengono integrate nell'IDE.  
  
 Esistono due tipi di componenti sul posto: cablata sul posto componenti e controlli dei componenti.  
  
 Cablata sul posto componenti sono disponibili i menu, barre degli strumenti e i comandi che sono strettamente integrati nell'interfaccia utente dell'IDE, viene visualizzato come se sono state compilate direttamente nell'IDE.  
  
 Controlli dei componenti non siano presenti i propri elementi dell'interfaccia utente integrati nell'IDE di; In alternativa utilizzare i menu, comandi e barre degli strumenti dell'IDE. Ad esempio, il comando grassetto può essere usato in grassetto una parola selezionata all'interno di un controllo di testo RTF incorporato in un form. Tuttavia, controlli di un componente possono richiedere di visualizzare elementi dell'interfaccia utente specifico del componente in modo dinamico installati.  
  
 servizio di linguaggio  
 Un set di oggetti che consente agli sviluppatori di VSPackage implementare le funzionalità dell'editor di codice lingua computer, ad esempio testo contrassegnare e colorare.  
  
 Progetto di file esterni  
 Progetto utilizzato per memorizzare i file aperti che non sono presenti in qualsiasi progetto. L'elenco di elementi in questo progetto non è persistente.  
  
 progetto  
 I progetti sono costituiti da oggetti della gerarchia o che implementano oggetti COM di `IVsHierarchy` interfaccia.  
  
 progettazione specifici del progetto o nell'editor  
 Finestra di progettazione che non può essere utilizzato indipendentemente dal tipo di progetto. Tutte le finestre di progettazione specifici del progetto immettere le informazioni di Editor Factory del Registro di sistema. L'IDE quindi possibile creare un'istanza alla finestra di progettazione ogni volta che un determinato tipo di file viene aperto in un progetto specifico.  
  
 finestra di tipo di progetto  
 Una finestra che costantemente tiene traccia della gerarchia del progetto attivo e dell'elemento dal contesto di selezione globale. Tipo di progetto windows utilizza il `SVsTrackSelectionEx` servizio per avvisare l'IDE di modifiche e visualizzare i commenti e suggerimenti all'utente. Esplora soluzioni è un esempio di una finestra del tipo di progetto.  
  
 Finestra Proprietà  
 In precedenza Visualizzatore proprietà.  
  
 progetti basati su riferimento  
 Progetto che non richiedono i file per il progetto si trovi nella stessa directory. Al contrario, i riferimenti ai file da altre directory non correlati vengono archiviati e gestiti dal progetto stesso.  
  
 tabella document in esecuzione  
 Struttura interna mediante il quale l'IDE gestisce l'elenco di tutti i documenti attualmente aperti. Questo elenco include tutti i documenti aperti in memoria indipendentemente dal fatto che i documenti sono in corso di modifica. Un documento è qualsiasi elemento che viene salvato, incluse le stored procedure aperte in un editor, i file in un progetto o il file di progetto principale \(ad esempio, i file vcproj\).  
  
 contesto della selezione  
 Dati che fa parte dei dettagli di ogni finestra dell'IDE e viene utilizzati per rilevare le selezioni attive. Contesto della selezione è costituita da:  
  
-   Puntatore al `IVsHierarchy` interfaccia della gerarchia del progetto  
  
-   Identificatore dell'elemento dell'elemento di progetto.  
  
-   Puntatore al `ISelectionContainer` interfaccia che fornisce accesso alle proprietà per gli oggetti attivi.  
  
-   Matrice di valori di elemento.  
  
 servizio  
 Un contratto per un set di interfacce COM che si trovano in un singolo oggetto COM. Quando si crea un servizio, che è identificato da un GUID, definire il set di interfacce COM che esegue il servizio. Gli oggetti COM utilizzano servizi per comunicare tra loro.  
  
 soluzione  
 Gruppo di progetti correlati con cui funziona un utente.  
  
 finestra di progettazione standard  
 Finestra di progettazione che può essere utilizzato indipendentemente dal tipo di progetto. Tutte le finestre di progettazione standard di immettere le informazioni di Editor Factory del Registro di sistema. L'IDE quindi possibile creare un'istanza alla finestra di progettazione ogni volta che viene aperto un file con un'estensione specifica. I dati devono essere salvati in un file.  
  
 editor standard  
 Editor che può essere utilizzato indipendente da qualsiasi tipo di progetto specifico. Tali editor sono EditorFactories registrato nel Registro di sistema. In questo modo l'IDE individuare e richiamare l'editor.  
  
 editor standard del sistema operativo  
 Incorporamento di un che non è Visual Studio specifico. È registrato utilizzando le chiavi di Win32 note \(ad esempio, Esplora risorse di Win32 sa come richiamare\). Se è possibile incorporare tali un editor, editor verrà visualizzata al suo posto nell'IDE. In caso contrario, viene creata una finestra di primo livello separata per tali editor.  
  
 contenitore sottocontesto  
 Un `IVsUserContext` oggetto collegato a un contenitore del contesto. Questo oggetto contiene parole chiave di ricerca, le parole chiave F1 e gli attributi per una selezione all'interno di un componente IDE. Esempi di sottocontesto includono un comando in una finestra degli strumenti o una parola chiave in un editor.  
  
 Elenco attività  
 Finestra degli strumenti che viene implementato dall'IDE e visualizza un elenco di attività attive.  
  
 buffer di testo  
 Nome comune per l'oggetto `VSTextBuffer`.  
  
 Visualizzazione di testo  
 Nome comune per l'oggetto `VSTextView`.  
  
 componente di livello principale dello strumento  
 Un componente che funziona come una finestra popup non modale, coordinamento strettamente con l'interfaccia utente dell'IDE. Come i componenti di livello superiori indipendenti, componenti di livello principale dello strumento devono inoltre coordinare modalità e i servizi di ciclo di messaggi con l'IDE.  
  
 componente di primo livello  
 Un oggetto package VS che gestisce una finestra non modale di livello superiore anziché l'area client di una finestra dell'IDE. Implementano i componenti di livello superiori di `IOleComponent` interfaccia per sfruttare i vantaggi dei servizi di ciclo di messaggi come l'accesso per il tempo di inattività.  
  
 Attivi dell'interfaccia utente  
 Un oggetto VSPackage è visibile e attualmente attivo.  
  
 Gerarchia dell'interfaccia utente  
 Un oggetto COM che implementa il `IVsUIHierarchy` interfaccia per consentire la visualizzazione di una gerarchia. Implementa la finestra gerarchia dell'interfaccia utente di `ISelectionContainer` interfaccia per aggiornare la finestra Proprietà, altre finestre del tipo di progetto è possono utilizzare questa implementazione, se necessario.  
  
 VSCT  
 Tabella di comandi di Visual Studio. Il file vsct contiene informazioni sul posizionamento e comportamenti dei menu, barre degli strumenti e i comandi in formato XML.  
  
 Package VS  
 Un componente installabile software che estende l'IDE di Visual Studio, contribuendo a uno o più delle operazioni seguenti: interfaccia utente, servizi, i tipi di progetto o dell'editor di progettazione. Un VSPackage è costituito da un oggetto COM che implementa il `IVsPackage` interfaccia e uno o più altri oggetti COM che implementano altre interfacce per supportare la selezione e altre funzionalità. Inoltre, un VSPackage presenta requisiti di registrazione specifica.