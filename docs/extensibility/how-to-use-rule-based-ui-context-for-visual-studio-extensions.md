---
title: "Procedura: utilizzare il contesto dell&#39;interfaccia utente basata su regole per estensioni di Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8dd2cd1d-d8ba-49b9-870a-45acf3a3259d
caps.latest.revision: 7
ms.author: "gregvanl"
caps.handback.revision: 7
---
# Procedura: utilizzare il contesto dell&#39;interfaccia utente basata su regole per estensioni di Visual Studio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Visual Studio consente di caricare package VS quando noto <xref:Microsoft.VisualStudio.Shell.UIContext>s vengono attivati. Tuttavia, questi contesti dell'interfaccia utente non sono molto bene capillare, non lasciando gli autori delle estensioni scelta ma per selezionare un contesto dell'interfaccia utente disponibili che attiva prima del punto lo desiderano VSPackage da caricare. Per un elenco dei contesti dell'interfaccia utente ben noti, vedere <xref:Microsoft.VisualStudio.Shell.KnownUIContexts>.  
  
 Caricamento dei pacchetti può avere un impatto sulle prestazioni e caricarli prima del necessario, non è consigliata. Visual Studio 2015 introdotto il concetto di contesti di interfaccia utente basata su regole, un meccanismo che consente agli autori di estensione definire le condizioni esatte in cui viene attivato un contesto dell'interfaccia utente e caricamento VS associato.  
  
## Contesto dell'interfaccia utente basata su regole  
 Una "regola" è costituito da un nuovo contesto dell'interfaccia utente \(GUID\) e un'espressione booleana che fa riferimento a uno o più "condizioni" combinato con logica "e", "o", "No" operazioni. "Condizioni" vengono valutate in modo dinamico in fase di esecuzione e l'espressione viene valutata nuovamente ogni volta che le modifiche apportate al relativo termini. Quando l'espressione restituisce true, viene attivato il contesto dell'interfaccia utente associato. In caso contrario, il contesto dell'interfaccia utente è disattivato.  
  
 Contesto dell'interfaccia utente basata su regole può essere utilizzato in diversi modi:  
  
1.  Specificare i vincoli di visibilità per comandi e finestre degli strumenti. È possibile nascondere i comandi\/strumenti di windows finché non viene soddisfatta la regola di contesto dell'interfaccia utente.  
  
2.  I vincoli del carico automatico: caricamento automatico di pacchetti solo quando viene soddisfatta la regola  
  
3.  Posticipata di attività: ritardare il caricamento fino a quando non è trascorso un intervallo specificato e viene soddisfatta comunque la regola.  
  
 Il meccanismo può essere utilizzato da qualsiasi estensione di Visual Studio.  
  
## Creare un contesto dell'interfaccia utente basata su regole  
 Si supponga di che avere un'estensione denominata TestPackage, che offre un comando di menu che si applica solo ai file con estensione "config". Prima di VS2015, l'opzione migliore è caricare TestPackage quando <xref:Microsoft.VisualStudio.Shell.KnownUIContexts.SolutionExistsAndFullyLoadedContext%2A> contesto dell'interfaccia utente è stato attivato. Questo non è efficiente, poiché la soluzione caricata non può contenere anche un file config. Possiamo vedere come contesto dell'interfaccia utente basata su regole può essere utilizzato per attivare un contesto dell'interfaccia utente solo quando un file con estensione config sia selezionata e caricare TestPackage quando viene attivato il contesto dell'interfaccia utente.  
  
1.  Definire un nuovo GUID UIContext e aggiungere alla classe VSPackage <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> e <xref:Microsoft.VisualStudio.Shell.ProvideUIContextRuleAttribute>.  
  
     Ad esempio, si supponga che un nuovo UIContext "UIContextGuid" viene aggiunta. GUID creato \(è possibile creare un GUID, fare clic su Strumenti \-\> Crea guid\) è "8B40D5E2\-5626\-42AE\-99EF\-3DD1EFF46E7B". Aggiungere il seguente all'interno della classe del pacchetto:  
  
    ```c#  
    public const string UIContextGuid = "8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B";  
    ```  
  
     Per gli attributi, aggiungere il codice seguente: \(dettagli di questi attributi verranno illustrati più avanti\)  
  
    ```c#  
    [ProvideAutoLoad(TestPackage.UIContextGuid)]      
    [ProvideUIContextRule(TestPackage.UIContextGuid,  
        name: "Test auto load",   
        expression: "DotConfig",  
        termNames: new[] { "DotConfig" },  
        termValues: new[] { "HierSingleSelectionName:.config$" })]  
    ```  
  
     Questi metadati definiscono il nuovo GUID UIContext \(8B40D5E2\-5626\-42AE\-99EF\-3DD1EFF46E7B\) e un'espressione che fa riferimento a un solo termine, "DotConfig". Il termine "DotConfig" restituisce true ogni volta che la selezione corrente nella gerarchia di active ha un nome che corrisponde al modello di espressione regolare "\\.config$" \(termina con "config"\). Il valore \(predefinito\) definisce un nome facoltativo per la regola utile per il debug.  
  
     I valori dell'attributo vengono aggiunti a pkgdef generati durante la fase di compilazione in un secondo momento.  
  
