---
title: Come package VS aggiungere elementi dell&quot;interfaccia utente | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user interfaces, adding elements
- UI element design [Visual Studio SDK], VSPackages
- VSPackages, contributing UI elements
ms.assetid: abc5d9d9-b267-48a1-92ad-75fbf2f4c1b9
caps.latest.revision: 60
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 6bf44a2b1fa029753c4b3c00f911070a2132bb75
ms.lasthandoff: 02/22/2017

---
# <a name="how-vspackages-add-user-interface-elements"></a>Come package VS aggiungere elementi dell'interfaccia utente
Un pacchetto Visual Studio è possibile aggiungere elementi dell'interfaccia utente, ad esempio, menu, barre degli strumenti e finestre degli strumenti di Visual Studio tramite il file vsct.  
  
 È possibile trovare linee guida per gli elementi dell'interfaccia utente in [linee guida esperienza utente di Visual Studio](../../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  
  
## <a name="the-visual-studio-command-table-architecture"></a>L'architettura di tabella comandi di Visual Studio  
 Come accennato, l'architettura di tabella comandi supporta principi architetturali sopra. Di seguito sono riportati i principi alla base di astrazioni, strutture di dati e gli strumenti di architettura di tabella il comando:  
  
-   Esistono tre tipi di elementi di base: menu, comandi e gruppi. Menu possono essere esposti nell'interfaccia utente come menu, sottomenu, barre degli strumenti o finestre degli strumenti. I comandi sono routine che l'utente è possibile eseguire nell'IDE e possono essere esposti come voci di menu, pulsanti, caselle di riepilogo o altri controlli. I gruppi sono contenitori per i menu e comandi.  
  
-   Ogni elemento è specificato da una definizione che descrive l'elemento, la priorità rispetto ad altri elementi e i flag che modificano il comportamento.  
  
-   Ogni elemento è una posizione che descrive l'elemento padre dell'elemento. Un elemento può contenere più elementi padre, in modo da poter essere visualizzati in più posizioni nell'interfaccia utente.  
  
     Ogni comando deve avere un gruppo padre, anche se è l'unico elemento figlio in quel gruppo. Ogni menu standard deve inoltre disporre di un gruppo padre. Barre degli strumenti e finestre degli strumenti funzionano come i propri elementi padre. Un gruppo può avere come padre barra dei menu di Visual Studio principale, o qualsiasi menu, barra degli strumenti o finestra degli strumenti.  
  
### <a name="how-items-are-defined"></a>Come sono definiti gli elementi  
 . File Vsct sono formattati in XML. Un file. vsct definisce gli elementi dell'interfaccia utente per un pacchetto e determina dove gli elementi vengono visualizzati nell'IDE. Ogni menu, un gruppo o un comando nel pacchetto viene assegnato un GUID e ID nel `Symbols` sezione. Nel resto di vsct il file, ogni menu, comandi e gruppo è identificato dalla combinazione di GUID e ID. Nell'esempio seguente viene illustrato un tipico `Symbols` sezione generato mediante il modello di pacchetto di Visual Studio quando un **comando di Menu** selezionati nel modello.  
  
```xml  
<Symbols>  
  <!-- This is the package guid. -->  
  <GuidSymbol name="guidMenuTextPkg" value="{b1253bc6-d266-402b-89e7-5e3d3b22c746}" />  
  
  <!-- This is the guid used to group the menu commands together -->  
  <GuidSymbol name="guidMenuTextCmdSet" value="{a633d4e4-6c65-4436-a138-1abeba7c9a69}">  
  
    <IDSymbol name="MyMenuGroup" value="0x1020" />  
    <IDSymbol name="cmdidMyCommand" value="0x0100" />  
  </GuidSymbol>  
  
  <GuidSymbol name="guidImages" value="{53323d9a-972d-4671-bb5b-9e418480922f}" >  
    <IDSymbol name="bmpPic1" value="1" />  
    <IDSymbol name="bmpPic2" value="2" />  
    <IDSymbol name="bmpPicSearch" value="3" />  
    <IDSymbol name="bmpPicX" value="4" />  
    <IDSymbol name="bmpPicArrows" value="5" />  
  </GuidSymbol>  
</Symbols>  
```  
  
 Elemento di livello principale di `Symbols` sezione è di [GuidSymbol elemento](../../extensibility/guidsymbol-element.md). `GuidSymbol`elementi di mapping dei nomi per i GUID vengono utilizzati dall'IDE per identificare i pacchetti e i relativi componenti.  
  
