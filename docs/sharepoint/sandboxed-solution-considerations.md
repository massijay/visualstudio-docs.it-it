---
title: "Considerazioni sulle soluzioni create mediante sandbox | Microsoft Docs"
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
  - "VS.SharePointTools.Project.SandboxedSolutions"
  - "VS.SharePointTools.Security.SandboxedSolutions"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "soluzioni farm [sviluppo per SharePoint in Visual Studio]"
  - "soluzioni create mediante sandbox [sviluppo per SharePoint in Visual Studio]"
  - "sviluppo per SharePoint in Visual Studio, soluzioni farm"
  - "sviluppo per SharePoint in Visual Studio, soluzioni create mediante sandbox"
ms.assetid: 6c2d2dc6-4acb-4b68-ba94-a61087e8dff0
caps.latest.revision: 23
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 22
---
# Considerazioni sulle soluzioni create mediante sandbox
  Le *soluzioni create mediante sandbox* sono una funzionalità di Microsoft SharePoint 2010 che consente agli utenti della raccolta siti di caricare le proprie soluzioni del codice personalizzate.  Una soluzione creata mediante sandbox comune prevede il caricamento delle proprie web part da parte degli utenti.  
  
 Un'applicazione di SharePoint creata mediante sandbox viene eseguita in un processo sicuro e monitorato che dispone dell'accesso a una parte limitata della Web farm.  In Microsoft SharePoint 2010 viene utilizzata una combinazione di funzionalità, raccolte e monitoraggio delle soluzioni, nonché un framework di convalida per abilitare le soluzioni create mediante sandbox.  
  
## Specifica del livello di attendibilità del progetto  
 In [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)], le soluzioni create mediante sandbox sono supportate tramite una proprietà booleana del progetto denominata *Sandboxed Solution*.  Questa proprietà può essere impostata nel progetto in qualsiasi momento o specificata quando si crea il progetto nella **Personalizzazione guidata SharePoint**.  
  
> [!NOTE]  
>  Se la proprietà *Sandboxed Solution* di un progetto viene modificata dopo la creazione, si potrebbero verificare errori di convalida.  
  
 Se la proprietà *Sandboxed Solution* viene impostata su **false** o si seleziona l'opzione **Distribuisci come soluzione farm**, la soluzione viene considerata come una soluzione con ambito farm.  Tuttavia, se la proprietà *Sandboxed Solution* viene impostata su **true** o si seleziona l'opzione **Distribuisci come soluzione creata mediante sandbox** nella procedura guidata, la soluzione viene trattata in modo diverso rispetto a una soluzione farm.  
  
## Gerarchia del sito di SharePoint  
 Per capire il funzionamento delle soluzioni create mediante sandbox, è opportuno sapere che i siti di SharePoint sono gerarchici dal punto di vista dell'ambito.  L'elemento superiore, a cui gli altri sono subordinati, è noto come Web farm:  
  
 Web farm  
  
 Applicazione Web A  
  
 Raccolta siti A1  
  
 Sito A1a  
  
 Applicazione Web B  
  
 Raccolta siti B1  
  
 Sito B1a  
  
 Sito B1b  
  
 Raccolta siti B2  
  
 Sito B2a  
  
 Come si può notare, nelle Web farm possono essere contenute una o più applicazioni Web che, a loro volta, possono includere una o più raccolte siti nelle quali possono essere presenti siti secondari e così via.  Le modifiche apportate a una raccolta siti influiscono solo su tale raccolta,  mentre le modifiche apportate a livello della Web farm influiscono su tutte le raccolte siti della farm.  
  
 Windows SharePoint Services 3.0 \(WSS\) permette di distribuire le soluzioni solo a livello di farm, mentre [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] consente di distribuire a livello di farm \(soluzione della farm\) oppure a livello di raccolta siti \(soluzione creata mediante sandbox\).  
  
## Funzione delle soluzioni create mediante sandbox  
 In WSS 3.0, le soluzioni potevano essere distribuite solo a livello di farm.  Pertanto sussisteva il rischio di distribuire soluzioni potenzialmente dannose o destabilizzanti che avrebbero interessato l'intera Web farm e tutte le altre raccolte siti e applicazioni in essa eseguite.  Tuttavia, tramite le soluzioni create mediante sandbox, è possibile distribuire le soluzioni in un'area secondaria della farm, ovvero una raccolta siti specifica.  Inoltre, per garantire una maggiore protezione, l'assembly della soluzione non viene caricato nel processo [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] principale \(w3wp.exe\),  bensì in uno separato \(SPUCWorkerProcess.exe\).  Questo processo è monitorato e implementa quote e limitazioni per proteggere la farm da soluzioni create mediante sandbox che eseguono attività dannose, ad esempio l'esecuzione di cicli rigidi che utilizzano cicli della CPU.  
  
