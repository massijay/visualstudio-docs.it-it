---
title: Progettazione tabella comandi XML (. File Vsct) | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- VSCT files, designing
ms.assetid: bb87a322-bac4-4258-92bc-9a876f05d653
caps.latest.revision: 27
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
ms.openlocfilehash: 047c23f9571007870e6d4db50f4604713c0d7ea3
ms.lasthandoff: 02/22/2017

---
# <a name="designing-xml-command-table-vsct-files"></a>Progettazione tabella comandi XML (. File Vsct)
Un file di tabella (vsct) del comando XML descrive il layout e l'aspetto degli elementi di comando per un VSPackage. Gli elementi di comando includono pulsanti, caselle combinate, menu, barre degli strumenti e gruppi di elementi di comando. In questo argomento viene descritto XML file tabella di comando, come influiscono menu e voci di comando e su come crearli.  
  
## <a name="commands-menus-groups-and-the-vsct-file"></a>I comandi, menu, gruppi e il File. vsct  
 file. vsct organizzati in gruppi di comandi, menu e comandi. Tag XML nel file vsct rappresentano ognuno di questi elementi, insieme ad altri elementi associati, ad esempio pulsanti di comando, posizionamento del comando e bitmap.  
  
 Quando si crea un nuovo pacchetto eseguendo il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pacchetto modello, il modello genera un file vsct con gli elementi necessari per un comando di menu, una finestra degli strumenti o editor personalizzato, a seconda delle selezioni. Questo file. vsct può quindi essere modificato per soddisfare i requisiti di un pacchetto specifico. Per esempi su come modificare un file. vsct, vedere gli esempi in [estensione menu e comandi](../../extensibility/extending-menus-and-commands.md).  
  
 Per creare un file vuoto. vsct, vedere [procedura: creare una. File Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md). Una volta creata, aggiungere elementi XML, attributi e valori del file per descrivere il layout dell'elemento di comando. Per uno schema XML dettagliato, vedere il [riferimento allo Schema XML VSCT](../../extensibility/vsct-xml-schema-reference.md).  
  
## <a name="differences-between-ctc-and-vsct-files"></a>Differenze tra file .ctc e vsct  
 Mentre il significato di tag XML in un file vsct è le stesse quelli ora deprecata .ctc formato di file, l'implementazione è leggermente diversa.  
  
-   Il nuovo ** \<extern >** tag è in cui si fa riferimento altri file. h da compilare, ad esempio quelle per il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sulla barra degli strumenti.  
  
-   Mentre vsct file di supporto di **/ includono** istruzione, come file .ctc, anche una nuova funzionalità \< **importare >** elemento. La differenza è **/ includono** riporta **tutti** delle informazioni, ma \< **importare >** riporta solo i nomi.  
  
-   Mentre i file .ctc richiedono un file di intestazione in cui si definiscono le direttive del preprocessore, uno non è richiesto per i file. vsct. Invece inserire direttive nella tabella dei simboli, all'interno di ** \<simbolo >** elementi, nella parte inferiore del file vsct.  
  
-   funzionalità di file. vsct un ** \<annotazione >** tag, che consente di incorporare informazioni desiderato, ad esempio note o persino le immagini.  
  
-   I valori vengono archiviati come attributi dell'elemento.  
  
-   Flag di comando può essere archiviato singolarmente o in pila.  IntelliSense, tuttavia, non funziona sui flag di comando in pila. Per ulteriori informazioni sui flag di comando, vedere il [comando Flag elemento](../../extensibility/command-flag-element.md).  
  
-   È possibile specificare più tipi, ad esempio divisione negli elenchi a discesa, casella combinata e così via.  
  
-   I GUID non vengono convalidati.  
  
-   Ogni elemento dell'interfaccia utente è una stringa che rappresenta il testo che viene visualizzato con esso.  
  
-   Elemento padre è facoltativo. Se omesso, viene utilizzato il valore "Gruppo" sconosciuto".  
  