> [!NOTE]
>  I GUID vengono generati automaticamente dal pacchetto di modello di Visual Studio. È inoltre possibile creare un GUID univoco facendo **Crea GUID** sul **strumenti** menu.  
  
 Il primo `GuidSymbol` elemento "guid [PackageName] Pkg", è il GUID del pacchetto stesso. Questo è il GUID utilizzato da Visual Studio per caricare il pacchetto. In genere, non dispone di elementi figlio.  
  
 Per convenzione, i menu e comandi sono raggruppati in un secondo `GuidSymbol` elemento "guid [PackageName] CmdSet", e le bitmap sono in un terzo `GuidSymbol` elemento, "guidImages". Non è necessario seguire questa convenzione, ma ogni menu, gruppo, comando e bitmap deve essere un figlio di un `GuidSymbol` elemento.  
  
 Nella seconda `GuidSymbol` elemento che rappresenta il set di comandi di pacchetto, sono diversi `IDSymbol` elementi. Ogni [IDSymbol elemento](../../extensibility/idsymbol-element.md) associa un nome a un valore numerico e può rappresentare un menu, un gruppo o un comando che fa parte del set di comandi. Il `IDSymbol` elementi nel terzo `GuidSymbol` elemento rappresentano bitmap che possono essere utilizzate come icone per i comandi. Poiché le coppie GUID o ID devono essere univoche in un'applicazione, non due elementi figlio dello stesso `GuidSymbol` elemento può avere lo stesso valore.  
  
### <a name="menus-groups-and-commands"></a>Menu, gruppi e comandi  
 Quando un menu, gruppo o il comando ha un GUID e ID, può essere aggiunto all'IDE. Ogni elemento dell'interfaccia utente deve disporre di quanto segue:  
  
-   Oggetto `guid` attributo che corrisponde al nome del `GuidSymbol` elementi definiti sotto l'elemento dell'interfaccia utente.  
  
-   Un `id` attributo che corrisponde al nome dell'oggetto associato `IDSymbol` elemento.  
  
     Insieme, il `guid` e `id` attributi costituiscono la *firma* dell'elemento dell'interfaccia utente.  
  
-   Oggetto `priority` attributo che determina il posizionamento dell'elemento dell'interfaccia utente nel relativo menu padre o un gruppo.  
  
-   Oggetto [elemento padre](../../extensibility/parent-element.md) con `guid` e `id` gli attributi che specificano la firma del menu padre o del gruppo.  
  
#### <a name="menus"></a>Menu  
 Le voci di menu viene definito come un [elemento Menu](../../extensibility/menu-element.md) nel `Menus` sezione. Menu necessario `guid`, `id`, e `priority` attributi e un `Parent` elemento e anche i seguenti attributi aggiuntivi e gli elementi figlio:  
  
-   Oggetto `type` attributo che specifica se il menu verrà visualizzato nell'IDE come un tipo di menu o una barra degli strumenti.  
  
-   Un [elemento stringhe](../../extensibility/strings-element.md) che contiene un [elemento ButtonText](../../extensibility/buttontext-element.md), che specifica il titolo del menu di scelta nell'IDE e un [CommandName elemento](../../extensibility/commandname-element.md), che specifica il nome che viene utilizzato per il **comando** finestra per accedere al menu.  
  
-   Flag facoltativi. Oggetto [comando Flag elemento](../../extensibility/command-flag-element.md) possibile che venga visualizzato in una definizione di menu per modificare l'aspetto o comportamento nell'IDE.  
  
 Ogni `Menu` elemento deve avere un gruppo padre, a meno che non è un elemento, ad esempio una barra degli strumenti ancorato. Un alloggiamento di espansione è il proprio padre. Per ulteriori informazioni su menu e i valori per il `type` attributo, vedere il [elemento Menu](../../extensibility/menu-element.md) documentazione.  
  
 Nell'esempio seguente viene visualizzato un menu che viene visualizzato accanto alla barra dei menu di Visual Studio, il **strumenti** menu.  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet"  