2.  Nel file VSCT per i comandi del TestPackage, aggiungere il flag "DynamicVisibility" per i comandi appropriati:  
  
    ```xml  
    <CommandFlag>DynamicVisibility</CommandFlag>  
    ```  
  
3.  Nella sezione di visibilità del VSCT, associare i comandi appropriati per il nuovo UIContext GUID definito in \#1:  
  
    ```xml  
    <VisibilityConstraints>   
        <VisibilityItem guid="guidTestPackageCmdSet" id="TestId"  context="guidTestUIContext"/>   
    </VisibilityConstraints>  
    ```  
  
4.  Nella sezione Symbols, aggiungere la definizione di UIContext:  
  
    ```xml  
    <GuidSymbol name="guidTestUIContext" value="{8B40D5E2-5626-42AE-99EF-3DD1EFF46E7B}" />  
    ```  
  
     A questo punto, i comandi di menu di scelta per i file config saranno visibili solo quando l'elemento selezionato in Esplora soluzioni è un file con "estensione config" e il pacchetto non verrà caricato finché non viene selezionato uno di tali comandi.  
  
 Successivamente, utilizziamo un debugger per verificare che il pacchetto viene caricato solo quando è previsto. Per eseguire il debug TestPackage:  
  
1.  Impostare un punto di interruzione nel <xref:Microsoft.VisualStudio.Shell.Package.Initialize%2A> metodo.  
  
2.  Compilare il TestPackage e avviare il debug.  
  
3.  Creare un progetto o aprirne uno.  
  
4.  Selezionare tutti i file con estensione diversa da config. Non verrà raggiunto il punto di interruzione.  
  
5.  Selezionare il file app. config.  
  
 Il TestPackage carica e si arresta in corrispondenza del punto di interruzione.  
  
## Aggiunta di altre regole per il contesto dell'interfaccia utente  
 Poiché le regole di contesto dell'interfaccia utente sono espressioni booleane, è possibile aggiungere regole più limitate per un contesto dell'interfaccia utente. Ad esempio, nel contesto dell'interfaccia utente precedente, è possibile specificare che la regola si applica solo quando viene caricata una soluzione con un progetto. In questo modo, i comandi non vengono visualizzati se si apre un file con "estensione config" come file autonomo, non come parte di un progetto.  
  
```c#  
[ProvideAutoLoad(TestPackage.UIContextGuid)]      
[ProvideUIContextRule(TestPackage.UIContextGuid,    
    name: "Test auto load",  
    expression: "(SingleProject | MultipleProjects) & DotConfig",    
    termNames: new[] { "SingleProject", "MultipleProjects","DotConfig" },     
    termValues: new[] { VSConstants.UICONTEXT_SolutionHasSingleProject_string , VSConstants.UICONTEXT_SolutionHasMultipleProjects_string , "HierSingleSelectionName:.config$" })]  
```  
  
 A questo punto l'espressione fa riferimento a tre termini. Le prime due condizioni, "SingleProject" e "MultipleProjects", fare riferimento ad altri contesti dell'interfaccia utente noto \(in base al GUID\). Il terzo termine "DotConfig" è definito in precedenza il contesto dell'interfaccia utente basata su regole.  
  
## Attivazione ritardata  
 Le regole possono avere un parametro facoltativo "ritardo". Il ritardo specificato in millisecondi. Se presente, il ritardo comporta l'attivazione o disattivazione del contesto dell'interfaccia utente della regola deve essere ritardata a tale intervallo di tempo. Se prima dell'intervallo di ritardo di nuovo le modifiche di regola, quindi non accadrà nulla. Questo meccanismo può essere utilizzato per operazioni di inizializzazione \- soprattutto l'inizializzazione unica senza basarsi su timer o la registrazione delle notifiche di inattività "scaglionare".  
  
 Ad esempio, è possibile specificare la regola di carico di test per un ritardo di 100 millisecondi:  
  
```c#  
[ProvideAutoLoad(TestPackage.UIContextGuid)]  
[ProvideUIContextRule(TestPackage.UIContextGuid,   
    name: "Test auto load",  
    expression: "DotConfig",   
    termNames: new[] { "DotConfig" },  
    termValues: new[] { "HierSingleSelectionName:.config$" },   
    delay: 100)]  
```  
  