-   L'icona di argomento è facoltativa.  
  
-   La sezione bitmap, come un .ctc file, ad eccezione del fatto che è ora possibile specificare un nome di file tramite href che vengono spostate dal compilatore vsct.exe in fase di compilazione.  
  
-   ResID - ID della risorsa bitmap precedente può essere utilizzato e comunque funziona esattamente come i file .ctc.  
  
-   HRef, un nuovo metodo che consente di specificare un nome di file per la risorsa bitmap. Si presuppone che vengono utilizzati tutti, pertanto è possibile omettere la sezione utilizzata. Il compilatore cercherà innanzitutto le risorse locali per il file, quindi scegliere le condivisioni di rete e tutte le risorse definite dall'opzione /I.  
  
-   KeyBinding - Non è necessario specificare un emulatore. Se si specifica uno, il compilatore presuppone che l'editor e l'emulatore sono uguali.  
  
-   Keychord - è stato eliminato. Il nuovo formato è Key1, Mod1, Key2, Mod2.  È possibile specificare un carattere, esadecimale o costante VK.  
  
 Il nuovo compilatore, vsct.exe, compila i file .ctc sia vsct. Il compilatore ctc.exe precedente, tuttavia, verrà riconoscere né compilare file. vsct.  
  
 È possibile utilizzare il compilatore vsct.exe per convertire un file .cto esistente in un file vsct. Per ulteriori informazioni, vedere [procedura: creare una. File Vsct da un oggetto esistente. File CTO](../../misc/how-to-create-a-dot-vsct-file-from-an-existing-dot-cto-file.md).  
  