id="TopLevelMenu" priority="0x700" type="Menu">  
  <Parent guid="guidSHLMainMenu"  
          id="IDG_VS_MM_TOOLSADDINS" />  
  <Strings>  
    <ButtonText>TestMenu</ButtonText>  
    <CommandName>TestMenu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="groups"></a>Gruppi  
 Un gruppo è un elemento definito nel `Groups` sezione del file vsct. I gruppi sono semplicemente contenitori. Non presenti nell'IDE, ad eccezione di una linea divisoria netta in un menu. Pertanto, un [elemento gruppo](../../extensibility/group-element.md) viene definito solo per la firma, alla priorità e padre.  
  
 Un gruppo può avere un menu o un altro gruppo di se stesso come padre. Tuttavia, l'elemento padre è in genere il menu o la barra degli strumenti. Il menu nell'esempio precedente è un figlio di `IDG_VS_MM_TOOLSADDINS` gruppo e tale gruppo è un elemento figlio della barra dei menu di Visual Studio. Nell'esempio seguente il gruppo è un figlio del menu di scelta nell'esempio precedente.  
  
```  
 <Group guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"  
priority="0x0600">  
   <Parent guid="guidTopLevelMenuCmdSet" id="TopLevelMenu"/>  
 </Group>  
```  
  
 Poiché fa parte di un menu, questo gruppo conterrà in genere i comandi. Tuttavia, potrebbe contenere anche altri menu. Si tratta di come sono definiti i sottomenu, come illustrato nell'esempio seguente.  
  
```xml  
<Menu guid="guidTopLevelMenuCmdSet" id="SubMenu"  
priority="0x0100" type="Menu">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup"/>  
  <Strings>  
    <ButtonText>Sub Menu</ButtonText>  
    <CommandName>Sub Menu</CommandName>  
  </Strings>  
</Menu>  
```  
  
#### <a name="commands"></a>Comandi:  
 Un comando che viene fornito per l'IDE è definito come un [elemento Button](../../extensibility/button-element.md) o [elemento combinata](../../extensibility/combo-element.md). Per essere visualizzati in un menu o una barra degli strumenti, il comando deve avere un gruppo padre.  
  
##### <a name="buttons"></a>Pulsanti  
 I pulsanti sono definiti nel `Buttons` sezione. Una voce di menu, pulsante o altro elemento che un utente fa clic per eseguire un singolo comando viene considerato un pulsante. Alcuni tipi di pulsanti possono anche includere funzionalità di elenco. I pulsanti hanno corrispondono a quelle richieste e gli attributi facoltativi che dispongono di menu, e può avere un [elemento Icon](../../extensibility/icon-element.md) che specifica il GUID e l'ID della bitmap che rappresenta il pulsante nell'IDE. Per ulteriori informazioni sui pulsanti e i relativi attributi, vedere il [elemento pulsanti](../../extensibility/buttons-element.md) documentazione.  
  
 Il pulsante nell'esempio seguente è un figlio del gruppo nell'esempio precedente e verrà visualizzato nell'IDE come voce di menu nel menu del padre di tale gruppo.  
  
```  
<Button guid="guidTopLevelMenuCmdSet" id="cmdidTestCommand" priority="0x0100" type="Button">  
  <Parent guid="guidTopLevelMenuCmdSet" id="MyMenuGroup" />  
  <Icon guid="guidImages" id="bmpPic1" />  
  <Strings>  
    <CommandName>cmdidTestCommand</CommandName>  
    <ButtonText>Test Command</ButtonText>  
  </Strings>  
</Button>  
```  
  
##### <a name="combos"></a>Casella combinata  
 Casella combinata è definiti nel `Combos` sezione. Ogni `Combo` elemento rappresenta una casella di riepilogo a discesa nell'IDE. La casella di riepilogo può essere o non accessibile in scrittura da parte degli utenti, a seconda del valore di `type` attributo della casella combinata. Casella combinata è gli stessi elementi e comportamento che i pulsanti sono e può avere i seguenti attributi aggiuntivi:  
  
-   Oggetto `defaultWidth` attributo che specifica la larghezza in pixel.  
  
