---
title: "Creazione e modifica. File Vsct | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Creazione di file VSCT, manuali"
ms.assetid: e9f715dc-12b7-439b-bdf3-f3dc75e62f1c
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Creazione e modifica. File Vsct
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

In questo documento illustra come creare un file vsct per aggiungere voci di menu, barre degli strumenti e altri elementi dell'interfaccia utente per l'ambiente di sviluppo integrato \(IDE\) di Visual Studio. Utilizzare questa procedura quando si aggiungono elementi dell'interfaccia utente a un pacchetto Visual Studio \(VSPackage\) che non dispone già di un file vsct.  
  
 Per i nuovi progetti, è consigliabile utilizzare il modello di pacchetto di Visual Studio in quanto genera un file vsct che, a seconda delle selezioni, già dispone gli elementi necessari per un comando di menu, una finestra degli strumenti o un editor personalizzato. È possibile modificare questo file. vsct per soddisfare i requisiti del pacchetto di Visual Studio. Per ulteriori informazioni su come modificare un file. vsct, vedere gli esempi in [Estensione menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
## La creazione del File  
 Creare un file vsct in queste fasi: creazione della struttura di file e risorse, dichiarare gli elementi dell'interfaccia utente, inserire gli elementi dell'interfaccia utente nell'IDE e aggiungere eventuali particolari funzionalità.  
  
### Struttura di file  
 La struttura di base di un file. vsct è un [CommandTable](../../extensibility/commandtable-element.md) elemento radice che contiene un [comandi](../../extensibility/commands-element.md) elemento e un [simboli](../../extensibility/symbols-element.md) elemento.  
  
##### Per creare la struttura di file  
  
1.  Aggiungere al progetto un file vsct seguendo i passaggi descritti in [Procedura: creare una. File Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md).  
  
2.  Aggiungere gli spazi dei nomi necessari per il `CommandTable` elemento, come illustrato nell'esempio seguente.  
  
    ```xml  
    <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10-18/CommandTable"   
    	xmlns:xs="http://www.w3.org/2001/XMLSchema">  
  
    ```  
  
3.  Nel `CommandTable` elemento, aggiungere un `Commands` elemento per ospitare tutti i menu personalizzati, barre degli strumenti, i gruppi di comandi e comandi. In modo che sia possono caricare gli elementi dell'interfaccia utente personalizzati, il `Commands` elemento deve avere il `Package` attributo impostato sul nome del pacchetto.  
  
     Dopo il `Commands` elemento, aggiungere un `Symbols` elemento per definire i GUID per il pacchetto e i nomi e ID di comando per gli elementi dell'interfaccia utente.  
  
### Inclusione di risorse di Visual Studio  
 Utilizzare il [Extern](../../extensibility/extern-element.md) elemento per accedere ai file che definiscono i comandi di Visual Studio e i menu necessari per inserire elementi dell'interfaccia utente nell'IDE. Se si intende utilizzare i comandi definiti all'esterno del pacchetto, utilizzare il [UsedCommands](../../extensibility/usedcommands-element.md) elemento per informare Visual Studio.  
  
##### Per includere le risorse di Visual Studio  
  
1.  Nella parte superiore del `CommandTable` elemento, aggiungere uno `Extern` \(elemento\) per ogni file esterni da cui viene fatto riferimento e impostare il `href` attributo sul nome del file. È possibile fare riferimento i seguenti file di intestazione per accedere alle risorse di Visual Studio:  
  
    -   Stdidcmd.h, definisce gli ID per tutti i comandi esposti da Visual Studio.  
  
    -   Vsshlids.h, contiene gli ID di comando per i menu di Visual Studio.  
  
2.  Se il pacchetto chiama tutti i comandi che sono definiti da Visual Studio o da altri pacchetti, aggiungere un `UsedCommands` elemento dopo il `Commands` elemento. Inserire questo elemento con un [UsedCommand](../../extensibility/usedcommand-element.md) \(elemento\) per ogni comando è chiamare che non fanno parte del pacchetto. Impostare il `guid` e `id` gli attributi del `UsedCommand` elementi per i valori GUID e ID dei comandi per chiamare. Per ulteriori informazioni su come trovare i comandi i GUID e ID di Visual Studio, vedere [I GUID e ID dei comandi di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md). Per chiamare i comandi da altri pacchetti, utilizzare il GUID e l'ID del comando, come definito nel file vsct per tali pacchetti.  
  
### Dichiarazione di elementi dell'interfaccia utente  
 Dichiarare tutti gli elementi dell'interfaccia utente nuovi nel `Symbols` sezione del file vsct.  
  
##### Per dichiarare gli elementi dell'interfaccia utente  
  
1.  Nel `Symbols` elemento, aggiungere tre [GuidSymbol](../../extensibility/guidsymbol-element.md) elementi. Ogni `GuidSymbol` elemento ha un `name` attributo e un `value` attributo. Impostare il `name` dell'attributo in modo che rifletta lo scopo dell'elemento. Il `value` attributo accetta un GUID. \(Per generare un GUID nella **strumenti** menu, fare clic su **Crea GUID**, e quindi selezionare **il formato del Registro di sistema**.\)  
  
     Il primo `GuidSymbol` elemento rappresenta il pacchetto e in genere non ha elementi figlio. Il secondo `GuidSymbol` element rappresenta il comando set e conterrà tutti i simboli che definiscono il menu, gruppi e i comandi. Il terzo `GuidSymbol` elemento rappresenta l'archivio di immagini e contiene i simboli per tutte le icone dei comandi. Se non si dispone di alcun comando che utilizzano le icone, è possibile omettere il terzo `GuidSymbol` elemento.  
  
2.  Nel `GuidSymbol` elemento che rappresenta il set di comandi, aggiungere uno o più [IDSymbol](../../extensibility/idsymbol-element.md) elementi. Ciascuno di essi rappresentano un menu, barra degli strumenti, gruppo o comando per aggiungere l'interfaccia utente.  
  
     Per ogni `IDSymbol` elemento, impostare il `name` attributo per il nome verrà utilizzato per fare riferimento al menu corrispondente, gruppo o comando e quindi impostare il `value` elemento in un numero esadecimale che rappresenta l'id di comando. Due `IDSymbol` gli elementi che hanno lo stesso padre possono avere lo stesso valore.  
  
3.  Se uno qualsiasi degli elementi dell'interfaccia utente richiedono le icone, aggiungere un `IDSymbol` \(elemento\) per ogni icona per il `GuidSymbol` elemento che rappresenta l'archivio di immagini.  
  
### Inserimento di elementi dell'interfaccia utente nell'IDE  
 Il [menu](../../extensibility/menus-element.md) elemento [gruppi](../../extensibility/groups-element.md) elemento, e [pulsanti](../../extensibility/buttons-element.md) elemento contengono le definizioni per tutti i menu, gruppi e i comandi che sono definiti nel pacchetto. Inserire questi menu, gruppi e i comandi nell'IDE utilizzando un [padre](../../extensibility/parent-element.md) elemento che fa parte della definizione dell'elemento dell'interfaccia utente, oppure utilizzando un [CommandPlacement](../../extensibility/commandplacement-element.md) elemento che viene definito altrove.  
  
 Ogni `Menu`, `Group`, e `Button` elemento ha un `guid` attributo e un `id` attributo. Impostare sempre il `guid` affinché corrisponda al nome di attributo il `GuidSymbol` elemento che rappresenta il comando set e set il `id` attributo sul nome del `IDSymbol` elemento che rappresenta il menu, un gruppo o un comando nel `Symbols` sezione.  
  
##### Per definire gli elementi dell'interfaccia utente  
  
1.  Se si sta definendo nuovi menu, sottomenu, menu di scelta rapida né le barre degli strumenti, aggiungere un `Menus` elemento per il `Commands` elemento. Quindi, per ogni menu da creare, aggiungere un [Menu](../../extensibility/menu-element.md) elemento per il `Menus` elemento.  
  
     Impostare il `guid` e `id` gli attributi del `Menu` elemento e quindi impostare il `type` attributo al tipo di menu che si desidera. È inoltre possibile impostare il `priority` attributo per stabilire la posizione relativa del menu del gruppo padre.  
  
    > [!NOTE]
    >  Il `priority` attributo non è applicabile per le barre degli strumenti e menu di scelta rapida.  
  
2.  Tutti i comandi nell'IDE di Visual Studio devono essere ospitati da gruppi di comando, che sono figli diretti del menu e barre degli strumenti. Se si aggiunge nuovi menu e barre degli strumenti all'IDE, queste devono contenere nuovi gruppi di comando. È anche possibile aggiungere gruppi di comandi ai menu e barre degli strumenti esistenti in modo che è possibile raggruppare visivamente i comandi.  
  
     Quando si aggiungono nuovi gruppi di comando, è innanzitutto necessario creare un `Groups` elemento e quindi aggiungervi un [gruppo](../../extensibility/group-element.md) \(elemento\) per ogni gruppo di comando.  
  
     Impostare il `guid` e `id` gli attributi di ogni `Group` elemento e quindi impostare il `priority` attributo per stabilire la posizione relativa del gruppo di menu padre. Per altre informazioni, vedere [Creazione di gruppi riutilizzabili di pulsanti](../../extensibility/creating-reusable-groups-of-buttons.md).  
  
3.  Se si aggiungono nuovi comandi all'IDE, aggiungere un `Buttons` elemento per il `Commands` elemento. Quindi, per ogni comando, aggiungere un [pulsante](../../extensibility/button-element.md) elemento per il `Buttons` elemento.  
  
    1.  Impostare il `guid` e `id` gli attributi di ogni `Button` elemento e quindi impostare il `type` attributo al tipo di pulsante desiderato. È inoltre possibile impostare il `priority` attributo per stabilire la posizione relativa del comando nel gruppo padre.  
  
        > [!NOTE]
        >  Utilizzare `type="button"` per i comandi di menu standard e i pulsanti sulle barre degli strumenti.  
  
    2.  Nel `Button` elemento, aggiungere un [stringhe](../../extensibility/strings-element.md) elemento che contiene un [ButtonText](../../extensibility/buttontext-element.md) elemento e un [CommandName](../../extensibility/commandname-element.md) elemento. Il `ButtonText` elemento fornisce l'etichetta di testo per una voce di menu o la descrizione comando per un pulsante della barra degli strumenti. Il `CommandName` elemento fornisce il nome del comando da utilizzare nel comando.  
  
    3.  Se il comando sarà presente un'icona, creare un [icona](../../extensibility/icon-element.md) elemento il `Button` elemento e impostare il relativo `guid` e `id` gli attributi il `Bitmap` \(elemento\) per l'icona.  
  
        > [!NOTE]
        >  Pulsanti della barra degli strumenti devono disporre le icone.  
  
     Per altre informazioni, vedere [Confronto tra oggetti MenuCommand e OleMenuCommand](../../misc/menucommands-vs-olemenucommands.md).  
  
4.  Se i comandi richiedono le icone, aggiungere un [bitmap](../../extensibility/bitmaps-element.md) elemento per il `Commands` elemento. Quindi, per ogni icona, aggiungere un [Bitmap](../../extensibility/bitmap-element.md) elemento per il `Bitmaps` elemento. Ciò è possibile specificare il percorso della risorsa bitmap. Per altre informazioni, vedere [Aggiunta di icone ai comandi di Menu](../../extensibility/adding-icons-to-menu-commands.md).  
  
 È possibile basarsi sulla struttura padre per posizionare correttamente la maggior parte dei menu, gruppi e i comandi. Per set di comandi di dimensioni molto grandi, o quando un menu, un gruppo o un comando deve apparire in più posizioni, si consiglia di specificare il posizionamento di comando.  
  
##### Si basi sull'elemento padre di posizionare gli elementi dell'interfaccia utente nell'IDE  
  
1.  Tipico elemento padre, creare un `Parent` ogni elemento `Menu`, `Group`, e `Command` elementi definiti nel pacchetto.  
  
     La destinazione di `Parent` elemento è il menu o gruppo che conterrà il menu o comando.  
  
    1.  Impostare il `guid` il nome dell'attributo di `GuidSymbol` elemento che definisce il set di comandi. Se l'elemento di destinazione non fa parte del pacchetto, utilizzare il guid per il set di comandi, come definito nel file vsct corrispondente.  
  
    2.  Impostare il `id` attributo in modo che corrisponda il `id` attributo del menu di destinazione o del gruppo. Per un elenco di gruppi che vengono esposti da Visual Studio e i menu, vedere [GUID e ID del menu di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md) o [GUID e ID delle barre degli strumenti di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md).  
  
 Se si dispone di un numero elevato di elementi dell'interfaccia utente da inserire nell'IDE o se sono presenti elementi che devono essere visualizzate in più posizioni, definire le posizioni nel [CommandPlacements](../../extensibility/commandplacements-element.md) elemento, come illustrato nei passaggi seguenti.  
  
##### Per utilizzare il posizionamento di comando per inserire elementi dell'interfaccia utente nell'IDE  
  
1.  Dopo il `Commands` elemento, aggiungere un `CommandPlacements` elemento.  
  
2.  Nel `CommandPlacements` elemento, aggiungere un `CommandPlacement` \(elemento\) per ogni menu, un gruppo o un comando per inserire.  
  
     Ogni `CommandPlacement` elemento o `Parent` elemento posiziona un menu, un gruppo o un comando in una posizione di IDE. Un elemento dell'interfaccia utente può avere un solo padre, ma può avere più posizioni di comando. Per inserire un elemento dell'interfaccia utente in più posizioni, aggiungere un `CommandPlacement` \(elemento\) per ogni posizione.  
  
3.  Impostare il `guid` e `id` gli attributi di ogni `CommandPlacement` elemento al menu di hosting o gruppo, proprio come si farebbe per un `Parent` elemento. È inoltre possibile impostare il `priority` attributo per stabilire la posizione relativa di elemento dell'interfaccia utente.  
  
 È possibile combinare posizionamento dall'elemento padre e il posizionamento di comando. Tuttavia, per il set di comandi molto grandi, si consiglia di utilizzare solo il posizionamento del comando.  
  
### Aggiunta di comportamenti speciali  
 È possibile utilizzare [CommandFlag](../../extensibility/command-flag-element.md) elementi per modificare il comportamento di menu e comandi, ad esempio, per modificare l'aspetto e la visibilità. È inoltre possibile modificare quando un comando è visibile tramite [VisibilityConstraints](../../extensibility/visibilityconstraints-element.md), o aggiungere tasti di scelta rapida utilizzando [KeyBindings](../../extensibility/keybindings-element.md). Determinati tipi di menu e comandi già conoscere in modo specifico i comportamenti incorporati.  
  
##### Per aggiungere comportamenti speciali  
  
1.  Per rendere visibili solo in determinati contesti dell'interfaccia utente, ad esempio, un elemento dell'interfaccia utente quando viene caricata una soluzione, utilizzare i vincoli di visibilità.  
  
    1.  Dopo il `Commands` elemento, aggiungere un `VisibilityConstraints` elemento.  
  
    2.  Per ogni elemento dell'interfaccia utente per limitare, aggiungere un [VisibilityItem](../../extensibility/visibilityitem-element.md) elemento.  
  
    3.  Per ogni `VisibilityItem` elemento, impostare il `guid` e `id` gli attributi per il menu, gruppo, o comando e quindi impostare il `context` attributo nel contesto dell'interfaccia utente desiderato, come definito nel <xref:Microsoft.VisualStudio.Shell.Interop.UIContextGuids80> \(classe\). Per altre informazioni, vedere [Elemento VisibilityItem](../../extensibility/visibilityitem-element.md).  
  
2.  Per impostare la visibilità o la disponibilità di un elemento dell'interfaccia utente nel codice, utilizzare uno o più dei flag del comando seguente:  
  
    -   DefaultDisabled  
  
    -   DefaultInvisible  
  
    -   DynamicItemStart  
  
    -   DynamicVisibility  
  
    -   NoShowOnMenuController  
  
    -   NotInTBList  
  
     Per altre informazioni, vedere [Elemento di Flag di comando](../../extensibility/command-flag-element.md).  
  
3.  Per modificare come viene visualizzato un elemento o modificarne l'aspetto in modo dinamico, utilizzare uno o più dei flag del comando seguente:  
  
    -   AlwaysCreate  
  
    -   CommandWellOnly  
  
    -   DefaultDocked  
  
    -   DontCache  
  
    -   DynamicItemStart  
  
    -   FixMenuController  
  
    -   IconAndText  
  
    -   PICT  
  
    -   StretchHorizontally  
  
    -   TextMenuUseButton  
  
    -   TestoConsente di modificare  
  
    -   TextOnly  
  
     Per altre informazioni, vedere [Elemento di Flag di comando](../../extensibility/command-flag-element.md).  
  
4.  Per modificare un elemento reazioni quando riceve i comandi, utilizzare uno o più dei flag del comando seguente:  
  
    -   AllowParams  
  
    -   CaseSensitive  
  
    -   CommandWellOnly  
  
    -   Filtro tasti  
  
    -   NoAutoComplete  
  
    -   NoButtonCustomize  
  
    -   NoKeyCustomize  
  
    -   NoToolbarClose  
  
    -   PostExec  
  
    -   RouteToDocs  
  
    -   TextIsAnchorCommand  
  
     Per altre informazioni, vedere [Elemento di Flag di comando](../../extensibility/command-flag-element.md).  
  
5.  Per collegare dipendenti dal menu di scelta rapida a un menu o un elemento in un menu, aggiungere un carattere e commerciale \('& '\) nel `ButtonText` \(elemento\) per il menu o la voce di menu. Il carattere che segue la e commerciale è la scelta rapida da tastiera attiva quando viene aperto il menu padre.  
  
6.  Per collegare un'indipendente dal menu di scelta rapida a un comando, utilizzare [KeyBindings](../../extensibility/keybindings-element.md). Per altre informazioni, vedere [Elemento dell'oggetto KeyBinding](../../extensibility/keybinding-element.md).  
  