## <a name="the-vsct-file-elements"></a>Gli elementi del File. vsct  
 La tabella di comando include la gerarchia e gli elementi seguenti:  
  
 [Elemento CommandTable](../../extensibility/commandtable-element.md) : rappresenta tutti i comandi, i gruppi di menu e menu associati a VSPackage.  
  
 [Elemento extern](../../extensibility/extern-element.md) : fa riferimento a file esterni. h da unire con il file vsct.  
  
 [Includere l'elemento](../../extensibility/include-element.md) , fa riferimento a qualsiasi file di intestazione aggiuntivi (h) che si desidera compilare insieme ai file your.vsct. Un file. vsct può includere file con estensione h che contiene le costanti che definiscono i comandi, gruppi di menu e menu che fornisce l'IDE o un altro VSPackage.  
  
 [Comandi elemento](../../extensibility/commands-element.md) : rappresenta tutti i singoli comandi che possono essere eseguiti. Ogni comando presenta i seguenti quattro elementi figlio:  
  
 [Elemento menu](../../extensibility/menus-element.md) : rappresenta tutti i menu e barre degli strumenti in VSPackage. I menu sono contenitori per i gruppi di comandi.  
  
 [Groups-elemento](../../extensibility/groups-element.md) : rappresenta tutti i gruppi di VSPackage. I gruppi sono raccolte di singoli comandi.  
  
 [I pulsanti elemento](../../extensibility/buttons-element.md) : rappresenta tutti i pulsanti di comando e le voci di menu VSPackage. I pulsanti sono controlli visivi che possono essere associati con i comandi.  
  
 [Elemento bitmap](../../extensibility/bitmaps-element.md) -rappresenta tutte le bitmap per tutti i pulsanti in VSPackage. Le bitmap sono immagini che vengono visualizzate accanto a o sui pulsanti di comando, a seconda del contesto.  
  
 [Elemento CommandPlacements](../../extensibility/commandplacements-element.md) -indica altri percorsi in cui devono essere posizionati singoli comandi nei menu del VSPackage.  
  
 [Elemento VisibilityConstraints](../../extensibility/visibilityconstraints-element.md) : consente di specificare o meno un comando Visualizza affatto volte o solo in determinati contesti, ad esempio quando viene visualizzata una particolare finestra di dialogo o finestra. Menu e comandi che hanno un valore per questo elemento verranno visualizzato solo quando è attivo il contesto specificato. Il comportamento predefinito consiste nel visualizzare il comando in qualsiasi momento.  
  
 [Elemento KeyBindings](../../extensibility/keybindings-element.md) : specifica le associazioni di chiavi per i comandi. Vale a dire una o più combinazioni di tasti che è necessario tenere premute per eseguire il comando, ad esempio **CTRL + S**.  
  
 [Elemento UsedCommands](../../extensibility/usedcommands-element.md) -Informs il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ambiente anche se il comando specificato è implementato da altro codice, quando il package VS corrente è attivo, fornisce l'implementazione del comando.  
  
 `Symbols Element`: Contiene i nomi dei simboli e gli ID di GUID per tutti i comandi nel pacchetto.  
  
## <a name="vsct-file-design-guidelines"></a>. Indicazioni per la progettazione di File Vsct  
 Per progettare correttamente un file. vsct, seguire queste linee guida.  
  
-   Comandi possono essere inseriti solo in gruppi, gruppi possono essere inseriti solo nei menu e menu possono essere inseriti solo in gruppi. Solo i menu sono effettivamente visualizzati nell'IDE, gruppi e i comandi non sono.  
  
-   Sottomenu non possono essere assegnati direttamente a un menu, ma devono essere assegnati a un gruppo, che a sua volta viene assegnato a un menu.  
  
-   I comandi, sottomenu e gruppi possono essere assegnati a un gruppo padre o menu utilizzando il campo padre della loro definizione direttiva.  
  
-   Organizzazione di una tabella comando esclusivamente tramite i campi padre nelle direttive di ha un limite significativo. Le direttive che definiscono gli oggetti possono accettare un solo padre argomento.  
  
-   Riutilizzo di comandi, gruppi o sottomenu richiede l'utilizzo di una nuova direttiva per creare una nuova istanza dell'oggetto con il proprio `GUID:ID` coppia.  
  
-   Ogni `GUID:ID` coppia deve essere univoco. Riutilizzo di un comando, ad esempio, situato in un menu, una barra degli strumenti o in un menu di scelta rapida, viene gestito dal <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>interfaccia.</xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>  
  
-   Comandi e sottomenu possono essere assegnati anche a più gruppi e gruppi possono essere assegnati a più menu utilizzando il [elemento Commands](../../extensibility/commands-element.md).  
  
## <a name="vsct-file-notes"></a>. File Vsct note  
 Se si apportano modifiche in un file vsct dopo che è sia compilarlo e inserirlo in una DLL satellite native, è consigliabile eseguire **devenv.exe /setup /nosetupvstemplates**. Questa operazione forza specificate nel Registro di sistema sperimentale per essere letto nuovamente e il database interno che descrive le risorse di VSPackage [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] verrà ricompilata.  
  
 Durante lo sviluppo, è possibile che più progetti VSPackage essere creato e registrato nell'hive sperimentale del Registro di sistema che può provocare confusione confusione nell'IDE. Per risolvere questo problema, è possibile ripristinare l'hive sperimentale le impostazioni predefinite per rimuovere registrati tutti i package VS e le eventuali modifiche apportate all'IDE. Per ripristinare l'hive sperimentale, utilizzare lo strumento CreateExpInstance.exe fornito con Visual Studio SDK. È possibile trovare all'indirizzo  
  
 **% PROGRAMFILES (x86) %\Visual Studio \<versione > SDK\VisualStudioIntegration\Tools\Bin\CreateExpInstance.exe**  
  
 Eseguire lo strumento da riga di comando **CreateExpInstance /Reset**. Tenere presente che questo strumento consente di rimuovere dall'hive sperimentale i package VS registrato che normalmente non vengono installati con [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## <a name="see-also"></a>Vedere anche  
 [Estensione menu e comandi](../../extensibility/extending-menus-and-commands.md)