-   Un `idCommandList` attributo che specifica un elenco che contiene gli elementi che vengono visualizzati nella casella di riepilogo. Nell'elenco di comandi deve essere dichiarato nello stesso `GuidSymbol` nodo che contiene la casella combinata.  
  
 Nell'esempio seguente definisce un elemento casella combinata.  
  
```xml  
<Combos>  
  <Combo guid="guidFirstToolWinCmdSet"  
         id="cmdidWindowsMediaFilename"  
         priority="0x0100" type="DynamicCombo"  
         idCommandList="cmdidWindowsMediaFilenameGetList"  
         defaultWidth="130">  
    <Parent guid="guidFirstToolWinCmdSet"  
            id="ToolbarGroupID" />  
    <CommandFlag>IconAndText</CommandFlag>  
    <CommandFlag>CommandWellOnly</CommandFlag>  
    <CommandFlag>StretchHorizontally</CommandFlag>  
    <Strings>  
      <CommandName>Filename</CommandName>  
      <ButtonText>Enter a Filename</ButtonText>  
    </Strings>  
  </Combo>  
</Combos>  
```  
  
##### <a name="bitmaps"></a>Bitmap  
 I comandi che verranno visualizzati insieme a un'icona devono includere un `Icon` elemento che fa riferimento a una bitmap utilizzando il GUID e ID. Ogni bitmap viene definito come un [elemento Bitmap](../../extensibility/bitmap-element.md) nel `Bitmaps` sezione. Gli unici necessari gli attributi per un `Bitmap` definizione sono `guid` e `href`, che punta al file di origine. Se il file di origine è un elenco di risorse, un **usedList** attributo è inoltre necessario, per elencare le immagini disponibili nell'elenco. Per ulteriori informazioni, vedere il [elemento Bitmap](../../extensibility/bitmap-element.md) documentazione.  
  
### <a name="parenting"></a>Relazione padre-figlio  
 Le regole seguenti determinano come un elemento può chiamare un altro elemento del relativo oggetto padre.  
  
|Elemento|Definite in questa sezione della tabella di comando|Può essere contenuto (come un elemento padre o dalla posizione nel `CommandPlacements` sezione o entrambi)|Può contenere (definito per un elemento padre)|  
|-------------|--------------------------------------------------|---------------------------------------------------------------------------------------------------|---------------------------------------------|  
|Gruppo|[Groups-elemento](../../extensibility/groups-element.md), l'IDE, altri package VS|Un menu, un gruppo, l'elemento stesso|Menu, gruppi e comandi|  
|Menu|[Elemento menu](../../extensibility/menus-element.md), l'IDE, altri package VS|1 per *n* gruppi|da&0; a *n* gruppi|  
|ToolBar|[Elemento menu](../../extensibility/menus-element.md), l'IDE, altri package VS|L'elemento stesso|da&0; a *n* gruppi|  
|MenuItem|[I pulsanti elemento](../../extensibility/buttons-element.md), l'IDE, altri package VS|1 per *n* gruppi, l'elemento stesso|-0 per *n* gruppi|  
|Pulsante|[I pulsanti elemento](../../extensibility/buttons-element.md), l'IDE, altri package VS|1 per *n* gruppi, l'elemento stesso||  
|Casella combinata|[Elemento casella combinata](../../extensibility/combos-element.md), l'IDE, altri package VS|1 per *n* gruppi, l'elemento stesso||  
  
### <a name="menu-command-and-group-placement"></a>Menu, comandi e posizionamento del gruppo  
 Un menu, un gruppo o un comando può apparire in più di una posizione nell'IDE. Per un elemento venga visualizzato in più posizioni, deve essere aggiunto per il `CommandPlacements` sezione come un [CommandPlacement elemento](../../extensibility/commandplacement-element.md). Qualsiasi menu, un gruppo o un comando può essere aggiunto come una posizione di comando. Tuttavia, le barre degli strumenti non può essere posizionate in questo modo perché non possono apparire in più posizioni sensibile al contesto.  
  
 Dispone di comandi nel modo `guid`, `id`, e `priority` gli attributi. Il GUID e ID devono corrispondere a quelli dell'elemento al quale è posizionato. Il `priority` attributo determina la posizione dell'elemento per quanto riguarda altri elementi. Quando l'IDE unisce due o più elementi che hanno la stessa priorità, le posizioni sono definiti, poiché l'IDE non garantisce che le risorse del pacchetto vengono letti nello stesso ordine ogni volta che il pacchetto viene compilato.  
  
 Se un menu o un gruppo viene visualizzato in più posizioni, tutti gli elementi figlio di tale menu o il gruppo verranno visualizzato in ogni istanza.  
  