## Tipi  
 Ecco i diversi tipi di termine che sono supportati:  
  
|||  
|-|-|  
|{nnnnnnnn\-nnnn\-nnnn\-nnnn\-nnnnnnnnnnnn}|Il GUID si riferisce a un contesto dell'interfaccia utente. Al termine sarà true ogni volta che il contesto dell'interfaccia utente è attivo e false in caso contrario.|  
|HierSingleSelectionName: \< modello \>|Al termine sarà true ogni volta che la selezione nella gerarchia di attivo è un singolo elemento e il nome dell'elemento selezionato corrisponde all'espressione regolare .net specificato da "modello".|  
|UserSettingsStoreQuery: \< query \>|"query" rappresenta un percorso completo nell'archivio delle impostazioni utente che deve restituire un valore diverso da zero. La query è suddiviso in una "raccolta" e "propertyName" all'ultima barra.|  
|ConfigSettingsStoreQuery: \< query \>|"query" rappresenta un percorso completo nell'archivio di impostazioni di configurazione che deve restituire un valore diverso da zero. La query è suddiviso in una "raccolta" e "propertyName" all'ultima barra.|  
|ActiveProjectFlavor: \< projectTypeGuid \>|Al termine sarà true ogni volta che il progetto selezionato è tipo generico \(aggregato\) e dispone di una versione che corrisponde al tipo di progetto specificato GUID.|  
|ActiveEditorContentType: \< contentType \>|Al termine sarà true quando il documento selezionato è un editor di testo con il tipo di contenuto specificato.|  
|ActiveProjectCapability: \< espressione \>|Il termine è true quando le funzionalità di progetto attivo corrisponde all'espressione specificata. Un'espressione può essere simile a Visual Basic &#124; CSharp|  
|SolutionHasProjectCapability: \< espressione \>|Simile alla precedente, ma termine è true quando si dispone di qualsiasi progetto caricato che corrisponde all'espressione.|  
  
## Compatibilità con estensione tra versioni  
 Regola in base i contesti dell'interfaccia utente è una nuova funzionalità di Visual Studio 2015 e potrebbe non essere trasferito a versioni precedenti. Questo costituisce un problema con le estensioni\/pacchetti destinati a più versioni di Visual Studio che deve essere caricato automaticamente in Visual Studio 2013 e versioni precedenti, ma possono trarre vantaggio da contesti dell'interfaccia utente basato su regole per evitare che viene caricato automaticamente in Visual Studio 2015.  
  
 Per supportare questi pacchetti, AutoLoadPackages voci nel Registro di sistema ora possono fornire un flag nel campo valore per indicare che la voce deve essere ignorata in Visual Studio 2015 e versioni successive. Questa operazione può essere eseguita mediante l'aggiunta di un'opzione di flag per <xref:Microsoft.VisualStudio.Shell.PackageAutoLoadFlags>. Ora è possibile aggiungere i package VS **SkipWhenUIContextRulesActive** opzione alla loro <xref:Microsoft.VisualStudio.Shell.ProvideAutoLoadAttribute> attributo per indicare la voce deve essere ignorata in Visual Studio 2015 e versioni successive.  
  
## Regole di contesto dell'interfaccia utente estendibile  
 In alcuni casi, pacchetti non possono utilizzare le regole di contesto dell'interfaccia utente statiche. Si supponga, ad esempio, che si dispone di un pacchetto di supporto di estendibilità in modo che lo stato del comando si basa sui tipi di editor che sono supportati dai provider MEF importati. Il comando è abilitato se è disponibile un'estensione che supporta il tipo di modifica corrente. In questi casi il pacchetto stesso non può utilizzare una regola del contesto dell'interfaccia utente statica, poiché le condizioni cambierebbero a seconda di quale MEF estensioni sono disponibili.  
  
 Per supportare questi pacchetti, i contesti dell'interfaccia utente basato su regole supportano un'espressione hardcoded "\*" che indica tutti i termini del contratto verrà essere unito a o. In questo modo per il pacchetto master definire una regola nota basati su contesto dell'interfaccia utente e collegare il relativo stato di comando per questo contesto. In seguito qualsiasi estensione MEF per il pacchetto master di destinazione è possibile aggiungere le condizioni per gli editor che supporta senza influire sulle altre condizioni o l'espressione master.  
  
 Il costruttore <xref:Microsoft.VisualStudio.Shell.ProvideExtensibleUIContextRuleAttribute.%23ctor%2A> documentazione viene illustrata la sintassi per le regole di contesto dell'interfaccia utente estensibile.