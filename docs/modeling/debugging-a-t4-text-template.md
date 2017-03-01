---
title: Debug di un modello di testo T4 | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text templates, troubleshooting
- text templates, debugging
ms.assetid: 0877fdf2-20bf-42da-b3cc-4c5856b80821
caps.latest.revision: 28
author: alancameronwills
ms.author: awills
manager: douge
translation.priority.ht:
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
ms.openlocfilehash: 5b6cb4a83e6aa06f6b29987893232d8b6e203c56
ms.lasthandoff: 02/22/2017

---
# <a name="debugging-a-t4-text-template"></a>Debug di un modello di testo T4
È possibile impostare punti di interruzione nei modelli di testo. Per eseguire il debug di un modello di testo in fase di progettazione, salvare il file di modello di testo e quindi scegliere **Debug modello T4** il menu di scelta rapida del file in Esplora soluzioni. Per eseguire il debug di un modello di testo in fase di esecuzione, è sufficiente eseguire il debug l'applicazione a cui appartiene.  
  
 Per eseguire il debug di un modello di testo, è necessario comprendere i passaggi del processo di trasformazione di modello. Diversi tipi di errori possono verificarsi all'interno di ogni passaggio. I passaggi sono i seguenti.  
  
|Passaggio|Modello della fase di progettazione: quando si verifica|Modello della fase di esecuzione: quando si verifica|  
|----------|--------------------------------------------|-----------------------------------------|  
|Codice viene generato dal modello di testo.<br /><br /> Errori nelle direttive, o non corrispondente o disordered `<#…#>` tag.|Quando si salva il modello o richiamare la trasformazione di testo.|Quando si salva il modello o richiamare la trasformazione di testo.|  
|Codice generato viene compilato.<br /><br /> Errori di compilazione nel codice del modello.|Immediatamente dopo il passaggio precedente.|Con il codice dell'applicazione.|  
|Esecuzione del codice.<br /><br /> Errori di runtime nel codice del modello.|Immediatamente dopo il passaggio precedente.|Quando l'applicazione viene eseguita e richiama il codice del modello.|  
  
 Nella maggior parte dei casi, i numeri di riga nel codice del modello sono espressi in segnalazione errori. Quando il report di errore fa riferimento a un nome di file temporaneo, la causa è una parentesi non corrispondente nel codice del modello di testo.  
  
 È possibile impostare punti di interruzione nei modelli di testo e il debug come di consueto.  
  
## <a name="common-errors-and-fixes"></a>Errori comuni e le correzioni  
 Nella tabella seguente sono elencati gli errori più comuni e le relative correzioni.  
  
