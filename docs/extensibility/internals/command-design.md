---
title: "Progettazione di comando | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comandi"
  - "i comandi, implementazione"
ms.assetid: 097108c3-f758-4b87-89d6-b32d12d9041a
caps.latest.revision: 34
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 34
---
# Progettazione di comando
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Quando si aggiunge un comando a un package VS, è necessario specificare dove è di visualizzato, quando è disponibile e come deve essere gestito.  
  
## Definizione dei controlli  
 Per definire nuovi controlli, includere un file della Tabella dei comandi di Visual Studio \(.vsct\) nel progetto VSPackage.  Se è stato creato un pacchetto VS utilizzando il modello importa pacchetto di Visual Studio, il progetto include uno di questi file.  Per ulteriori informazioni, vedere [Tabella di comandi di Visual Studio \(. File Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md).  
  
 Visual Studio che tutti i file con estensione .vsct cerca in modo da poter visualizzare i controlli.  Poiché questi file sono diversi dal file di package VS, Visual Studio non deve caricare il pacchetto per individuare controlli.  Per ulteriori informazioni, vedere [Come package VS aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
 Visual Studio utilizza l'attributo di registrazione di <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> per definire le risorse di menu e i controlli.  Per ulteriori informazioni, vedere [Implementazione](../../extensibility/internals/command-implementation.md).  
  
 I controlli possono essere modificati in fase di esecuzione in vari modi.  Possono essere visualizzati o nascosti, abilitati o disabilitati.  È possibile visualizzare testo o le icone diverso, o contenere valori diversi.  Molte personalizzazione può essere eseguita prima di carico di Visual Studio il package VS.  Per ulteriori informazioni, vedere [Come package VS aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
## gestori comandi  
 Quando si crea un comando, è necessario fornire un gestore eventi per eseguire il comando.  Se l'utente seleziona il comando, necessario in modo appropriato da correggere.  Una destinazione comando significa inviarla al package VS corretto per abilitare o disabilitare, il nascondere o visualizzare e lo esegue se l'utente sceglie a tale scopo.  Per ulteriori informazioni, vedere [Algoritmo di routing](../../extensibility/internals/command-routing-algorithm.md).  
  
## L'ambiente del comando di Visual Studio  
 Visual Studio può contenere qualsiasi numero di Vspackage ed è facilitare il proprio gruppo di comando.  Verrà visualizzato l'ambiente solo i controlli appropriati all'attività corrente.  Per ulteriori informazioni, vedere [Disponibilità](../../extensibility/internals/command-availability.md) e [Selezione oggetti di contesto](../../extensibility/internals/selection-context-objects.md).  
  
 Un package VS che definisce i nuovi controlli, i menu, barre degli strumenti, o i menu di scelta rapida vengono fornite le informazioni sui comandi di Visual Studio in fase di installazione tra voci del Registro di sistema che fa riferimento a risorse in codice nativo o assembly gestiti.  Ogni risorsa fare riferimento a un file di risorse di dati binari \(.cto\), che viene generato quando si compila un file della Tabella dei comandi di Visual Studio \(.vsct\).  Ciò consente a Visual Studio per fornire insiemi uniti di comando, i menu e le barre degli strumenti senza che sia necessario caricare ogni package VS installato.  
  
### Organizzazione di comando  
 L'ambiente consente di posizionare i controlli del gruppo, alla priorità e scegliere dal menu.  
  
-   I gruppi vengono raccolte logiche di controlli correlati, ad esempio, di **tagliare**, di **copia**e di gruppo di controlli di **Incolla** .  I gruppi sono i controlli visualizzati i menu.  
  
-   La priorità determina l'ordine in cui i singoli controlli in un gruppo appaiono nel menu.  
  
-   i menu fungono da contenitori per i gruppi.  
  
 L'ambiente predefinisce alcuni controlli, gruppi e menu.  Per ulteriori informazioni, vedere [Comando predefinito, gruppo e il posizionamento della barra degli strumenti](../../extensibility/internals/default-command-group-and-toolbar-placement.md).  
  
 Un comando può essere assegnato a un gruppo primario.  I controlli primari del gruppo la posizione del comando nella struttura del menu principale e nella finestra di dialogo di **personalizzare** .  Un comando può essere visualizzato nei gruppi più, ad esempio, un comando può essere il menu principale, un menu di scelta rapida e una barra degli strumenti.  Per ulteriori informazioni, vedere [Come package VS aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md).  
  
### Routing dei comandi  
 Il processo di chiamata e la risoluzione dei controlli per Vspackage è diverso dal processo di chiamare i metodi sulle istanze dell'oggetto.  
  
 I controlli della route dell'ambiente in sequenza dal contesto più interno del comando \(locale\), basato sulla selezione corrente, al contesto \(globale\) più esterno.  Il primo contesto che può eseguire il comando è che la gestione.  Per ulteriori informazioni, vedere [Algoritmo di routing](../../extensibility/internals/command-routing-algorithm.md).  
  
 Nella maggior parte delle istanze, i controlli di handle di ambiente utilizzando l'interfaccia di <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> .  Poiché la combinazione di routing dei comandi numerosi oggetti diversi in per gestire i controlli, <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> può essere implementato da un numero qualsiasi di oggetti, questi comprendono i controlli ActiveX Microsoft, implementazioni di visualizzazione della finestra, oggetti documento, gerarchie di progetto e package VS è oggetti \(per i controlli globali\).  In qualche specializzato caso, ad esempio, il routing ordina in una gerarchia, l'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy> deve essere distribuita.  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Implementazione](../../extensibility/internals/command-implementation.md)|Viene illustrato come implementare i controlli in un VSPackage.|  
|[Disponibilità](../../extensibility/internals/command-availability.md)|Viene descritto come il contesto di Visual Studio determina quali controlli sono disponibili.|  
|[Algoritmo di routing](../../extensibility/internals/command-routing-algorithm.md)|Viene descritto come l'architettura di routing dei comandi di Visual Studio consente ai controlli essere gestito da Vspackage diverso.|  
|[Linee guida per la selezione host](../../extensibility/internals/command-placement-guidelines.md)|Suggerisce come posizionare i controlli nell'ambiente di Visual Studio.|  
|[Come package VS aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)|Viene descritto come Vspackage possibile utilizzare al meglio l'architettura del comando di Visual Studio.|  
|[Comando predefinito, gruppo e il posizionamento della barra degli strumenti](../../extensibility/internals/default-command-group-and-toolbar-placement.md)|Viene descritto come Vspackage è preferibile utilizzare i controlli inclusi in Visual Studio.|  
|[La gestione di VSPackage](../../extensibility/managing-vspackages.md)|Viene descritto come viene caricata in Visual Studio Vspackage.|  
|[Tabella di comandi di Visual Studio \(. File Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)|Vengono fornite informazioni sui file XML di .vsct, utilizzati per descrivere il layout e l'aspetto dei controlli in Vspackage.|