## <a name="command-visibility-and-context"></a>Comando visibilità e il contesto  
 Quando sono installati più package VS, una moltitudine di menu, voci di menu e barre degli strumenti può confusioni nell'IDE. Per evitare questo problema, è possibile controllare la visibilità dei singoli elementi dell'interfaccia utente utilizzando *vincoli di visibilità* e i flag di comando.  
  
##### <a name="visibility-constraints"></a>Vincoli di visibilità  
 Un vincolo di visibilità viene impostato come un [VisibilityItem elemento](../../extensibility/visibilityitem-element.md) nel `VisibilityConstraints` sezione. Un vincolo di visibilità definisce i contesti dell'interfaccia utente specifici in cui l'elemento di destinazione è visibile. Un menu o un comando che è incluso in questa sezione è visibile solo quando uno dei contesti definiti è attivo. Se un menu o il comando non viene fatto riferimento in questa sezione, è sempre visibile per impostazione predefinita. In questa sezione non si applica ai gruppi.  
  
 `VisibilityItem`gli elementi devono avere tre attributi, come segue: il `guid` e `id` dell'elemento dell'interfaccia utente di destinazione, e `context`. Il `context` attributo specifica quando l'elemento di destinazione sarà visibile e accetta qualsiasi contesto dell'interfaccia utente valido come valore. Le costanti di contesto dell'interfaccia utente per Visual Studio sono membri di <xref:Microsoft.VisualStudio.VSConstants>classe.</xref:Microsoft.VisualStudio.VSConstants> Ogni `VisibilityItem` elemento può accettare il valore di un solo contesto. Per applicare un contesto di secondo, creare una seconda `VisibilityItem` elemento che punta all'elemento stesso, come illustrato nell'esempio seguente.  
  
```xml  
<VisibilityConstraints>  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasSingleProject" />  
  <VisibilityItem guid="guidSolutionToolbarCmdSet"  
        id="cmdidTestCmd"  
        context="UICONTEXT_SolutionHasMultipleProjects" />  
</VisibilityConstraints>  
```  
  
##### <a name="command-flags"></a>Flag di comando  
 I flag di comando seguenti possono influire sulla visibilità dei menu e comandi a che si applicano.  
  
 AlwaysCreate  
 Menu viene creato anche se non contiene né gruppi di pulsanti.  
  
 Valida per:`Menu`  
  
 CommandWellOnly  
 Applicare questo flag se il comando non viene visualizzato il menu di primo livello e si desidera renderlo disponibile per la personalizzazione di altre shell, ad esempio, associarlo a una chiave. Dopo aver installato il pacchetto Visual Studio, un utente può personalizzare questi comandi aprendo il **opzioni** la finestra di dialogo e quindi modificare la posizione di comando sotto il **ambiente tastiera** categoria. Non influisce sul posizionamento nel menu di scelta rapida, barre degli strumenti, i controller di menu o sottomenu.  
  
 Valida per: `Button`,`Combo`  
  
 DefaultDisabled  
 Per impostazione predefinita, il comando è disabilitato se il package VS che implementa il comando non è stato caricato o non è stato chiamato il metodo QueryStatus.  
  
 Valida per: `Button`,`Combo`  
  
 DefaultInvisible  
 Per impostazione predefinita, il comando è invisibile se il package VS che implementa il comando non è stato caricato o non è stato chiamato il metodo QueryStatus.  
  
 Deve essere combinato con il `DynamicVisibility` flag.  
  
 Valid for: `Button`, `Combo`,`Menu`  
  
 DynamicVisibility  
 La visibilità del comando può essere modificata utilizzando il metodo QueryStatus o un GUID che viene incluso nel contesto di `VisibilityConstraints` sezione.  
  
 Si applica ai comandi che vengono visualizzati nei menu, non sulle barre degli strumenti. Gli elementi di livello superiore della barra degli strumenti possono essere disabilitati, ma non nascosti quando il flag OLECMDF_INVISIBLE viene restituito dal metodo QueryStatus.  
  
 In un menu, questo flag indica inoltre che deve essere automaticamente nascosto quando i relativi membri sono nascosti. Questo flag viene in genere assegnato a sottomenu perché menu di primo livello dispone già di questo comportamento.  
  
 Deve essere combinato con il `DefaultInvisible` flag.  
  
 Valid for: `Button`, `Combo`,`Menu`  
  
 NoShowOnMenuController  
 Se un comando che include questo flag è posizionato su un controller di menu, il comando non viene visualizzato nell'elenco a discesa.  
  
 Valida per:`Button`  
  
 Per ulteriori informazioni sui flag di comando, vedere il [comando Flag elemento](../../extensibility/command-flag-element.md) documentazione.  
  
