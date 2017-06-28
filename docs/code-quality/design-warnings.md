---
title: "Avvisi di progettazione | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.designrules"
helpviewer_keywords: 
  - "avvisi di progettazione"
  - "avvisi dell'analisi del codice gestito, avvisi di progettazione"
  - "avvisi, progettazione"
ms.assetid: 34e65a18-560c-423f-814f-519089e318cf
caps.latest.revision: 25
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 25
---
# Avvisi di progettazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gli avvisi di progettazione supportano la conformità alle linee guida di progettazione di Microsoft .NET Framework.  
  
## In questa sezione  
  
|Regola|Descrizione|  
|------------|-----------------|  
|[CA1000: Non dichiarare membri statici su tipi generici](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Quando viene chiamato un membro statico di un tipo generico, è necessario specificare l'argomento di tipo.  Quando viene chiamato un membro di istanza generica che non supporta l'inferenza, è necessario specificare l'argomento di tipo relativo al membro.  In questi due casi, la sintassi necessaria per specificare l'argomento di tipo è diversa e può generare confusione.|  
|[CA1001: I tipi proprietari di campi Disposable devono essere Disposable](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|Una classe dichiara e implementa un campo di istanza di tipo System.IDisposable e la classe non implementa IDisposable.  Una classe che dichiara un campo IDisposable è indirettamente proprietaria di una risorsa non gestita e deve implementare l'interfaccia IDisposable.|  
|[CA1002: Non esporre elenchi generici](../code-quality/ca1002-do-not-expose-generic-lists.md)|System.Collections.Generic.List\<\(Of \<\(T\>\)\>\) è una generica raccolta progettata per le prestazioni, non per l'ereditarietà.  List, pertanto, non contiene membri virtuali.  Devono invece essere esposte le raccolte generiche che sono state progettate per l'ereditarietà.|  
|[Ca1003: Utilizzare istanze di gestori eventi generici](../code-quality/ca1003-use-generic-event-handler-instances.md)|Un tipo contiene un delegato che restituisce un tipo void, la cui firma contiene due parametri \(il primo è un oggetto e il secondo un tipo assegnabile a EventArgs\) e l'assembly che lo contiene è destinato a [!INCLUDE[dnprdnlong](../code-quality/includes/dnprdnlong_md.md)].|  
|[CA1004: I metodi generici devono fornire parametri di tipo](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|Per inferenza si intende la procedura con cui viene determinato l'argomento di tipo di un metodo generico in base al tipo di argomento passato al metodo, piuttosto che in base alla specifica esplicita dell'argomento di tipo.  Per consentire l'inferenza, la firma di parametro di un metodo generico deve includere un parametro dello stesso tipo del parametro di tipo relativo al metodo.  In tal caso non è necessario specificare l'argomento di tipo.  Quando si utilizza l'inferenza per tutti i parametri di tipo, la sintassi necessaria per chiamare metodi di istanza generici e non generici è identica. In questo modo si semplifica l'usabilità dei metodi generici.|  
|[CA1005: Evitare un uso eccessivo di parametri nei tipi generici](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Quanto più è alto il numero di parametri di tipo contenuti, maggiore è la difficoltà di sapere e ricordare cosa rappresenta ciascun parametro.  È in genere ovvio con un parametro del tipo, come in List\<T\> e in alcuni casi con due parametri del tipo, come in Dictionary\<TKey, TValue\>.  Tuttavia, se il numero dei parametri di tipo è superiore a due, il livello di difficoltà sarà troppo elevato per la maggior parte degli utenti.|  
|[CA1006: Non annidare tipi generici nelle firme dei membri](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Un argomento di tipo annidato è un argomento di tipo che è anche un tipo generico.  Per chiamare un membro la cui firma contiene un argomento di tipo annidato, l'utente deve creare un'istanza su un tipo generico e passare il tipo al costruttore di un secondo tipo generico.  La sintassi e la procedura necessarie sono complesse ed è opportuno evitarle.|  
|[CA1007: Utilizzare generics dove appropriato](../code-quality/ca1007-use-generics-where-appropriate.md)|Un metodo visibile esternamente contiene un parametro di riferimento di tipo System.Object.  L'utilizzo di un metodo generico consente di passare al metodo tutti i tipi soggetti a vincoli senza prima eseguire il cast del tipo al tipo del parametro di riferimento.|  
|[CA1008: Gli enum devono avere valore zero](../code-quality/ca1008-enums-should-have-zero-value.md)|Il valore predefinito di un'enumerazione non inizializzata, come altri tipi di valore, è zero.  Un'enumerazione senza attributi flag definisce un membro utilizzando il valore zero in modo che il valore predefinito sia un valore valido dell'enumerazione.  Se un'enumerazione a cui è applicato l'attributo FlagsAttribute definisce un membro con valore zero, il relativo nome deve essere "None" per indicare che nell'enumerazione non è stato impostato alcun valore.|  
|[CA1009: Dichiarare correttamente i gestori eventi](../code-quality/ca1009-declare-event-handlers-correctly.md)|I metodi di gestione eventi accettano due parametri.  Il primo è di tipo System.Object ed è denominato "sender".  Corrisponde all'oggetto che ha generato l'evento.  Il secondo parametro è di tipo System.EventArgs ed è denominato "e".  Questi sono i dati associati all'evento.  I metodi del gestore eventi non restituiscono un valore. Nel linguaggio di programmazione C\# il tipo restituito è void.|  
|[CA1010: Le raccolte devono implementare un'interfaccia generica](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Per ampliare la possibilità di utilizzo di una raccolta, implementare una delle interfacce di raccolte generiche.  La raccolta può quindi essere utilizzata per popolare tipi di raccolte generiche.|  
|[CA1011: Considerare il passaggio di tipi di base come parametri](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Quando un tipo di base viene specificato come parametro in una dichiarazione di metodo, qualsiasi tipo derivato dal tipo di base può essere passato al metodo come argomento corrispondente.  Se la funzionalità aggiuntiva fornita dal tipo di parametro derivato non è necessaria, l'utilizzo del tipo di base consente un utilizzo più ampio del metodo.|  
|[CA1012: I tipi astratti non devono avere costruttori](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|I costruttori sui tipi astratti possono essere chiamati solo da tipi derivati.  Poiché i costruttori pubblici creano istanze di un tipo e non è possibile creare istanze di un tipo astratto, per una buona progettazione non bisognerebbe creare un tipo astratto con costruttore pubblico.|  
|[CA1013: Eseguire l'overload dell'operatore "uguale a" all'overload degli operatori di addizione e sottrazione](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Un membro pubblico o protetto implementa gli operatori di addizione o sottrazione senza implementare l'operatore di uguaglianza.|  
|[CA1014: Contrassegnare gli assembly con CLSCompliantAttribute](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|In Common Language Specification \(CLS\) vengono definite limitazioni di denominazione, tipi di dati e regole che gli assembly devono rispettare per poter essere utilizzati tra diversi linguaggi di programmazione.  In una buona programmazione tutti gli assembly devono indicare in modo esplicito la conformità CLS utilizzando CLSCompliantAttribute.  Se questo attributo non è presente su un assembly, tale assembly non è conforme.|  
|[CA1016: Contrassegnare gli assembly con AssemblyVersionAttribute](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|In .NET Framework viene utilizzato il numero di versione per identificare in modo univoco un assembly e per stabilire associazioni a tipi in assembly con nome sicuro.  Il numero di versione viene utilizzato insieme ai criteri di versione ed editore.  Per impostazione predefinita, le applicazioni vengono eseguite solo con la versione di assembly con cui sono state compilate.|  
|[CA1017: Contrassegnare gli assembly con ComVisibleAttribute](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|ComVisibleAttribute determina il modo in cui i client COM accedono al codice gestito.  In una buona progettazione gli assembly devono indicare in modo esplicito la visibilità COM.  È possibile impostare la visibilità COM per l'intero assembly e quindi eseguirne l'override per singoli tipi e membri dei tipi.  Se questo attributo non è presente, il contenuto dell'assembly è visibile ai client COM.|  
|[CA1018: Contrassegnare gli attributi con AttributeUsageAttribute](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Quando si definisce un attributo personalizzato, contrassegnarlo tramite AttributeUsageAttribute per indicare la posizione nel codice sorgente in cui applicare l'attributo personalizzato.  Il significato e l'utilizzo previsto di un attributo ne determinano le posizioni valide nel codice.|  
|[CA1019: Definire le funzioni di accesso per gli argomenti degli attributi](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Gli attributi possono definire argomenti obbligatori che devono essere specificati quando si applica l'attributo a una destinazione.  Sono inoltre noti come argomenti posizionali poiché vengono forniti ai costruttori di attributo come parametri posizionali.  Per ogni argomento obbligatorio, l'attributo deve fornire anche una proprietà in sola lettura corrispondente in modo che il valore dell'argomento possa essere recuperato in fase di esecuzione.  Gli attributi possono inoltre definire argomenti facoltativi, noti anche come argomenti denominati.  Questi argomenti sono forniti ai costruttori degli attributi in base al nome e devono disporre di una proprietà in lettura e scrittura corrispondente.|  
|[CA1020: Evitare l'utilizzo di spazi dei nomi con un numero ridotto di tipi](../code-quality/ca1020-avoid-namespaces-with-few-types.md)|Accertarsi che ognuno degli spazi dei nomi disponga di un'organizzazione logica e che sia presente un motivo valido per inserire tipi in uno spazio dei nomi scarsamente popolato.|  
|[CA1021: Evitare parametri out](../code-quality/ca1021-avoid-out-parameters.md)|Il passaggio di tipi per riferimento \(mediante out o ref\) richiede esperienza nell'utilizzo dei puntatori, nonché la conoscenza delle differenze tra tipi di valore e tipi di riferimento e dei metodi di gestione con più valori restituiti.  Inoltre, la differenza tra parametri out e ref non è nota a tutti.|  
|[CA1023: Gli indicizzatori non devono essere multidimensionali](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Gli indicizzatori, ovvero le proprietà indicizzate, devono utilizzare un indice singolo.  Gli indicizzatori multidimensionali possono ridurre sensibilmente l'usabilità della libreria.|  
|[CA1024: Utilizzare proprietà dove appropriato](../code-quality/ca1024-use-properties-where-appropriate.md)|Un metodo pubblico o protetto presenta un nome che inizia con "Get", non accetta parametri e restituisce un valore diverso da una matrice.  Il metodo presenta tutte le caratteristiche per diventare una proprietà.|  
|[Ca1025: Sostituire gli argomenti ripetitivi con una matrice di parametri](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Utilizzare una matrice di parametri anziché argomenti ripetuti quando non si conosce il numero esatto di argomenti e quando gli argomenti variabili sono dello stesso tipo oppure possono essere passati come lo stesso tipo.|  
|[CA1026: Evitare l'utilizzo di parametri predefiniti](../code-quality/ca1026-default-parameters-should-not-be-used.md)|I metodi che utilizzano parametri predefiniti sono consentiti dalla specifica CLS; questa specifica, tuttavia, consente ai compilatori di ignorare i valori assegnati a questi parametri.  Per mantenere il comportamento desiderato tra diversi linguaggi di programmazione, è necessario sostituire i metodi che utilizzano parametri predefiniti con overload di metodi che forniscono i parametri predefiniti.|  
|[CA1027: Contrassegnare le enumerazioni con FlagsAttribute](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Un'enumerazione è un tipo di valore che definisce un insieme di costanti denominate correlate.  Applicare FlagsAttribute a un'enumerazione quando le relative costanti denominate possono essere combinate in modo significativo.|  
|[CA1028: L'archivio di enum deve essere Int32](../code-quality/ca1028-enum-storage-should-be-int32.md)|Un'enumerazione è un tipo di valore che definisce un insieme di costanti denominate correlate.  Per impostazione predefinita, il tipo di dati System.Int32 viene utilizzato per archiviare il valore costante.  Anche se è possibile modificare questo tipo sottostante, non è necessario né consigliato nella maggior parte degli scenari.|  
|[CA1030: Utilizzare eventi dove appropriato](../code-quality/ca1030-use-events-where-appropriate.md)|Questa regola rileva i metodi che presentano nomi comunemente utilizzati per gli eventi.  Se un metodo viene chiamato in risposta a una modifica dello stato chiaramente definita, il metodo deve essere richiamato da un gestore eventi.  Gli oggetti che chiamano il metodo devono generare eventi anziché chiamare direttamente il metodo.|  
|[CA1031: Non rilevare tipi di eccezione generali](../code-quality/ca1031-do-not-catch-general-exception-types.md)|Le eccezioni generali non devono essere rilevate.  Rilevare un'eccezione più specifica oppure generare nuovamente l'eccezione generale come ultima istruzione nel blocco catch.|  
|[CA1032: Implementare costruttori di eccezioni standard](../code-quality/ca1032-implement-standard-exception-constructors.md)|Se non viene fornito l'insieme completo di costruttori può risultare difficile gestire correttamente le eccezioni.|  
|[CA1033: I metodi di interfaccia devono essere richiamabili dai tipi figlio](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|Un tipo visibile esternamente non sealed fornisce un'implementazione di metodo esplicita di un'interfaccia pubblica e non fornisce un metodo visibile esternamente alternativo con lo stesso nome.|  
|[CA1034: I tipi annidati non devono essere visibili](../code-quality/ca1034-nested-types-should-not-be-visible.md)|Un tipo annidato è un tipo dichiarato nell'ambito di un altro tipo.  I tipi annidati sono utili per incapsulare dettagli di implementazione privati del tipo contenitore.  I tipi annidati utilizzati per questo scopo non devono essere visibili esternamente.|  
|[CA1035: Le implementazioni di ICollection hanno membri fortemente tipizzati](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|La regola richiede che le implementazioni di ICollection forniscano membri fortemente tipizzati in modo che agli utenti non venga richiesto di eseguire il cast di argomenti al tipo Object quando utilizzano la funzionalità fornita dall'interfaccia.  La regola presuppone che il tipo che implementa ICollection esegua questa operazione per gestire una raccolta di istanze di un tipo più sicuro di Object.|  
|[CA1036: Eseguire l'override di metodi su tipi confrontabili](../code-quality/ca1036-override-methods-on-comparable-types.md)|Un tipo pubblico o protetto implementa l'interfaccia System.IComparable.  Non esegue l'override di Object.Equals né l'overload dell'operatore specifico del linguaggio per uguaglianza, ineguaglianza, minore di o maggiore di.|  
|[CA1038: Gli enumeratori devono essere fortemente tipizzati](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Questa regola richiede che le implementazioni di IEnumerator forniscano anche una versione fortemente tipizzata della proprietà Current in modo che agli utenti non venga richiesto di eseguire il cast del valore restituito al tipo sicuro quando utilizzano la funzionalità fornita dall'interfaccia.|  
|[CA1039: Gli elenchi sono fortemente tipizzati](../code-quality/ca1039-lists-are-strongly-typed.md)|La regola richiede che le implementazioni di IList forniscano membri fortemente tipizzati in modo che agli utenti non venga richiesto di eseguire il cast di argomenti al tipo System.Object quando utilizzano la funzionalità fornita dall'interfaccia.|  
|[CA1040: Evitare l'utilizzo di interfacce vuote](../code-quality/ca1040-avoid-empty-interfaces.md)|Le interfacce definiscono membri che forniscono un comportamento o un contratto di utilizzo.  La funzionalità descritta dall'interfaccia può essere adottata da qualsiasi tipo, indipendentemente dal punto in cui il tipo è visualizzato nella gerarchia di ereditarietà.  Un tipo implementa un'interfaccia fornendo implementazioni per i membri dell'interfaccia.  Un'interfaccia vuota non definisce alcun membro. Di conseguenza, non definisce un contratto implementabile.|  
|[CA1041: Fornire una proprietà ObsoleteAttribute.Message](../code-quality/ca1041-provide-obsoleteattribute-message.md)|Un tipo o un membro viene contrassegnato utilizzando un attributo System.ObsoleteAttribute per cui non è stata specificata la proprietà ObsoleteAttribute.Message.  Quando viene compilato un membro o un tipo contrassegnato utilizzando ObsoleteAttribute, viene visualizzata la proprietà Message dell'attributo che fornisce all'utente informazioni sul tipo o membro obsoleto.|  
|[CA0143: Utilizzare argomento di tipo stringa o integrale per gli indicizzatori](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Gli indicizzatori, ovvero le proprietà indicizzate, devono utilizzare tipi integrali o stringa per l'indice.  Questi tipi vengono in genere utilizzati per l'indicizzazione di strutture di dati e aumentano l'utilizzabilità della libreria.  L'utilizzo del tipo Object deve essere limitato ai casi in cui non sia possibile specificare in fase di progettazione il tipo integrale o stringa.|  
|[CA1044: Le proprietà non devono essere in sola scrittura](../code-quality/ca1044-properties-should-not-be-write-only.md)|Sebbene la presenza di proprietà di sola lettura sia accettabile e spesso necessaria, le linee guida di progettazione proibiscono l'utilizzo di proprietà di sola scrittura.  Ciò è dovuto al fatto che consentire a un utente di impostare un valore e quindi impedirgli di visualizzarlo, non offre alcuna sicurezza.  Inoltre, senza accesso in lettura, lo stato degli oggetti condivisi non può essere visualizzato, il che ne limita l'utilità.|  
|[CA1045: Non passare i tipi per riferimento](../code-quality/ca1045-do-not-pass-types-by-reference.md)|Il passaggio di tipi per riferimento \(mediante out o ref\) richiede esperienza nell'utilizzo dei puntatori, nonché la conoscenza delle differenze tra tipi di valore e tipi di riferimento e dei metodi di gestione con più valori restituiti.  Gli architetti di librerie destinate a un pubblico generico non devono aspettarsi che gli utenti siano in grado di utilizzare i parametri out o ref.|  
|[CA1046: Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Per i tipi di riferimento, l'implementazione predefinita dell'operatore di uguaglianza è quasi sempre corretta.  Per impostazione predefinita, i due riferimenti sono uguali solo se puntano allo stesso oggetto.|  
|[CA1047: Non dichiarare membri protetti nei tipi sealed](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|I tipi dichiarano membri protetti in modo che i tipi che ereditano possano accedere al membro o eseguirne l'override.  Per definizione, non è possibile ereditare tipi sealed, pertanto non è possibile chiamare metodi protetti su tipi sealed.|  
|[CA1048: Non dichiarare membri virtuali nei tipi sealed](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|I tipi dichiarano metodi come virtuali in modo che l'ereditarietà di tipi possa eseguire l'override dell'implementazione del metodo virtuale.  Per definizione, non è possibile ereditare un tipo sealed.  Di conseguenza, un metodo virtuale su un tipo sealed risulterà non significativo.|  
|[CA1049: I tipi delle risorse native devono essere Disposable](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|I tipi che allocano risorse non gestite devono implementare IDisposable per consentire ai chiamanti di rilasciare quelle risorse su richiesta e ridurre la durata degli oggetti che le contengono.|  
|[CA1050: Dichiarare i tipi negli spazi dei nomi](../code-quality/ca1050-declare-types-in-namespaces.md)|I tipi vengono dichiarati in spazi dei nomi per impedire conflitti di denominazione e per organizzare i tipi correlati in una gerarchia di oggetti.|  
|[CA1051: Non dichiarare campi di istanza visibili](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|L'utilizzo principale di un campo deve essere come dettaglio di implementazione.  I campi devono essere privati o interni e devono essere esposti tramite proprietà.|  
|[CA1052: I tipi che contengono membri statici devono essere sealed](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|Un tipo pubblico o protetto contiene solo membri statici e non è dichiarato utilizzando il modificatore sealed \(C\#\) o NotInheritable \(Visual Basic\).  Un tipo non adatto a essere ereditato deve essere contrassegnato utilizzando il modificatore sealed per impedire che venga utilizzato come tipo di base.|  
|[CA1053: I tipi che contengono membri statici non devono avere costruttori](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|Un tipo pubblico o annidato dichiara solo membri statici e presenta un costruttore predefinito pubblico o protetto.  Il costruttore non è necessario perché la chiamata a membri statici non richiede un'istanza del tipo.  A scopo di sicurezza e protezione, l'overload dei valori di stringa deve chiamare l'overload URI tramite l'argomento stringa.|  
|[CA1054: I parametri URI non devono essere stringhe](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|Se un metodo accetta una rappresentazione in forma di stringa di un URI, è necessario fornire un overload corrispondente che accetti un'istanza della classe URI che fornisce questi servizi in modo sicuro e protetto.|  
|[CA1055: I valori restituiti URI non devono essere stringhe](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|Questa regola presuppone che il metodo restituisca un URI.  Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza.  La classe System.Uri fornisce questi servizi in modo sicuro e protetto.|  
|[CA1056: Le proprietà URI non devono essere stringhe](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Questa regola presuppone che la proprietà rappresenti un URI.  Una rappresentazione in forma di stringa di un URI è soggetta a errori di analisi e codifica e può creare vulnerabilità nella sicurezza.  La classe System.Uri fornisce questi servizi in modo sicuro e protetto.|  
|[CA1057: Gli overload URI dei valori di stringa chiamano gli overload System.Uri](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Un tipo dichiara overload del metodo che risultano diversi solo per la sostituzione di un parametro di stringa con un parametro System.Uri.  L'overload che accetta il parametro di stringa non chiama l'overload che accetta il parametro URI.|  
|[CA1058: I tipi non devono estendere tipi di base specifici](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|Un tipo visibile esternamente estende tipi di base specifici.  Utilizzare una delle alternative seguenti:|  
|[CA1059: I membri non devono esporre tipi concreti specifici](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|Un tipo concreto è un tipo con implementazione completa, pertanto è possibile crearne un'istanza.  Per consentire un utilizzo esteso del membro, sostituire il tipo concreto utilizzando l'interfaccia suggerita.|  
|[CA1060: Spostare i P\/Invoke nella classe NativeMethods](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|I metodi di chiamata al sistema operativo, ad esempio quelli contrassegnati con <xref:System.Runtime.InteropServices.DllImportAttribute?displayProperty=fullName> o i metodi definiti mediante la parola chiave Declare in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] accedono a codice non gestito.  Questi metodi devono appartenere alla classe NativeMethods, SafeNativeMethods o UnsafeNativeMethods.|  
|[CA1061: Non nascondere i metodi di una classe base](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Un metodo in un tipo di base è nascosto da un metodo denominato in modo identico in un tipo derivato, quando la firma del parametro del metodo derivato differisce solo per i tipi che presentano una derivazione più debole rispetto ai tipi corrispondenti nella firma del parametro del metodo di base.|  
|[CA1062: Convalidare gli argomenti di metodi pubblici](../code-quality/ca1062-validate-arguments-of-public-methods.md)|È necessario che tutti gli argomenti di riferimento passati a metodi visibili esternamente vengano sottoposti a verifica per accertarsi che non corrispondano a valori Null.|  
|[CA1063: Implementare IDisposable correttamente](../code-quality/ca1063-implement-idisposable-correctly.md)|È necessario che tutti i tipi IDisposable implementino correttamente il modello Dispose.|  
|[CA1064: Le eccezioni devono essere pubbliche](../code-quality/ca1064-exceptions-should-be-public.md)|Un'eccezione interna è visibile solo nel relativo ambito interno.  Se l'eccezione si verifica al di fuori dell'ambito interno, può essere rilevata solo tramite l'eccezione di base.  Se l'eccezione interna è ereditata da <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName> o <xref:System.ApplicationException?displayProperty=fullName>, il codice esterno non disporrà di informazioni sufficienti per la corretta gestione dell'eccezione.|  
|[CA1065: Non generare eccezioni in posizioni non previste](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Un metodo che normalmente non genera eccezioni genera un'eccezione.|  
|[CA2210: Gli assembly devono avere nomi sicuri validi](../code-quality/ca2210-assemblies-should-have-valid-strong-names.md)|Il nome sicuro protegge i client dal caricamento involontario di un assembly alterato.  Gli assembly con nomi sicuri non devono essere distribuiti al di fuori di scenari molto limitati.  Se si condividono o distribuiscono assembly non firmati correttamente, l'assembly può essere alterato, non essere caricato in Common Language Runtime oppure l'utente potrebbe avere la necessità di disabilitare la verifica nel proprio computer.|