## Raccolta di soluzioni della raccolta siti  
 [!INCLUDE[sharepointShort](../sharepoint/includes/sharepointshort-md.md)] 2010 è una funzionalità nota come "raccolta di soluzioni della raccolta siti". È possibile accedere a questa funzionalità dalla pagina Amministrazione centrale SharePoint 2010 o aprendo il menu **Azioni sito**, scegliendo **Impostazioni sito** e scegliendo il collegamento **Soluzioni** in  **Raccolte** nel sito di SharePoint.  Le raccolte di soluzioni sono repository di soluzioni che consentono agli amministratori della raccolta siti di gestire le soluzioni nelle proprie raccolte siti.  
  
 La raccolta di soluzioni è una raccolta documenti archiviata nel sito Web radice del sito di SharePoint.  La raccolta di soluzioni sostituisce i modelli di sito e supporta i pacchetti di soluzione.  Una volta caricato, un file del pacchetto di soluzione SharePoint \(con estensione wsp\) viene elaborato come una soluzione creata mediante sandbox.  
  
## Limitazioni delle soluzioni create mediante sandbox  
 Quando viene distribuita una soluzione creata mediante sandbox, la matrice della funzionalità SharePoint disponibile è limitata per consentire di ridurre qualsiasi vulnerabilità della sicurezza.  Di seguito sono riportate alcune di queste limitazioni:  
  
-   Le soluzioni create mediante sandbox dispongono di un sottoinsieme limitato di elementi della soluzione distribuibili.  I modelli di progetto SharePoint potenzialmente vulnerabili, ad esempio le definizioni di sito e i flussi di lavoro, non sono disponibili.  
  
-   SharePoint consente di eseguire il codice della soluzione creata mediante sandbox in un processo \(SPUCWorkerProcess.exe\) separato dal processo del pool di applicazioni [!INCLUDE[TLA2#tla_iis5](../sharepoint/includes/tla2sharptla-iis5-md.md)] \(w3wp.exe\) principale.  
  
-   Le cartelle mappate non possono essere aggiunte al progetto.  
  
-   I tipi nell'assembly Microsoft.Office.Server di [!INCLUDE[moss_14_long](../sharepoint/includes/moss-14-long-md.md)] non possono essere utilizzati nelle soluzioni create mediante sandbox.  Inoltre, solo i tipi nell'assembly Microsoft.SharePoint di [!INCLUDE[wss_14_long](../sharepoint/includes/wss-14-long-md.md)] possono essere utilizzati nelle soluzioni create mediante sandbox.  
  
 È importante notare che anche se una soluzione SharePoint viene specificata come soluzione creata mediante sandbox, il server SharePoint non sarà influenzato; infatti vengono soltanto determinati il modo in cui il progetto SharePoint viene distribuito a SharePoint da [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e gli assembly associati.  Questa condizione non influisce sul file con estensione wsp generato e quest'ultimo non dispone di dati direttamente correlati alla proprietà *Sandboxed Solution*.  
  
## Funzionalità ed elementi delle soluzioni create mediante sandbox  
 Le soluzioni create mediante sandbox supportano le funzionalità e gli elementi seguenti:  
  
-   Tipi\/campi del contenuto  
  
-   Azioni personalizzate  
  
-   Flussi di lavoro dichiarativi  
  
-   Ricevitori di eventi  
  
-   Callout di funzionalità  
  
-   Definizioni di elenco  
  
-   Istanze di elenco  
  
-   Modulo\/file  
  
-   Navigazione  
  
-   Onet.xml  
  
-   SPItemEventReceiver  
  
-   SPListEventReceiver  
  
-   SPWebEventReceiver  
  
-   Supporto per tutte le web part che derivano da `System.Web.UI.WebControls.WebParts.WebPart`  
  
-   Web part  
  
-   Elementi della funzionalità WebTemplate \(anziché Webtemp.xml\)  
  
-   Web part visive  
  
 Le soluzioni create mediante sandbox non supportano le funzionalità e gli elementi seguenti:  
  
-   Pagine applicazione  
  
-   Gruppo delle azioni personalizzate  
  
-   Funzionalità con ambito farm  
  
-   Elemento `HideCustomAction`  
  
-   Funzionalità con ambito applicazione Web  
  
-   Flussi di lavoro con codice  
  
## Vedere anche  
 [Differenze tra soluzioni create mediante sandbox e soluzioni farm](../sharepoint/differences-between-sandboxed-and-farm-solutions.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)  
  
  