##### <a name="general-requirements"></a>Requisiti generali  
 Il comando è necessario passare la seguente serie di test prima che possa essere visualizzato e abilitato:  
  
-   Il comando è posizionato correttamente.  
  
-   Il `DefaultInvisible` non è impostato.  
  
-   Il menu padre o la barra degli strumenti è visibile.  
  
-   Il comando non è visibile a causa di una voce contesto il [VisibilityConstraints elemento](../../extensibility/visibilityconstraints-element.md) sezione.  
  
-   Codice di package VS che implementa il <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interfaccia consente di visualizzare e il comando.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> Nessun codice interfaccia intercettata e agire su di esso.  
  
-   Quando un utente sceglie il comando, questa diventa la procedura descritta in [Routing algoritmo](../../extensibility/internals/command-routing-algorithm.md).  
  
## <a name="calling-pre-defined-commands"></a>Chiamata di comandi predefiniti  
 Il [UsedCommands elemento](../../extensibility/usedcommands-element.md) consente di VS per accedere ai comandi che vengono fornite altre VSPackage o dall'IDE. A tale scopo, creare un [UsedCommand elemento](../../extensibility/usedcommand-element.md) con il GUID e ID del comando da utilizzare. Questo garantisce che il comando verrà caricato da Visual Studio, anche se non fa parte della configurazione di Visual Studio corrente. Per ulteriori informazioni, vedere [UsedCommand elemento](../../extensibility/usedcommand-element.md).  
  
## <a name="interface-element-appearance"></a>Aspetto di elemento di interfaccia  
 Considerazioni per la selezione e il posizionamento di elementi di comando sono i seguenti:  
  
-   [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]offre molti elementi dell'interfaccia utente che vengono visualizzati in modo diverso a seconda della posizione.  
  
-   Un elemento dell'interfaccia utente che viene definito mediante il `DefaultInvisible` flag non verrà visualizzato nell'IDE a meno che non è visualizzato dalla relativa implementazione VSPackage di uno il <xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>(metodo), o associata a un particolare contesto dell'interfaccia utente nel `VisibilityConstraints` sezione.</xref:EnvDTE.IDTCommandTarget.QueryStatus%2A>  
  
-   Potrebbe non essere visualizzato anche un comando posizionato correttamente. Ciò è perché l'IDE automaticamente nasconde o Visualizza alcuni comandi, a seconda delle interfacce VSPackage (o non abbia) implementato. Implementazione del VSPackage di alcuni, ad esempio, compilare interfacce cause relative alla compilazione menu elementi da visualizzare automaticamente.  
  
-   L'applicazione di `CommandWellOnly` flag nella definizione di elemento dell'interfaccia utente significa che il comando è possibile aggiungere solo dalla personalizzazione.  
  
-   I comandi possono essere disponibili solo in determinati contesti dell'interfaccia utente, ad esempio, solo quando una finestra di dialogo viene visualizzata quando l'IDE è in visualizzazione progettazione.  
  
-   Per generare alcuni elementi dell'interfaccia utente da visualizzare nell'IDE, è necessario implementare una o più interfacce o a scrivere il codice.  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione menu e comandi](../../extensibility/extending-menus-and-commands.md)