7.  Per localizzare il testo del menu, utilizzare il `LocCanonicalName` elemento. Per altre informazioni, vedere [Elemento di stringhe](../../extensibility/strings-element.md).  
  
 Alcuni tipi di menu e pulsante includono particolari funzionalità. Nella tabella seguente vengono descritti alcuni menu specializzato e tipi di pulsanti. Per altri tipi, vedere il `types` attributo descrizioni in [Elemento menu](../../extensibility/menu-element.md), [Elemento Button](../../extensibility/button-element.md), e [Elemento casella combinata](../../extensibility/combo-element.md).  
  
 Casella combinata  
 Una casella combinata è un elenco di riepilogo a discesa che può essere utilizzato in una barra degli strumenti. Per aggiungere caselle combinate all'interfaccia utente, creare un [casella combinata](../../extensibility/combos-element.md) elemento il `Commands` elemento. Aggiungere quindi il `Combos` elemento un `Combo` \(elemento\) per ogni casella combinata aggiungere.`Combo` gli elementi hanno gli stessi attributi e gli elementi figlio come `Button` elementi e dispongono inoltre di `DefaultWidth` e `idCommandList` gli attributi. Il `DefaultWidth` attributo imposta la larghezza in pixel e `idCommandList` attributo punti a un ID di comando che viene utilizzato per popolare la casella combinata. Per ulteriori informazioni, vedere il `Combo` la documentazione dell'elemento.  
  
 MenuController  
 Un controller di menu è un pulsante con una freccia accanto a esso. Facendo clic sulla freccia, viene visualizzato un elenco. Per aggiungere un controller di menu all'interfaccia utente, creare un `Menu` e impostare il relativo `type` attributo **MenuController** o **MenuControllerLatched**, in base al comportamento desiderato. Per popolare un controller di menu, impostarlo come elemento padre di un `Group` elemento. Il controller menu visualizzerà tutti gli elementi figlio di tale gruppo nel relativo elenco a discesa.  
  
## Vedere anche  
 [Estensione menu e comandi](../../extensibility/extending-menus-and-commands.md)   
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Riferimento allo Schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md)