---
title: "Set di regole Regole estese delle linee guida di progettazione per codice gestito | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a338caf2-b75d-4f23-a0f9-3024fa0bceac
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 10
---
# Set di regole Regole estese delle linee guida di progettazione per codice gestito
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il set di regole Regole estese delle linee guida di progettazione Microsoft amplia le regole base delle linee guida di progettazione per aumentare i problemi di usabilità e manutenibilità segnalati.  Particolare attenzione è rivolta alle linee guida di denominazione.  È necessario considerare di includere questo set di regole se il progetto include codice di libreria o se si desidera applicare gli standard più elevati per la scrittura di codice di facile manutenibilità.  
  
 Le Regole estese delle linee guida di progettazione Microsoft includono tutte le Regole base delle linee guida di progettazione Microsoft.  Le Regole base delle linee guida di progettazione Microsoft includono tutte le Regole minime consigliate Microsoft.  Per ulteriori informazioni, vedere [Set di regole Regole base delle linee guida di progettazione per codice gestito](../code-quality/basic-design-guideline-rules-rule-set-for-managed-code.md) e [Set di regole consigliate gestite per codice gestito](../code-quality/managed-recommended-rules-rule-set-for-managed-code.md).  
  
 Nella tabella seguente vengono descritte tutte le regole del set Regole estese delle linee guida di progettazione Microsoft.  
  