|Messaggio di errore|Descrizione|Soluzione|  
|-------------------|-----------------|--------------|  
|Impossibile caricare la classe base '{0}' da cui eredita la classe Transformation.|Si verifica se non è possibile trovare la classe base specificata nel `inherits` parametro in una direttiva del modello. Il messaggio fornisce il numero di riga della direttiva template.|Assicurarsi che la classe specificata esista e che l'assembly che esiste in è specificato in una direttiva assembly.|  
|Impossibile risolvere il testo di inclusione per il file: {0}|Si verifica quando non è possibile trovare un modello incluso. Il messaggio fornisce il nome del file di inclusione richiesto.|Assicurarsi che il percorso del file è relativo al percorso del modello originale, o che il file sia in un percorso a cui è registrato con l'host o che vi sia un percorso completo del file.|  
|Sono stati generati errori durante l'inizializzazione dell'oggetto di trasformazione. La trasformazione non verrà eseguita.|Si verifica quando Initialize della classe di trasformazione non è riuscito o ha restituito false.|Il codice nella funzione Initialize () viene fornito dalla classe di base di trasformazione specificata nella \<#@template#> direttiva e dai processori di direttiva. L'errore che ha causato initialize probabilmente esito negativo è nell'elenco degli errori. Esaminare il motivo dell'errore. È possibile esaminare il codice generato per Initialize () seguendo le procedure per eseguire il debug di un modello.|  
|L'assembly '{0}' per il processore di direttiva '\ {1 \' non è stato concesso il set di autorizzazioni FullTrust. Sono consentiti solo assembly attendibili per fornire i processori di direttiva. Questo processore di direttiva non potranno essere caricato.|Si verifica quando il sistema non concede autorizzazioni FullTrust a un assembly contenente un processore di direttiva. Il messaggio fornisce il nome dell'assembly e il nome del processore di direttiva.|Assicurarsi di utilizzare solo assembly attendibili nel computer locale.|  
|Il percorso '{0}' deve essere locale al computer o parte dell'area attendibile.|Si verifica quando una direttiva o direttiva dell'assembly fa riferimento a un file non presenti nel computer locale o nella zona attendibile della rete.|Assicurarsi che la directory in cui la direttiva o direttive dell'assembly si trovano nell'area attendibile. È possibile aggiungere una directory di rete all'area attendibile tramite Internet Explorer.|  
|Più errori di sintassi, ad esempio "Non valido token ' catch'" o "uno spazio dei nomi non può contenere direttamente membri"|Troppe parentesi graffe di chiusura nel codice del modello. Il compilatore lo confonde con il codice di generazione standard.|Controllare il numero di parentesi graffe e le parentesi all'interno di delimitatori di codice di chiusura.|  
|Cicli o istruzioni condizionali non compilato o eseguito correttamente. Ad esempio: `<#if (i>10)#> Number is: <#= i #>`.<br /><br /> Questo codice genera sempre il valore di è. Solo "numero:" condizionale.|In c#, utilizzare sempre le parentesi graffe per racchiudere i blocchi di testo incorporati nelle istruzioni di controllo.|Aggiungere le parentesi graffe: `<#if (i>10) { #>    Number is: <#= i #><# } #>`.|  
|"Espressione troppo complessa" durante l'elaborazione di un modello di progettazione o la compilazione di un modello di runtime (pre-elaborato).<br /><br /> [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]smette di funzionare quando si tenta di controllare il codice generato da un modello di runtime.|Blocco di testo è troppo lungo. Blocchi di testo T4 converte un'espressione di concatenazione di stringa, con una stringa letterale per ogni riga del modello. Blocchi di testo molto lunghi possono oltrepassare i limiti di dimensioni del compilatore.|Suddividere il blocco di testo lungo con un blocco di espressione, ad esempio:<br /><br /> `<#= "" #>`|  
  
## <a name="warning-descriptions-and-fixes"></a>Correzioni e le descrizioni di avviso  
 Nella tabella seguente sono elencati gli avvisi più comuni con le relative correzioni, se disponibile.  
  
|Messaggio di avviso|Descrizione|Soluzione|  
|---------------------|-----------------|--------------|  
|Il caricamento del file di inclusione '{0}' ha restituito una stringa null o vuota.|Si verifica se un file di modello di testo incluso è vuoto. Il messaggio contiene il nome del file del file incluso.|Rimuovere la direttiva di inclusione o assicurarsi che il file contiene alcuni contenuti.|  
|Compilazione trasformazione:|Antepone questa stringa a tutti gli errori o avvisi provenienti dal compilatore durante la compilazione della trasformazione. Questa stringa indica che il compilatore genera un errore o avviso.|Se si dispone di un problema di individuazione della DLL, potrebbe essere necessario fornire il percorso completo o un nome sicuro completo se la DLL nella Global Assembly Cache.|  
|Il parametro '{0}' esiste già nella direttiva. Il parametro duplicato verrà ignorato.|Si verifica quando un parametro è specificato più volte in una direttiva. Il messaggio fornisce il nome del parametro e il numero di riga della direttiva.|Rimuovere la specifica del parametro duplicato.|  
|Si è verificato un errore durante il caricamento di file di inclusione '{0}'. La direttiva di inclusione verrà ignorata.|Si verifica quando non è possibile trovare un file specificato un `include` (direttiva). Il messaggio fornisce il nome del file e il numero di riga della direttiva.|Assicurarsi che il file di inclusione è presente nella stessa directory del file di modello di testo originale o in una directory di inclusione che sono registrate con l'host.|  
|Classe di base non valida specificata per la classe della trasformazione. La classe di base deve derivare da TextTransformation.|Si verifica quando il `inherits` parametro in una direttiva del modello specifica una classe che eredita da `TextTransformation`. Il messaggio fornisce il numero di riga della direttiva template.|Specificare una classe che deriva da `TextTransformation`.|  
|Impostazioni cultura non valida è stata specificata nella direttiva 'template'. Le impostazioni cultura deve essere nel formato "xx-XX". Verranno utilizzate le impostazioni cultura invarianti.|Si verifica quando il parametro delle impostazioni cultura in una direttiva del modello è stato specificato correttamente. Il messaggio fornisce il numero di riga della direttiva template.|Modificare il parametro delle impostazioni cultura in una lingua valida nel formato "xx-XX".|  
|È stato specificato un valore di debug non valido '{0}' nella direttiva del modello. Il valore di debug deve essere "true" o "false". Verrà utilizzato il valore predefinito "false".|Si verifica quando il `debug` parametro in una direttiva del modello è stato specificato correttamente. Il messaggio fornisce il numero di riga della direttiva template.|Impostare il parametro debug su "true" o "false".|  
|Un valore HostSpecific non valido '{0}' è stato specificato nella direttiva del modello. Il valore di HostSpecific deve essere "true" o "false". Verrà utilizzato il valore predefinito "false".|Si verifica quando il parametro host specifico in un `template` direttiva è stata specificata correttamente. Il messaggio fornisce il numero di riga della direttiva template.|Impostare il parametro specifica dell'host su "true" o "false".|  
|Un linguaggio non valido '{0}' è stato specificato nella direttiva 'template'. La lingua deve essere "C#" o "VB". Verrà utilizzato il valore predefinito di "C#".|Si verifica quando viene specificata una lingua non supportata nel `template` (direttiva). Sono consentiti solo "C#" o "VB" (distinzione tra maiuscole e minuscole). Il messaggio fornisce il numero di riga della direttiva template.|Impostare il `language` parametro nella direttiva del modello "C#" o "VB".|  
|Nel modello sono state trovate più direttive di output. Tutti tranne il primo verranno ignorati.|Si verifica quando più `output` direttive vengono specificate in un file modello. Il messaggio fornisce il numero di riga della direttiva output duplicati.|Rimuovi duplicati `output` direttive.|  
|Nel modello sono state trovate più direttive di modello. Tutti tranne il primo verranno ignorati. Più parametri alla direttiva del modello devono essere specificati all'interno di una direttiva template.|Si verifica se si specificano più `template` direttive all'interno di un file di modello di testo (inclusi i file inclusi). Il messaggio fornisce il numero di riga della direttiva template duplicati.|Aggregare i diversi `template` direttive in un unico `template` (direttiva).|  
|Per una direttiva denominata '{0}' è stato specificato alcun processore. La direttiva verrà ignorata.|Si verifica se si specifica un `custom` (direttiva), ma non forniscono un `processor` attributo. Il messaggio fornisce il nome della direttiva e il numero di riga.|Fornire un `processor` con il nome dell'attributo di `directive` processore di direttiva.|  
|Impossibile trovare un processore denominato '{0}' per la direttiva denominata '\ {1 \'. La direttiva verrà ignorata.|Si verifica quando il sistema non sono disponibili le `directive` processore specificato all'interno di un `custom` (direttiva). Il messaggio contiene il nome della direttiva, nome del processore e il numero di riga della direttiva.|Impostare il `processor` attributo nella direttiva per il nome del processore di direttiva.|  
|Un parametro obbligatorio '{0}' per la direttiva '\ {1 \' non trovato. La direttiva verrà ignorata.|Si verifica quando il sistema non fornisce un parametro di direttiva obbligatorio. Il messaggio contiene il nome del parametro mancante, il nome della direttiva e il numero di riga.|Fornire il parametro mancante.|  
|Il processore denominato '{0}' non supporta la direttiva denominata '\ {1 \'. La direttiva verrà ignorata.|Si verifica quando un processore di direttiva non supporta una direttiva. Il messaggio fornisce il numero di riga e il nome della direttiva che insieme al nome del processore di direttiva.|Correggere il nome della direttiva.|  
|La direttiva di inclusione per il file '{0}' causa un ciclo infinito.|Se le istruzioni di inclusione circolare visualizzata vengono specificati (ad esempio, il file include file B, che include il file).|Non si specifica circolare le istruzioni di inclusione.|  
|Esecuzione trasformazione:|Antepone questa stringa per tutti gli errori o avvisi generati durante l'esecuzione della trasformazione.|Non applicabile.|  
|Un tag di inizio o fine imprevisto trovato all'interno di un blocco. Assicurarsi che non sia stato digitato erroneamente un tag di inizio o fine, e che non è necessario alcun blocco annidato nel modello.|Visualizzato quando si dispone di un'eccezione imprevista \<# o #>. Ovvero, se si dispone di un \<# dopo un altro tag aperto che non è stato chiuso o si dispone di un simbolo #> quando non vi è alcun tag aperto prima. Il messaggio fornisce il numero di riga del tag non corrispondenti.|Rimuovere il tag di inizio o fine non corrispondente o utilizzare un carattere di escape.|  
|Una direttiva è stata specificata in un formato non corretto. La direttiva verrà ignorata. Specificare la direttiva nel formato`<#@ name [parametername="parametervalue"]*  #>`|Se non si specifica una direttiva nel formato corretto, visualizzato dal parser. Il messaggio fornisce il numero di riga della direttiva non corretto.|Assicurarsi che tutte le direttive siano nel formato `<#@ name [parametername="parametervalue"]*  #>`. Per ulteriori informazioni, vedere [direttive di modello di testo T4](../modeling/t4-text-template-directives.md).|  
|Impossibile caricare l'Assembly '{0}' per il processore di direttiva registrato '\ {1 \'<br /><br /> {2}|Si verifica quando un processore di direttiva non è stato caricato dall'host. Il messaggio identifica l'assembly fornito per il processore di direttiva e il nome del processore di direttiva.|Verificare che il processore di direttiva sia registrato correttamente e che l'assembly sia presente.|  
|Impossibile trovare il tipo '{0}' nell'Assembly '\ {1 \' per processore di direttiva registrato '\ {2'<br /><br /> {3}|Si verifica quando un tipo di processore di direttiva potrebbe non essere caricato dall'assembly. Il messaggio contiene il nome del tipo, assembly e processore di direttiva.|Vshost Trova informazioni processore di direttiva (nome, assembly e tipo) nel Registro di sistema. Verificare che il processore di direttiva sia registrato correttamente e che il tipo sia presente nell'assembly.|  
|Problema durante il caricamento dell'assembly '{0}'|Si verifica quando si verifica un problema di caricamento di un assembly. Il messaggio fornisce il nome dell'assembly.|È possibile specificare gli assembly da caricare in \<@# assembly #> direttive e dai processori di direttiva. Il messaggio di errore che segue questa stringa deve fornire i dati più sul motivo per cui non è riuscito il caricamento dell'assembly.|  
|Si è verificato un problema nella creazione e inizializzazione del processore di direttiva denominato '\ {1 \'. Il tipo del processore è {0}. La direttiva verrà ignorata.|Si verifica quando il sistema Impossibile creare o inizializzare un processore di direttiva. Il messaggio contiene il numero di riga e il nome della direttiva e il tipo di processore.|Assicurarsi che si utilizza il processore di direttiva corretto e che il processore di direttiva dispone di un costruttore predefinito pubblico. In caso contrario, utilizzare le opzioni di debug per scoprire il motivo per cui il metodo Initialize () del processore di direttiva è. Per ulteriori informazioni, vedere [risoluzione dei problemi di modelli di testo](../modeling/debugging-a-t4-text-template.md).|  
|È stata generata un'eccezione durante l'elaborazione di una direttiva denominata '{0}'.|Si verifica quando un processore di direttiva genera un'eccezione durante l'elaborazione di una direttiva.|Assicurarsi che i parametri per il processore di direttiva siano corretti.|  
|L'host ha generato un'eccezione durante il tentativo di risolvere il riferimento all'assembly '{0}'.|Si verifica quando l'host genera un'eccezione durante il tentativo di risolvere un riferimento all'assembly. Il messaggio fornisce l'assembly fare riferimento a stringa.|Assembly riferimenti provenire da \<@# assembly #> direttive e dai processori di direttiva. Assicurarsi che il parametro 'name' fornito nel parametro dell'assembly sia corretto.|  
|Tenta di specificare il valore \ {1 \ non supportato '{0}' per direttiva \ {2|Si verifica con RequiresProvidesDirectiveProcessor (tutti i processori di direttiva generati derivano da essa), quando si fornisce un supportato argomento richiede o fornisce.|Assicurarsi che i nomi in name = 'value' fornite in coppie di richiede e fornisce i parametri siano corretti.|