|Regola|Descrizione|  
|------------|-----------------|  
|[CA1001](../code-quality/ca1001-types-that-own-disposable-fields-should-be-disposable.md)|I tipi proprietari di campi Disposable devono essere Disposable|  
|[CA1009](../code-quality/ca1009-declare-event-handlers-correctly.md)|Dichiarare correttamente i gestori eventi|  
|[CA1016](../code-quality/ca1016-mark-assemblies-with-assemblyversionattribute.md)|Contrassegnare gli assembly con AssemblyVersionAttribute|  
|[CA1033](../code-quality/ca1033-interface-methods-should-be-callable-by-child-types.md)|I metodi di interfaccia devono essere richiamabili dai tipi figlio|  
|[CA1049](../code-quality/ca1049-types-that-own-native-resources-should-be-disposable.md)|I tipi delle risorse native devono essere Disposable|  
|[CA1060](../code-quality/ca1060-move-p-invokes-to-nativemethods-class.md)|Spostare i P\/Invoke nella classe NativeMethods|  
|[CA1061](../code-quality/ca1061-do-not-hide-base-class-methods.md)|Non nascondere i metodi di una classe base|  
|[CA1063](../code-quality/ca1063-implement-idisposable-correctly.md)|Implementare IDisposable correttamente|  
|[CA1065](../code-quality/ca1065-do-not-raise-exceptions-in-unexpected-locations.md)|Non generare eccezioni in posizioni non previste|  
|[CA1301](../code-quality/ca1301-avoid-duplicate-accelerators.md)|Evitare tasti di scelta rapida duplicati|  
|[CA1400](../code-quality/ca1400-p-invoke-entry-points-should-exist.md)|I punti di ingresso P\/Invoke devono esistere|  
|[CA1401](../code-quality/ca1401-p-invokes-should-not-be-visible.md)|I P\/Invoke non devono essere visibili|  
|[CA1403](../code-quality/ca1403-auto-layout-types-should-not-be-com-visible.md)|I tipi layout automatici non devono essere visibili a COM|  
|[CA1404](../code-quality/ca1404-call-getlasterror-immediately-after-p-invoke.md)|Chiamare GetLastError immediatamente dopo P\/Invoke|  
|[CA1405](../code-quality/ca1405-com-visible-type-base-types-should-be-com-visible.md)|I tipi di base del tipo visibile a COM devono essere visibili a COM|  
|[CA1410](../code-quality/ca1410-com-registration-methods-should-be-matched.md)|I metodi di registrazione COM devono corrispondere|  
|[CA1415](../code-quality/ca1415-declare-p-invokes-correctly.md)|Dichiarare correttamente i P\/Invoke|  
|[CA1821](../code-quality/ca1821-remove-empty-finalizers.md)|Rimuovere i finalizzatori vuoti|  
|[CA1900](../code-quality/ca1900-value-type-fields-should-be-portable.md)|I campi dei tipi di valore devono essere portabili|  
|[CA1901](../code-quality/ca1901-p-invoke-declarations-should-be-portable.md)|Le dichiarazioni P\/Invoke devono essere portabili|  
|[CA2002](../code-quality/ca2002-do-not-lock-on-objects-with-weak-identity.md)|Non bloccare oggetti con identità debole|  
|[CA2100](../code-quality/ca2100-review-sql-queries-for-security-vulnerabilities.md)|Controllare l'eventuale vulnerabilità di sicurezza delle query SQL|  
|[CA2101](../code-quality/ca2101-specify-marshaling-for-p-invoke-string-arguments.md)|Specificare il marshalling per gli argomenti di stringa P\/Invoke|  
|[CA2108](../code-quality/ca2108-review-declarative-security-on-value-types.md)|Controllare la sicurezza dichiarativa sui tipi di valori|  
|[CA2111](../code-quality/ca2111-pointers-should-not-be-visible.md)|I puntatori non devono essere visibili|  
|[CA2112](../code-quality/ca2112-secured-types-should-not-expose-fields.md)|I tipi protetti non devono esporre campi|  
|[CA2114](../code-quality/ca2114-method-security-should-be-a-superset-of-type.md)|La sicurezza del metodo deve essere un superset del tipo|  
|[CA2116](../code-quality/ca2116-aptca-methods-should-only-call-aptca-methods.md)|I metodi APTCA devono chiamare solo metodi APTCA|  
|[CA2117](../code-quality/ca2117-aptca-types-should-only-extend-aptca-base-types.md)|I tipi APTCA devono estendere solo tipi di base APTCA|  
|[CA2122](../code-quality/ca2122-do-not-indirectly-expose-methods-with-link-demands.md)|Non esporre in modo indiretto metodi con richieste di collegamento|  
|[CA2123](../code-quality/ca2123-override-link-demands-should-be-identical-to-base.md)|Le richieste di collegamento negli override devono essere identiche a quelle nei metodi di base|  
|[CA2124](../code-quality/ca2124-wrap-vulnerable-finally-clauses-in-outer-try.md)|Eseguire il wrapping delle clausole finally vulnerabili in un try esterno|  
|[CA2126](../code-quality/ca2126-type-link-demands-require-inheritance-demands.md)|Per le richieste di collegamento dei tipi sono necessarie richieste di ereditarietà|  
|[CA2131](../code-quality/ca2131-security-critical-types-may-not-participate-in-type-equivalence.md)|I tipi SecurityCritical non possono partecipare all'equivalenza del tipo|  
|[CA2132](../code-quality/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors.md)|I costruttori predefiniti devono essere Critical almeno come i costruttori predefiniti del tipo base|  
|[CA2133](../code-quality/ca2133-delegates-must-bind-to-methods-with-consistent-transparency.md)|Delegati devono essere associati ai metodi con trasparenza consistente|  
|[CA2134](../code-quality/ca2134-methods-must-keep-consistent-transparency-when-overriding-base-methods.md)|I metodi devono conservare trasparenza consistente durante l'override dei metodi base|  
|[CA2137](../code-quality/ca2137-transparent-methods-must-contain-only-verifiable-il.md)|I metodi Transparent devono contenere solo IL verificabile|  
|[CA2138](../code-quality/ca2138-transparent-methods-must-not-call-methods-with-the-suppressunmanagedcodesecurity-attribute.md)|I metodi Transparent non devono chiamare i metodi con l'attributo SuppressUnmanagedCodeSecurity|  
|[CA2140](../code-quality/ca2140-transparent-code-must-not-reference-security-critical-items.md)|Il codice Transparent non deve far riferimento a elementi SecurityCritical|  
|[CA2141](../code-quality/ca2141-transparent-methods-must-not-satisfy-linkdemands.md)|I metodi Transparent non devono soddisfare i LinkDemand|  
|[CA2146](../code-quality/ca2146-types-must-be-at-least-as-critical-as-their-base-types-and-interfaces.md)|I tipi devono essere Critical almeno come le interfacce e i tipi base relativi|  
|[CA2147](../code-quality/ca2147-transparent-methods-may-not-use-security-asserts.md)|I metodi Transparent non possono utilizzare asserzioni di sicurezza|  
|[CA2149](../code-quality/ca2149-transparent-methods-must-not-call-into-native-code.md)|I metodi Transparent non devono effettuare chiamate nel codice nativo|  
|[CA2200](../code-quality/ca2200-rethrow-to-preserve-stack-details.md)|Eseguire il rethrow per conservare i dettagli dello stack|  
|[CA2202](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)|Non eliminare oggetti più volte|  
|[CA2207](../code-quality/ca2207-initialize-value-type-static-fields-inline.md)|Inizializzare i campi statici dei tipi di valore inline|  
|[CA2212](../code-quality/ca2212-do-not-mark-serviced-components-with-webmethod.md)|Non contrassegnare componenti serviti con WebMethod|  
|[CA2213](../code-quality/ca2213-disposable-fields-should-be-disposed.md)|I campi Disposable devono essere eliminati|  
|[CA2214](../code-quality/ca2214-do-not-call-overridable-methods-in-constructors.md)|Non chiamare metodi sottoponibili a override nei costruttori|  
|[CA2216](../code-quality/ca2216-disposable-types-should-declare-finalizer.md)|I tipi Disposable devono dichiarare un finalizzatore|  
|[CA2220](../code-quality/ca2220-finalizers-should-call-base-class-finalizer.md)|I finalizzatori devono chiamare il finalizzatore della classe base|  
|[CA2229](../code-quality/ca2229-implement-serialization-constructors.md)|Implementare costruttori di serializzazione|  
|[CA2231](../code-quality/ca2231-overload-operator-equals-on-overriding-valuetype-equals.md)|Eseguire l'overload dell'operatore "uguale a" all'override di ValueType.Equals|  
|[CA2232](../code-quality/ca2232-mark-windows-forms-entry-points-with-stathread.md)|Contrassegnare i punti di ingresso del Windows Form con STAThread|  
|[CA2235](../code-quality/ca2235-mark-all-non-serializable-fields.md)|Contrassegnare tutti i campi non serializzabili|  
|[CA2236](../code-quality/ca2236-call-base-class-methods-on-iserializable-types.md)|Chiamare metodi della classe base su tipi ISerializable|  
|[CA2237](../code-quality/ca2237-mark-iserializable-types-with-serializableattribute.md)|Contrassegnare i tipi ISerializable con SerializableAttribute|  
|[CA2238](../code-quality/ca2238-implement-serialization-methods-correctly.md)|Implementare correttamente i metodi di serializzazione|  
|[CA2240](../code-quality/ca2240-implement-iserializable-correctly.md)|Implementare ISerializable in modo corretto|  
|[CA2241](../code-quality/ca2241-provide-correct-arguments-to-formatting-methods.md)|Fornire argomenti corretti ai metodi di formattazione|  
|[CA2242](../code-quality/ca2242-test-for-nan-correctly.md)|Testare i valori NaN in modo corretto|  
|[CA1000](../code-quality/ca1000-do-not-declare-static-members-on-generic-types.md)|Non dichiarare membri statici su tipi generici|  
|[CA1002](../code-quality/ca1002-do-not-expose-generic-lists.md)|Non esporre elenchi generici|  
|[CA1003](../code-quality/ca1003-use-generic-event-handler-instances.md)|Utilizzare istanze di gestori eventi generici|  
|[CA1004](../code-quality/ca1004-generic-methods-should-provide-type-parameter.md)|I metodi generici devono fornire parametri di tipo|  
|[CA1005](../code-quality/ca1005-avoid-excessive-parameters-on-generic-types.md)|Evitare un uso eccessivo di parametri nei tipi generici|  
|[CA1006](../code-quality/ca1006-do-not-nest-generic-types-in-member-signatures.md)|Non annidare tipi generici nelle firme dei membri|  
|[CA1007](../code-quality/ca1007-use-generics-where-appropriate.md)|Utilizzare generics dove appropriato|  
|[CA1008](../code-quality/ca1008-enums-should-have-zero-value.md)|Gli enum devono avere valore zero|  
|[CA1010](../code-quality/ca1010-collections-should-implement-generic-interface.md)|Le raccolte devono implementare un'interfaccia generica|  
|[CA1011](../code-quality/ca1011-consider-passing-base-types-as-parameters.md)|Considerare il passaggio di tipi di base come parametri|  
|[CA1012](../code-quality/ca1012-abstract-types-should-not-have-constructors.md)|I tipi astratti non devono avere costruttori|  
|[CA1013](../code-quality/ca1013-overload-operator-equals-on-overloading-add-and-subtract.md)|Eseguire l'overload dell'operatore "uguale a" all'overload degli operatori di addizione e sottrazione|  
|[CA1014](../code-quality/ca1014-mark-assemblies-with-clscompliantattribute.md)|Contrassegnare gli assembly con CLSCompliantAttribute|  
|[CA1017](../code-quality/ca1017-mark-assemblies-with-comvisibleattribute.md)|Contrassegnare gli assembly con ComVisibleAttribute|  
|[CA1018](../code-quality/ca1018-mark-attributes-with-attributeusageattribute.md)|Contrassegnare gli attributi con AttributeUsageAttribute|  
|[CA1019](../code-quality/ca1019-define-accessors-for-attribute-arguments.md)|Definire le funzioni di accesso per gli argomenti degli attributi|  
|[CA1023](../code-quality/ca1023-indexers-should-not-be-multidimensional.md)|Gli indicizzatori non devono essere multidimensionali|  
|[CA1024](../code-quality/ca1024-use-properties-where-appropriate.md)|Utilizzare proprietà dove appropriato|  
|[CA1025](../code-quality/ca1025-replace-repetitive-arguments-with-params-array.md)|Sostituire gli argomenti ripetitivi con una matrice di parametri|  
|[CA1026](../code-quality/ca1026-default-parameters-should-not-be-used.md)|Evitare l'utilizzo di parametri predefiniti|  
|[CA1027](../code-quality/ca1027-mark-enums-with-flagsattribute.md)|Contrassegnare le enumerazioni con FlagsAttribute|  
|[CA1028](../code-quality/ca1028-enum-storage-should-be-int32.md)|L'archiviazione di enum deve essere Int32|  
|[CA1030](../code-quality/ca1030-use-events-where-appropriate.md)|Utilizzare eventi dove appropriato|  
|[CA1031](../code-quality/ca1031-do-not-catch-general-exception-types.md)|Non rilevare tipi di eccezione generali|  
|[CA1032](../code-quality/ca1032-implement-standard-exception-constructors.md)|Implementare costruttori di eccezioni standard|  
|[CA1034](../code-quality/ca1034-nested-types-should-not-be-visible.md)|I tipi annidati non devono essere visibili|  
|[CA1035](../code-quality/ca1035-icollection-implementations-have-strongly-typed-members.md)|Le implementazioni di ICollection hanno membri fortemente tipizzati|  
|[CA1036](../code-quality/ca1036-override-methods-on-comparable-types.md)|Eseguire l'override di metodi su tipi confrontabili|  
|[CA1038](../code-quality/ca1038-enumerators-should-be-strongly-typed.md)|Gli enumeratori devono essere fortemente tipizzati|  
|[CA1039](../code-quality/ca1039-lists-are-strongly-typed.md)|Gli elenchi sono fortemente tipizzati|  
|[CA1041](../code-quality/ca1041-provide-obsoleteattribute-message.md)|Fornire una proprietà ObsoleteAttribute.Message|  
|[CA1043](../code-quality/ca1043-use-integral-or-string-argument-for-indexers.md)|Utilizzare argomento di tipo stringa o integrale per gli indicizzatori|  
|[CA1044](../code-quality/ca1044-properties-should-not-be-write-only.md)|Le proprietà non devono essere in sola scrittura|  
|[CA1046](../code-quality/ca1046-do-not-overload-operator-equals-on-reference-types.md)|Non eseguire l'overload dell'operatore "uguale a" per i tipi di riferimento|  
|[CA1047](../code-quality/ca1047-do-not-declare-protected-members-in-sealed-types.md)|Non dichiarare membri protetti nei tipi sealed|  
|[CA1048](../code-quality/ca1048-do-not-declare-virtual-members-in-sealed-types.md)|Non dichiarare membri virtuali nei tipi sealed|  
|[CA1050](../code-quality/ca1050-declare-types-in-namespaces.md)|Dichiarare i tipi negli spazi dei nomi|  
|[CA1051](../code-quality/ca1051-do-not-declare-visible-instance-fields.md)|Non dichiarare campi di istanza visibili|  
|[CA1052](../code-quality/ca1052-static-holder-types-should-be-sealed.md)|I tipi che contengono membri statici devono essere sealed|  
|[CA1053](../code-quality/ca1053-static-holder-types-should-not-have-constructors.md)|I tipi che contengono membri statici non devono avere costruttori|  
|[CA1054](../code-quality/ca1054-uri-parameters-should-not-be-strings.md)|I parametri URI non devono essere stringhe|  
|[CA1055](../code-quality/ca1055-uri-return-values-should-not-be-strings.md)|I valori restituiti URI non devono essere stringhe|  
|[CA1056](../code-quality/ca1056-uri-properties-should-not-be-strings.md)|Le proprietà URI non devono essere stringhe|  
|[CA1057](../code-quality/ca1057-string-uri-overloads-call-system-uri-overloads.md)|Gli overload URI di stringhe chiamano gli overload System.Uri|  
|[CA1058](../code-quality/ca1058-types-should-not-extend-certain-base-types.md)|I tipi non devono estendere tipi di base specifici|  
|[CA1059](../code-quality/ca1059-members-should-not-expose-certain-concrete-types.md)|I membri non devono esporre tipi concreti specifici|  
|[CA1064](../code-quality/ca1064-exceptions-should-be-public.md)|Le eccezioni devono essere pubbliche|  
|[CA1500](../code-quality/ca1500-variable-names-should-not-match-field-names.md)|I nomi delle variabili non devono corrispondere ai nomi dei campi|  
|[CA1502](../code-quality/ca1502-avoid-excessive-complexity.md)|Evitare complessità eccessiva|  
|[CA1708](../code-quality/ca1708-identifiers-should-differ-by-more-than-case.md)|Gli identificatori non si devono differenziare solo in base alle maiuscole e minuscole|  
|[CA1716](../code-quality/ca1716-identifiers-should-not-match-keywords.md)|Gli identificatori non devono corrispondere a parole chiave|  
|[CA1801](../code-quality/ca1801-review-unused-parameters.md)|Rivedere i parametri inutilizzati|  
|[CA1804](../code-quality/ca1804-remove-unused-locals.md)|Rimuovere locali non utilizzati|  
|[CA1809](../code-quality/ca1809-avoid-excessive-locals.md)|Evitare un numero eccessivo di variabili locali|  
|[CA1810](../code-quality/ca1810-initialize-reference-type-static-fields-inline.md)|Inizializzare i campi statici del tipo di riferimento inline|  
|[CA1811](../code-quality/ca1811-avoid-uncalled-private-code.md)|Evitare codice privato che non viene richiamato|  
|[CA1812](../code-quality/ca1812-avoid-uninstantiated-internal-classes.md)|Evitare classi interne prive di istanze|  
|[CA1813](../code-quality/ca1813-avoid-unsealed-attributes.md)|Evitare attributi non sealed|  
|[CA1814](../code-quality/ca1814-prefer-jagged-arrays-over-multidimensional.md)|Preferire matrici di matrici rispetto a matrici multidimensionali|  
|[CA1815](../code-quality/ca1815-override-equals-and-operator-equals-on-value-types.md)|Eseguire l'override di Equals e dell'operatore "uguale a" sui tipi di valore|  
|[CA1819](../code-quality/ca1819-properties-should-not-return-arrays.md)|Le proprietà non devono restituire matrici|  
|[CA1820](../code-quality/ca1820-test-for-empty-strings-using-string-length.md)|Testare le stringhe vuote utilizzando la lunghezza di stringa|  
|[CA1822](../code-quality/ca1822-mark-members-as-static.md)|Contrassegnare i membri come statici|  
|[CA1823](../code-quality/ca1823-avoid-unused-private-fields.md)|Evitare campi privati non utilizzati|  
|[CA2201](../code-quality/ca2201-do-not-raise-reserved-exception-types.md)|Non generare tipi di eccezione riservati|  
|[CA2205](../code-quality/ca2205-use-managed-equivalents-of-win32-api.md)|Utilizzare equivalenti gestiti dall'API Win32|  
|[CA2208](../code-quality/ca2208-instantiate-argument-exceptions-correctly.md)|Creare istanze di eccezioni di argomento correttamente|  
|[CA2211](../code-quality/ca2211-non-constant-fields-should-not-be-visible.md)|I campi non costanti non devono essere visibili|  
|[CA2217](../code-quality/ca2217-do-not-mark-enums-with-flagsattribute.md)|Non contrassegnare le enumerazioni con FlagsAttribute|  
|[CA2219](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)|Non generare eccezioni in clausole di eccezione|  
|[CA2221](../code-quality/ca2221-finalizers-should-be-protected.md)|I finalizzatori devono essere protetti|  
|[CA2222](../code-quality/ca2222-do-not-decrease-inherited-member-visibility.md)|Non diminuire la visibilità di membri ereditati|  
|[CA2223](../code-quality/ca2223-members-should-differ-by-more-than-return-type.md)|La differenza tra membri non deve limitarsi al tipo restituito|  
|[CA2224](../code-quality/ca2224-override-equals-on-overloading-operator-equals.md)|Eseguire l'override di Equals all'override dell'operatore|  
|[CA2225](../code-quality/ca2225-operator-overloads-have-named-alternates.md)|Gli overload degli operatori hanno alternative con nome|  
|[CA2226](../code-quality/ca2226-operators-should-have-symmetrical-overloads.md)|Gli operatori devono avere overload simmetrici|  
|[CA2227](../code-quality/ca2227-collection-properties-should-be-read-only.md)|Le proprietà di raccolta devono essere in sola lettura|  
|[CA2230](../code-quality/ca2230-use-params-for-variable-arguments.md)|Utilizzare params per argomenti variabili|  
|[CA2234](../code-quality/ca2234-pass-system-uri-objects-instead-of-strings.md)|Passare oggetti System.Uri invece di stringhe|  
|[CA2239](../code-quality/ca2239-provide-deserialization-methods-for-optional-fields.md)|Fornire metodi di deserializzazione per i campi facoltativi|  
|[CA1020](../code-quality/ca1020-avoid-namespaces-with-few-types.md)|Evitare l'utilizzo di spazi dei nomi con un numero ridotto di tipi|  
|[CA1021](../code-quality/ca1021-avoid-out-parameters.md)|Evitare parametri out|  
|[CA1040](../code-quality/ca1040-avoid-empty-interfaces.md)|Evitare l'utilizzo di interfacce vuote|  
|[CA1045](../code-quality/ca1045-do-not-pass-types-by-reference.md)|Non passare i tipi per riferimento|  
|[CA1062](../code-quality/ca1062-validate-arguments-of-public-methods.md)|Convalidare gli argomenti di metodi pubblici|  
|[CA1501](../code-quality/ca1501-avoid-excessive-inheritance.md)|Evitare ereditarietà eccessiva|  
|[CA1504](../code-quality/ca1504-review-misleading-field-names.md)|Controllare i nomi dei campi fuorvianti|  
|[CA1505](../code-quality/ca1505-avoid-unmaintainable-code.md)|Evitare codice non manutenibile|  
|[CA1506](../code-quality/ca1506-avoid-excessive-class-coupling.md)|Evitare un numero eccessivo di accoppiamenti di classi|  
|[CA1700](../code-quality/ca1700-do-not-name-enum-values-reserved.md)|Non denominare 'Reserved' i valori di enumerazione|  
|[CA1701](../code-quality/ca1701-resource-string-compound-words-should-be-cased-correctly.md)|Le parole composte di una stringa di risorsa devono essere digitate correttamente con distinzione tra maiuscole e minuscole|  
|[CA1702](../code-quality/ca1702-compound-words-should-be-cased-correctly.md)|Le parole composte devono essere digitate correttamente con distinzione tra maiuscole e minuscole|  
|[CA1703](../code-quality/ca1703-resource-strings-should-be-spelled-correctly.md)|Le stringhe di risorsa devono essere digitate correttamente|  
|[CA1704](../code-quality/ca1704-identifiers-should-be-spelled-correctly.md)|Gli identificatori devono essere digitati correttamente|  
|[CA1707](../code-quality/ca1707-identifiers-should-not-contain-underscores.md)|Gli identificatori non devono contenere caratteri di sottolineatura|  
|[CA1709](../code-quality/ca1709-identifiers-should-be-cased-correctly.md)|Gli identificatori devono essere digitati correttamente con distinzione tra maiuscole e minuscole|  
|[CA1710](../code-quality/ca1710-identifiers-should-have-correct-suffix.md)|Gli identificatori devono contenere il suffisso corretto|  
|[CA1711](../code-quality/ca1711-identifiers-should-not-have-incorrect-suffix.md)|Gli identificatori non devono contenere un suffisso non corretto|  
|[CA1712](../code-quality/ca1712-do-not-prefix-enum-values-with-type-name.md)|Non utilizzare nomi di tipo come prefisso nei valori di enumerazione|  
|[CA1713](../code-quality/ca1713-events-should-not-have-before-or-after-prefix.md)|Non utilizzare il prefisso Before o After negli eventi|  
|[CA1714](../code-quality/ca1714-flags-enums-should-have-plural-names.md)|Le enumerazioni con Flags devono avere nomi plurali|  
|[CA1715](../code-quality/ca1715-identifiers-should-have-correct-prefix.md)|Gli identificatori devono contenere il prefisso corretto|  
|[CA1717](../code-quality/ca1717-only-flagsattribute-enums-should-have-plural-names.md)|Solo le enumerazioni con FlagsAttribute devono avere nomi plurali|  
|[CA1719](../code-quality/ca1719-parameter-names-should-not-match-member-names.md)|I nomi dei parametri non devono corrispondere ai nomi dei membri|  
|[CA1720](../code-quality/ca1720-identifiers-should-not-contain-type-names.md)|Gli identificatori non devono contenere nomi di tipo|  
|[CA1721](../code-quality/ca1721-property-names-should-not-match-get-methods.md)|I nomi delle proprietà non devono corrispondere ai metodi get|  
|[CA1722](../code-quality/ca1722-identifiers-should-not-have-incorrect-prefix.md)|Gli identificatori non devono contenere il prefisso non corretto|  
|[CA1724](../code-quality/ca1724-type-names-should-not-match-namespaces.md)|I nomi dei tipi non devono corrispondere agli spazi dei nomi|  
|[CA1725](../code-quality/ca1725-parameter-names-should-match-base-declaration.md)|I nomi dei parametri devono corrispondere alla dichiarazione di base|  
|[CA1726](../code-quality/ca1726-use-preferred-terms.md)|Utilizzare termini preferiti|  
|[CA2204](../code-quality/ca2204-literals-should-be-spelled-correctly.md)|I valori letterali devono essere digitati in modo corretto|