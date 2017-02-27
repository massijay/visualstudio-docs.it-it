---
title: "IDiaSymbol | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol (interfaccia)"
ms.assetid: 01ad328a-736c-4933-a9f8-c2ded19ddd8c
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# IDiaSymbol
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Vengono descritte le proprietà di un'istanza del simbolo.  
  
## Sintassi  
  
```  
IDiaSymbol : IUnknown  
```  
  
## Metodi in ordine alfabetico  
 Nella tabella seguente sono elencati i metodi `IDiaSymbol`.  
  
> [!NOTE]
>  I simboli verranno restituiti i dati significativi solo per alcuni di questi metodi, a seconda del tipo di simbolo.  Se un metodo restituisce `S_OK`, il metodo restituisce i dati significativi.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md)|Recupera tutti i figli del simbolo.|  
|[IDiaSymbol::findChildrenEx](../../debugger/debug-interface-access/idiasymbol-findchildrenex.md)|Recupera i figli del simbolo.  Questo metodo è la versione estesa [IDiaSymbol::findChildren](../../debugger/debug-interface-access/idiasymbol-findchildren.md).|  
|[IDiaSymbol::findChildrenExByAddr](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyaddr.md)|Recupera i figli di simboli che sono validi a un indirizzo specificato.|  
|[IDiaSymbol::findChildrenExByRVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyrva.md)|Recupera i figli di simboli che sono validi a un indirizzo virtuale relativo specificato \(RVA\).|  
|[IDiaSymbol::findChildrenExByVA](../../debugger/debug-interface-access/idiasymbol-findchildrenexbyva.md)|Recupera i figli di simboli che sono validi a un indirizzo virtuale specificato.|  
|[IDiaSymbol::findInlineFramesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyaddr.md)|Recupera un'enumerazione che consente a un client ripetere da tutti i frame inline in un indirizzo specificato.|  
|[IDiaSymbol::findInlineFramesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyrva.md)|Recupera un'enumerazione che consente a un client ripetere da tutti i frame inline in un indirizzo virtuale relativo specificato \(RVA\).|  
|[IDiaSymbol::findInlineFramesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineframesbyva.md)|Recupera un'enumerazione che consente a un client ripetere da tutti i frame inline in un indirizzo virtuale specificato \(VA\).|  
|[IDiaSymbol::findInlineeLines](../../debugger/debug-interface-access/idiasymbol-findinlineelines.md)|Recupera un'enumerazione che consente a un client ripetere direttamente o indirettamente dalle informazioni sul numero di riga di tutte le funzioni in linea, in questo simbolo.|  
|[IDiaSymbol::findInlineeLinesByAddr](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyaddr.md)|Recupera un'enumerazione che consente a un client ripetere direttamente o indirettamente dalle informazioni sul numero di riga di tutte le funzioni in linea, in questo simbolo nell'intervallo di indirizzi specificato.|  
|[IDiaSymbol::findInlineeLinesByRVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyrva.md)|Recupera un'enumerazione che consente a un client ripetere direttamente o indirettamente dalle informazioni sul numero di riga di tutte le funzioni in linea, in questo simbolo interno dell'indirizzo virtuale relativo specificato \(RVA\).|  
|[IDiaSymbol::findInlineeLinesByVA](../../debugger/debug-interface-access/idiasymbol-findinlineelinesbyva.md)|Recupera un'enumerazione che consente a un client ripetere direttamente o indirettamente dalle informazioni sul numero di riga di tutte le funzioni in linea, in questo simbolo interno dell'indirizzo virtuale specificato \(VA\).|  
|[IDiaSymbol::findSymbolsByRVAForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsbyrvaforacceleratorpointertag.md)|Dato un valore corrispondente tag, questo metodo restituisce un'enumerazione di simboli contenuti in questa funzione stub a un indirizzo virtuale relativo specificato.|  
|[IDiaSymbol::findSymbolsForAcceleratorPointerTag](../../debugger/debug-interface-access/idiasymbol-findsymbolsforacceleratorpointertag.md)|Restituisce il numero dei tag del puntatore di scelta rapida nella funzione dello stub di AMP C\+\+.|  
|[IDiaSymbol::get\_acceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-acceleratorpointertags.md)|Restituisce tutti i valori del tag del puntatore di scelta rapida che corrispondono alla funzione stub di tasti di scelta rapida AMP C\+\+.|  
|[IDiaSymbol::get\_access](../../debugger/debug-interface-access/idiasymbol-get-access.md)|Recupera il modificatore di accesso al membro di una classe.|  
|[IDiaSymbol::get\_addressOffset](../../debugger/debug-interface-access/idiasymbol-get-addressoffset.md)|Recupera la parte di offset di una posizione address.|  
|[IDiaSymbol::get\_addressSection](../../debugger/debug-interface-access/idiasymbol-get-addresssection.md)|Recupera la parte della sezione di una posizione address.|  
|[IDiaSymbol::get\_addressTaken](../../debugger/debug-interface-access/idiasymbol-get-addresstaken.md)|Recupera un flag che indica se un altro simbolo fa riferimento questo indirizzo.|  
|[IDiaSymbol::get\_age](../../debugger/debug-interface-access/idiasymbol-get-age.md)|Recupera il valore di età di un database di programma.|  
|[IDiaSymbol::get\_arrayIndexType](../../debugger/debug-interface-access/idiasymbol-get-arrayindextype.md)|Recupera l'identificatore del simbolo del tipo di indice della matrice.|  
|[IDiaSymbol::get\_arrayIndexTypeId](../../debugger/debug-interface-access/idiasymbol-get-arrayindextypeid.md)|Recupera l'identificatore di tipo di indice della matrice dei simboli.|  
|[IDiaSymbol::get\_backEndMajor](../../debugger/debug-interface-access/idiasymbol-get-backendmajor.md)|Recupera il numero di versione principale back\-end.|  
|[IDiaSymbol::get\_backEndMinor](../../debugger/debug-interface-access/idiasymbol-get-backendminor.md)|Recupera il numero di versione secondario back\-end.|  
|[IDiaSymbol::get\_backEndBuild](../../debugger/debug-interface-access/idiasymbol-get-backendbuild.md)|Recupera il numero di build back\-end.|  
|[IDiaSymbol::get\_baseDataOffset](../../debugger/debug-interface-access/idiasymbol-get-basedataoffset.md)|Recuperare l'offset di base di dati.|  
|[IDiaSymbol::get\_baseDataSlot](../../debugger/debug-interface-access/idiasymbol-get-basedataslot.md)|Recupera lo slot di dati di base.|  
|[IDiaSymbol::get\_baseSymbol](../../debugger/debug-interface-access/idiasymbol-get-basesymbol.md)|Recupera il simbolo che il puntatore è basato.|  
|[IDiaSymbol::get\_baseSymbolId](../../debugger/debug-interface-access/idiasymbol-get-basesymbolid.md)|Recupera il simbolo ID da cui il puntatore è basato.|  
|[IDiaSymbol::get\_baseType](../../debugger/debug-interface-access/idiasymbol-get-basetype.md)|Recupera il tag del tipo di un tipo semplice.|  
|[IDiaSymbol::get\_bitPosition](../../debugger/debug-interface-access/idiasymbol-get-bitposition.md)|Recupera il percorso di bit di un percorso.|  
|[IDiaSymbol::get\_builtInKind](../../debugger/debug-interface-access/idiasymbol-get-builtinkind.md)|Recupera un tipo incorporato del tipo di HLSL.|  
|[IDiaSymbol::get\_callingConvention](../../debugger/debug-interface-access/idiasymbol-get-callingconvention.md)|Restituisce un indicatore della convenzione di chiamata di un metodo.|  
|[IDiaSymbol::get\_classParent](../../debugger/debug-interface-access/idiasymbol-get-classparent.md)|Recupera un riferimento al padre del simbolo.|  
|[IDiaSymbol::get\_classParentId](../../debugger/debug-interface-access/idiasymbol-get-classparentid.md)|Recupera l'identificatore della classe padre del simbolo.|  
|[IDiaSymbol::get\_code](../../debugger/debug-interface-access/idiasymbol-get-code.md)|Recupera un flag che indica se il simbolo fa riferimento a un codice dell'.|  
|[IDiaSymbol::get\_compilerGenerated](../../debugger/debug-interface-access/idiasymbol-get-compilergenerated.md)|Recupera un flag che indica se il simbolo è generato dal compilatore.|  
|[IDiaSymbol::get\_compilerName](../../debugger/debug-interface-access/idiasymbol-get-compilername.md)|Recupera il nome del compilatore utilizzato per creare [Compilando](../../debugger/debug-interface-access/compiland.md).|  
|[IDiaSymbol::get\_constructor](../../debugger/debug-interface-access/idiasymbol-get-constructor.md)|Recupera un flag che indica se il tipo di dati definito dall'utente dispone di un costruttore.|  
|[IDiaSymbol::get\_container](../../debugger/debug-interface-access/idiasymbol-get-container.md)|Recupera il simbolo contenitore di questo simbolo.|  
|[IDiaSymbol::get\_constType](../../debugger/debug-interface-access/idiasymbol-get-consttype.md)|Recupera un flag che indica se il tipo di dati definito dall'utente è costante.|  
|[IDiaSymbol::get\_count](../../debugger/debug-interface-access/idiasymbol-get-count.md)|Recupera il numero di elementi in un elenco o in una matrice.|  
|[IDiaSymbol::get\_countLiveRanges](../../debugger/debug-interface-access/idiasymbol-get-countliveranges.md)|Recupera il numero di intervalli degli indirizzi validi associati al simbolo locale.|  
|[IDiaSymbol::get\_customCallingConvention](../../debugger/debug-interface-access/idiasymbol-get-customcallingconvention.md)|Recupera un flag che indica se la funzione utilizza la convenzione di chiamata personalizzata.|  
|[IDiaSymbol::get\_dataBytes](../../debugger/debug-interface-access/idiasymbol-get-databytes.md)|Recupera i byte di dati di un simbolo OEM.|  
|[IDiaSymbol::get\_dataKind](../../debugger/debug-interface-access/idiasymbol-get-datakind.md)|Recupera la classificazione variabile di un simbolo di dati.|  
|[IDiaSymbol::get\_editAndContinueEnabled](../../debugger/debug-interface-access/idiasymbol-get-editandcontinueenabled.md)|Recupera il flag che descrive la funzionalità Modifica e continuazione del programma o dell'unità compilato.|  
|[IDiaSymbol::get\_farReturn](../../debugger/debug-interface-access/idiasymbol-get-farreturn.md)|Recupera un flag che indica se la funzione viene utilizzata per un restituita.|  
|[IDiaSymbol::get\_frontEndMajor](../../debugger/debug-interface-access/idiasymbol-get-frontendmajor.md)|Recupera il numero di versione principale front\-end.|  
|[IDiaSymbol::get\_frontEndMinor](../../debugger/debug-interface-access/idiasymbol-get-frontendminor.md)|Recupera il numero di versione secondario front\-end.|  
|[IDiaSymbol::get\_frontEndBuild](../../debugger/debug-interface-access/idiasymbol-get-frontendbuild.md)|Recupera il numero di build front\-end.|  
|[IDiaSymbol::get\_function](../../debugger/debug-interface-access/idiasymbol-get-function.md)|Recupera un flag che indica se il simbolo pubblico fa riferimento a una funzione.|  
|[IDiaSymbol::get\_guid](../../debugger/debug-interface-access/idiasymbol-get-guid.md)|Recupera il GUID del simbolo.|  
|[IDiaSymbol::get\_hasAlloca](../../debugger/debug-interface-access/idiasymbol-get-hasalloca.md)|Recupera un flag che indica se la funzione contiene una chiamata a `alloca`.|  
|[IDiaSymbol::get\_hasAssignmentOperator](../../debugger/debug-interface-access/idiasymbol-get-hasassignmentoperator.md)|Recupera un flag che indica se il tipo di dati definito dall'utente dispone di operatori di assegnazione definito.|  
|[IDiaSymbol::get\_hasCastOperator](../../debugger/debug-interface-access/idiasymbol-get-hascastoperator.md)|Recupera un flag che indica se il tipo di dati definito dall'utente dispone di operatori di cast definito.|  
|[IDiaSymbol::get\_hasDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-hasdebuginfo.md)|Recupera un flag che indica se il modulo contiene le informazioni di debug.|  
|[IDiaSymbol::get\_hasEH](../../debugger/debug-interface-access/idiasymbol-get-haseh.md)|Recupera un flag che indica se la funzione ha gestori di eccezioni C\+\+\-style.|  
|[IDiaSymbol::get\_hasEHa](../../debugger/debug-interface-access/idiasymbol-get-haseha.md)|Recupera un flag che indica se la funzione ha un gestore eccezioni asincrono.|  
|[IDiaSymbol::get\_hasInlAsm](../../debugger/debug-interface-access/idiasymbol-get-hasinlasm.md)|Recupera un flag che indica se la funzione ha assembly inline.|  
|[IDiaSymbol::get\_hasLongJump](../../debugger/debug-interface-access/idiasymbol-get-haslongjump.md)|Recupera un flag che indica se la funzione contiene un comando di longjmp \(parte di gestione delle eccezioni di tipo C.|  
|[IDiaSymbol::get\_hasManagedCode](../../debugger/debug-interface-access/idiasymbol-get-hasmanagedcode.md)|Recupera un flag che indica se il form contiene il codice gestito.|  
|[IDiaSymbol::get\_hasNestedTypes](../../debugger/debug-interface-access/idiasymbol-get-hasnestedtypes.md)|Recupera un flag che indica se il tipo di dati definito dall'utente ha definizioni di tipo annidato.|  
|[IDiaSymbol::get\_hasSecurityChecks](../../debugger/debug-interface-access/idiasymbol-get-hassecuritychecks.md)|Recupera un flag che indica se la funzione o il modulo dispone di controlli di sicurezza compilati in \(tramite l'opzione del compilatore [\/GS \(Controllo sicurezza buffer\)](/visual-cpp/build/reference/gs-buffer-security-check) \).|  
|[IDiaSymbol::get\_hasSEH](../../debugger/debug-interface-access/idiasymbol-get-hasseh.md)|Recupera un flag che indica se la funzione ha gestione delle eccezioni strutturata di tipo win32.|  
|[IDiaSymbol::get\_hasSetJump](../../debugger/debug-interface-access/idiasymbol-get-hassetjump.md)|Recupera un flag che indica se la funzione contiene un comando di setjmp.|  
|[IDiaSymbol::get\_indirectVirtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-indirectvirtualbaseclass.md)|Recupera un flag che indica se il tipo di dati definito dall'utente è una classe base virtuale indiretta.|  
|[IDiaSymbol::get\_InlSpec](../../debugger/debug-interface-access/idiasymbol-get-inlspec.md)|Recupera un flag che indica se la funzione è stata contrassegnata con l'attributo inline.|  
|[IDiaSymbol::get\_interruptReturn](../../debugger/debug-interface-access/idiasymbol-get-interruptreturn.md)|Recupera un flag che indica se la funzione ha un valore dall'istruzione di interruzione.|  
|[IDiaSymbol::get\_intro](../../debugger/debug-interface-access/idiasymbol-get-intro.md)|Recupera un flag che indica se la funzione è la funzione virtuale della classe base.|  
|[IDiaSymbol::get\_isAcceleratorGroupSharedLocal](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorgroupsharedlocal.md)|Recupera un flag che indica se il simbolo corrisponde a una variabile locale condivisa gruppo nel codice compilato per la scelta di AMP C\+\+.|  
|[IDiaSymbol::get\_isAcceleratorPointerTagLiveRange](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorpointertagliverange.md)|Recupera un flag che indica se il simbolo corrisponde *al simbolo del campo di definizione* per il componente tag di una variabile puntatore nel codice compilato per la scelta di AMP C\+\+.  Il simbolo del campo di definizione è la posizione di una variabile di intervallo di indirizzi.|  
|[IDiaSymbol::get\_isAcceleratorStubFunction](../../debugger/debug-interface-access/idiasymbol-get-isacceleratorstubfunction.md)|Indica se il simbolo corrisponde a un simbolo di primo livello di funzione per una shader compilato per una scelta rapida che corrisponde a una chiamata `parallel_for_each`.|  
|[IDiaSymbol::get\_isAggregated](../../debugger/debug-interface-access/idiasymbol-get-isaggregated.md)|Recupera un flag che indica se i dati sono parte di un aggregato di molti simboli.|  
|[IDiaSymbol::get\_isCTypes](../../debugger/debug-interface-access/idiasymbol-get-isctypes.md)|Recupera un flag che indica se il file di simboli contiene i tipi C.|  
|[IDiaSymbol::get\_isCVTCIL](../../debugger/debug-interface-access/idiasymbol-get-iscvtcil.md)|Recupera un flag che indica se il modulo è stato convertito in Microsoft Intermediate Language \(CIL\) comune in codice nativo.|  
|[IDiaSymbol::get\_isDataAligned](../../debugger/debug-interface-access/idiasymbol-get-isdataaligned.md)|Recupera un flag che indica se gli elementi di un tipo di dati definito dall'utente sono allineati a un limite specifico.|  
|[IDiaSymbol::get\_isHLSLData](../../debugger/debug-interface-access/idiasymbol-get-ishlsldata.md)|Specifica se il simbolo rappresenta i dati di alto livello \(HLSL\) di linguaggio di shader.|  
|[IDiaSymbol::get\_isHotpatchable](../../debugger/debug-interface-access/idiasymbol-get-ishotpatchable.md)|Recupera un flag che indica se il modulo è stato compilato con l'opzione del compilatore [\/hotpatch \(Crea immagine con funzionalità di patch a caldo\)](/visual-cpp/build/reference/hotpatch-create-hotpatchable-image).|  
|[IDiaSymbol::get\_isLTCG](../../debugger/debug-interface-access/idiasymbol-get-isltcg.md)|Recupera un flag che indica se il modulo gestito è stato effettuato con il LTCG del linker.|  
|[IDiaSymbol::get\_isMatrixRowMajor](../../debugger/debug-interface-access/idiasymbol-get-ismatrixrowmajor.md)|Specifica se è maggiore della riga.|  
|[IDiaSymbol::get\_isMSILNetmodule](../../debugger/debug-interface-access/idiasymbol-get-ismsilnetmodule.md)|Recupera un flag che indica se il modulo gestito è.  netmodule \(che contiene solo metadati\).|  
|[IDiaSymbol::get\_isMultipleInheritance](../../debugger/debug-interface-access/idiasymbol-get-ismultipleinheritance.md)|Specifica se i punti del puntatore `this` a un membro dati con ereditarietà multipla.|  
|[IDiaSymbol::get\_isNaked](../../debugger/debug-interface-access/idiasymbol-get-isnaked.md)|Recupera un flag che indica se la funzione ha l'attributo [naked](/visual-cpp/cpp/naked-cpp).|  
|[IDiaSymbol::get\_isOptimizedAway](../../debugger/debug-interface-access/idiasymbol-get-isoptimizedaway.md)|Specifica se la variabile è ottimizzata via.|  
|[IDiaSymbol::get\_isPointerBasedOnSymbolValue](../../debugger/debug-interface-access/idiasymbol-get-ispointerbasedonsymbolvalue.md)|Specifica se il puntatore `this` è basato su un valore del simbolo.|  
|[IDiaSymbol::get\_isPointerToDataMember](../../debugger/debug-interface-access/idiasymbol-get-ispointertodatamember.md)|Specifica se il simbolo è un puntatore a un membro dati.|  
|[IDiaSymbol::get\_isPointerToMemberFunction](../../debugger/debug-interface-access/idiasymbol-get-ispointertomemberfunction.md)|Specifica se il simbolo è un puntatore a una funzione membro.|  
|[IDiaSymbol::get\_isReturnValue](../../debugger/debug-interface-access/idiasymbol-get-isreturnvalue.md)|Specifica se la variabile porta un valore restituito.|  
|[IDiaSymbol::get\_isSdl](../../debugger/debug-interface-access/idiasymbol-get-issdl.md)|Specifica se il modulo compilato con l'opzione \/SDL.|  
|[IDiaSymbol::get\_isSingleInheritance](../../debugger/debug-interface-access/idiasymbol-get-issingleinheritance.md)|Specifica se i punti del puntatore `this` a un membro dati con ereditarietà singola.|  
|[IDiaSymbol::get\_isSplitted](../../debugger/debug-interface-access/idiasymbol-get-issplitted.md)|Recupera un flag che indica se i dati sono stati suddivisi in aggregazione di simboli distinti.|  
|[IDiaSymbol::get\_isStatic](../../debugger/debug-interface-access/idiasymbol-get-isstatic.md)|Recupera un flag che indica se una funzione o un livello di thunk è statico.|  
|[IDiaSymbol::get\_isStripped](../../debugger/debug-interface-access/idiasymbol-get-isstripped.md)|Recupera un flag che indica se i simboli privati sono stati rimossi dal file di simboli.|  
|[IDiaSymbol::get\_isVirtualInheritance](../../debugger/debug-interface-access/idiasymbol-get-isvirtualinheritance.md)|Specifica se i punti del puntatore `this` a un membro dati mediante l'ereditarietà virtuale.|  
|[IDiaSymbol::get\_language](../../debugger/debug-interface-access/idiasymbol-get-language.md)|Recupera il linguaggio di origine.|  
|[IDiaSymbol::get\_length](../../debugger/debug-interface-access/idiasymbol-get-length.md)|Recupera il numero di byte di memoria utilizzati dall'oggetto rappresentato da questo simbolo.|  
|[IDiaSymbol::get\_lexicalParent](../../debugger/debug-interface-access/idiasymbol-get-lexicalparent.md)|Recupera un riferimento al padre lessicale del simbolo.|  
|[IDiaSymbol::get\_lexicalParentId](../../debugger/debug-interface-access/idiasymbol-get-lexicalparentid.md)|Recupera l'identificatore padre lessicale del simbolo.|  
|[IDiaSymbol::get\_libraryName](../../debugger/debug-interface-access/idiasymbol-get-libraryname.md)|Recupera il nome file della libreria o del file oggetto da cui è stato caricato.|  
|[IDiaSymbol::get\_liveRangeLength](../../debugger/debug-interface-access/idiasymbol-get-liverangelength.md)|Restituisce la lunghezza dell'intervallo di indirizzi in cui il simbolo locale è valido.|  
|[IDiaSymbol::get\_liveRangeStartAddressSection](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddresssection.md)|Restituisce parte della sezione dell'intervallo di indirizzo iniziale in cui il simbolo locale è valido.|  
|[IDiaSymbol::get\_liveRangeStartAddressOffset](../../debugger/debug-interface-access/idiasymbol-get-liverangestartaddressoffset.md)|Restituisce parte di offset dell'intervallo di indirizzo iniziale in cui il simbolo locale è valido.|  
|[IDiaSymbol::get\_liveRangeStartRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-liverangestartrelativevirtualaddress.md)|Restituisce l'inizio dell'intervallo di indirizzi in cui il simbolo locale è valido.|  
|[IDiaSymbol::get\_locationType](../../debugger/debug-interface-access/idiasymbol-get-locationtype.md)|Recupera il tipo di posizione del simbolo di dati.|  
|[IDiaSymbol::get\_lowerBound](../../debugger/debug-interface-access/idiasymbol-get-lowerbound.md)|Recupera il limite inferiore di una dimensione della matrice FORTRAN.|  
|[IDiaSymbol::get\_lowerBoundId](../../debugger/debug-interface-access/idiasymbol-get-lowerboundid.md)|Recupera l'identificatore del simbolo del limite inferiore di una dimensione della matrice FORTRAN.|  
|[IDiaSymbol::get\_machineType](../../debugger/debug-interface-access/idiasymbol-get-machinetype.md)|Recupera il tipo di cpu di destinazione.|  
|[IDiaSymbol::get\_managed](../../debugger/debug-interface-access/idiasymbol-get-managed.md)|Recupera un flag che indica se il simbolo si riferisce al codice gestito.|  
|[IDiaSymbol::get\_memorySpaceKind](../../debugger/debug-interface-access/idiasymbol-get-memoryspacekind.md)|Recupera il tipo dello spazio di memoria.|  
|[IDiaSymbol::get\_msil](../../debugger/debug-interface-access/idiasymbol-get-msil.md)|Recupera un flag che indica se il simbolo si riferisce al codice Microsoft Intermediate Language \(MSIL\).|  
|[IDiaSymbol::get\_name](../../debugger/debug-interface-access/idiasymbol-get-name.md)|Recupera il nome del simbolo.|  
|[IDiaSymbol::get\_nested](../../debugger/debug-interface-access/idiasymbol-get-nested.md)|Recupera un flag che indica se il tipo di dati definito dall'utente è annidato.|  
|[IDiaSymbol::get\_noInline](../../debugger/debug-interface-access/idiasymbol-get-noinline.md)|Recupera un flag che indica se la funzione contrassegnata con l'attributo [noinline](/visual-cpp/cpp/noinline).|  
|[IDiaSymbol::get\_noReturn](../../debugger/debug-interface-access/idiasymbol-get-noreturn.md)|Recupera un flag che indica se la funzione è stata dichiarata con l'attributo [noreturn](/visual-cpp/cpp/noreturn).|  
|[IDiaSymbol::get\_noStackOrdering](../../debugger/debug-interface-access/idiasymbol-get-nostackordering.md)|Recupera un flag che indica se nessun ordine dello stack può essere eseguito come parte del controllo del buffer dello stack.|  
|[IDiaSymbol::get\_notReached](../../debugger/debug-interface-access/idiasymbol-get-notreached.md)|Recupera un flag che indica se la funzione o non viene raggiunta mai.|  
|[IDiaSymbol::get\_numberOfAcceleratorPointerTags](../../debugger/debug-interface-access/idiasymbol-get-numberofacceleratorpointertags.md)|Restituisce il numero dei tag del puntatore di scelta rapida nella funzione dello stub di AMP C\+\+.|  
|[IDiaSymbol::get\_numberOfModifiers](../../debugger/debug-interface-access/idiasymbol-get-numberofmodifiers.md)|Recupera il numero dei modificatori che si applicano al tipo originale.|  
|[IDiaSymbol::get\_numberOfRegisterIndices](../../debugger/debug-interface-access/idiasymbol-get-numberofregisterindices.md)|Recupera il numero di indici di log.|  
|[IDiaSymbol::get\_numberOfRows](../../debugger/debug-interface-access/idiasymbol-get-numberofrows.md)|Recupera il numero di righe della matrice.|  
|[IDiaSymbol::get\_numberOfColumns](../../debugger/debug-interface-access/idiasymbol-get-numberofcolumns.md)|Recupera il numero di colonne nella matrice.|  
|[IDiaSymbol::get\_objectFileName](../../debugger/debug-interface-access/idiasymbol-get-objectfilename.md)|Recupera il nome file dell'oggetto.|  
|[IDiaSymbol::get\_objectPointerType](../../debugger/debug-interface-access/idiasymbol-get-objectpointertype.md)|Recupera il tipo di puntatore a un oggetto per il metodo della classe.|  
|[IDiaSymbol::get\_oemId](../../debugger/debug-interface-access/idiasymbol-get-oemid.md)|Recupera il valore `oemId` del simbolo.|  
|[IDiaSymbol::get\_oemSymbolId](../../debugger/debug-interface-access/idiasymbol-get-oemsymbolid.md)|Recupera il valore `oemSymbolId` del simbolo.|  
|[IDiaSymbol::get\_offset](../../debugger/debug-interface-access/idiasymbol-get-offset.md)|Recuperare l'offset della posizione del simbolo.|  
|[IDiaSymbol::get\_optimizedCodeDebugInfo](../../debugger/debug-interface-access/idiasymbol-get-optimizedcodedebuginfo.md)|Recupera un flag che indica se la funzione o l'etichetta contiene il codice nonché le informazioni di debug ottimizzati.|  
|[IDiaSymbol::get\_overloadedOperator](../../debugger/debug-interface-access/idiasymbol-get-overloadedoperator.md)|Recupera un flag che indica se il tipo di dati definito dall'utente ha eseguito l'overload degli operatori.|  
|[IDiaSymbol::get\_packed](../../debugger/debug-interface-access/idiasymbol-get-packed.md)|Recupera un flag che indica se il tipo di dati definito dall'utente è wrapping.|  
|[IDiaSymbol::get\_platform](../../debugger/debug-interface-access/idiasymbol-get-platform.md)|Recupera il tipo di piattaforma per cui il programma o il modulo è stato compilato.|  
|[IDiaSymbol::get\_pure](../../debugger/debug-interface-access/idiasymbol-get-pure.md)|Recupera un flag che indica se è la funzione virtuale pure.|  
|[IDiaSymbol::get\_rank](../../debugger/debug-interface-access/idiasymbol-get-rank.md)|Recupera il numero di dimensioni di una matrice multidimensionale FORTRAN.|  
|[IDiaSymbol::get\_reference](../../debugger/debug-interface-access/idiasymbol-get-reference.md)|Recupera un flag che indica se il tipo di puntatore è un riferimento.|  
|[IDiaSymbol::get\_registerId](../../debugger/debug-interface-access/idiasymbol-get-registerid.md)|Recupera l'indicatore di log della posizione.|  
|[IDiaSymbol::get\_registerType](../../debugger/debug-interface-access/idiasymbol-get-registertype.md)|Recupera il tipo di log.|  
|[IDiaSymbol::get\_relativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-relativevirtualaddress.md)|Recupera indirizzo virtuale \(RVA\) della posizione.|  
|[IDiaSymbol::get\_restrictedType](../../debugger/debug-interface-access/idiasymbol-get-restrictedtype.md)|Specifica se il puntatore `this` è contrassegnato come limitato.|  
|[IDiaSymbol::get\_samplerSlot](../../debugger/debug-interface-access/idiasymbol-get-samplerslot.md)|Recupera lo slot della raccolta di test.|  
|[IDiaSymbol::get\_scoped](../../debugger/debug-interface-access/idiasymbol-get-scoped.md)|Recupera un flag che indica se il tipo di dati definito dall'utente viene visualizzato in un ambito lessicale globali.|  
|[IDiaSymbol::get\_signature](../../debugger/debug-interface-access/idiasymbol-get-signature.md)|Recupera il valore della firma del simbolo.|  
|[IDiaSymbol::get\_sizeInUdt](../../debugger/debug-interface-access/idiasymbol-get-sizeinudt.md)|Recupera la dimensione di un membro di un tipo definito da.|  
|[IDiaSymbol::get\_slot](../../debugger/debug-interface-access/idiasymbol-get-slot.md)|Recupera il numero di slot della posizione.|  
|[IDiaSymbol::get\_sourceFileName](../../debugger/debug-interface-access/idiasymbol-get-sourcefilename.md)|Recupera il nome del file di origine.|  
|[IDiaSymbol::getSrcLineOnTypeDefn](../../debugger/debug-interface-access/idiasymbol-getsrclineontypedefn.md)|Recupera il file di origine e il numero di riga che indica dove un tipo definito dall'utente specificato non è definito.|  
|[IDiaSymbol::get\_stride](../../debugger/debug-interface-access/idiasymbol-get-stride.md)|Recupera la strada della matrice o della matrice strided.|  
|[IDiaSymbol::get\_subType](../../debugger/debug-interface-access/idiasymbol-get-subtype.md)|Recupera il tipo in.|  
|[IDiaSymbol::get\_subTypeId](../../debugger/debug-interface-access/idiasymbol-get-subtypeid.md)|Recupera la sotto digitare ID.|  
|[IDiaSymbol::get\_symbolsFileName](../../debugger/debug-interface-access/idiasymbol-get-symbolsfilename.md)|Recupera il nome del file da cui i simboli sono stati caricati.|  
|[IDiaSymbol::get\_symIndexId](../../debugger/debug-interface-access/idiasymbol-get-symindexid.md)|Recupera l'identificatore univoco del simbolo.|  
|[IDiaSymbol::get\_symTag](../../debugger/debug-interface-access/idiasymbol-get-symtag.md)|Recupera il classificatore del tipo del simbolo.|  
|[IDiaSymbol::get\_targetOffset](../../debugger/debug-interface-access/idiasymbol-get-targetoffset.md)|Recupera la sezione di offset di una destinazione di thunk.|  
|[IDiaSymbol::get\_targetRelativeVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetrelativevirtualaddress.md)|Recupera indirizzo virtuale relativo \(RVA\) di una destinazione di thunk.|  
|[IDiaSymbol::get\_targetSection](../../debugger/debug-interface-access/idiasymbol-get-targetsection.md)|Recupera la sezione indirizzo di una destinazione di thunk.|  
|[IDiaSymbol::get\_targetVirtualAddress](../../debugger/debug-interface-access/idiasymbol-get-targetvirtualaddress.md)|Recupera indirizzo virtuale \(VA\) di una destinazione di thunk.|  
|[IDiaSymbol::get\_textureSlot](../../debugger/debug-interface-access/idiasymbol-get-textureslot.md)|Recupera lo slot di trama.|  
|[IDiaSymbol::get\_thisAdjust](../../debugger/debug-interface-access/idiasymbol-get-thisadjust.md)|Recupera il controller master logico `this` per il metodo.|  
|[IDiaSymbol::get\_thunkOrdinal](../../debugger/debug-interface-access/idiasymbol-get-thunkordinal.md)|Recupera il tipo di thunk di funzione.|  
|[IDiaSymbol::get\_timeStamp](../../debugger/debug-interface-access/idiasymbol-get-timestamp.md)|Recupera il timestamp del file eseguibile sottostante.|  
|[IDiaSymbol::get\_token](../../debugger/debug-interface-access/idiasymbol-get-token.md)|Recupera il token di metadati di una funzione o una variabile gestita.|  
|[IDiaSymbol::get\_type](../../debugger/debug-interface-access/idiasymbol-get-type.md)|Recupera un riferimento alla firma della funzione.|  
|[IDiaSymbol::get\_typeId](../../debugger/debug-interface-access/idiasymbol-get-typeid.md)|Recupera l'identificatore di tipo del simbolo.|  
|[IDiaSymbol::get\_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)|Recupera una matrice di valori di tipo compilatore specifici per questo simbolo.|  
|[IDiaSymbol::get\_typeIds](../../debugger/debug-interface-access/idiasymbol-get-typeids.md)|Recupera una matrice di valori compilatore specifici dell'identificatore di tipo per questo simbolo.|  
|[IDiaSymbol::get\_uavSlot](../../debugger/debug-interface-access/idiasymbol-get-uavslot.md)|Recupera lo slot di uav.|  
|[IDiaSymbol::get\_udtKind](../../debugger/debug-interface-access/idiasymbol-get-udtkind.md)|Recupera la varietà di tipo definito dall'utente \(UDT\).|  
|[IDiaSymbol::get\_unalignedType](../../debugger/debug-interface-access/idiasymbol-get-unalignedtype.md)|Recupera un flag che indica se il tipo di dati definito dall'utente non è allineato.|  
|[IDiaSymbol::get\_undecoratedName](../../debugger/debug-interface-access/idiasymbol-get-undecoratedname.md)|Recupera il nome non decorato per C\+\+ decorato, o il collegamento, nome.|  
|[IDiaSymbol::get\_undecoratedNameEx](../../debugger/debug-interface-access/idiasymbol-get-undecoratednameex.md)|L'estensione del metodo `get_undecoratedName` che recupera il nome non decorato in base al valore di un campo di estensione.|  
|[IDiaSymbol::get\_unmodifiedTypeId](../../debugger/debug-interface-access/idiasymbol-get-unmodifiedtypeid.md)|Recupera l'id del tipo \(non\) originale.|  
|[IDiaSymbol::get\_upperBound](../../debugger/debug-interface-access/idiasymbol-get-upperbound.md)|Recupera il limite superiore della dimensione di una matrice FORTRAN.|  
|[IDiaSymbol::get\_upperBoundId](../../debugger/debug-interface-access/idiasymbol-get-upperboundid.md)|Recupera l'identificatore del simbolo del limite superiore della dimensione di una matrice FORTRAN.|  
|[IDiaSymbol::get\_value](../../debugger/debug-interface-access/idiasymbol-get-value.md)|Recupera il valore di una costante.|  
|[IDiaSymbol::get\_virtual](../../debugger/debug-interface-access/idiasymbol-get-virtual.md)|Recupera un flag che indica se la funzione è virtuale.|  
|[IDiaSymbol::get\_virtualAddress](../../debugger/debug-interface-access/idiasymbol-get-virtualaddress.md)|Recupera indirizzo virtuale \(VA\) della posizione.|  
|[IDiaSymbol::get\_virtualBaseClass](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseclass.md)|Recupera un flag che indica se il tipo di dati definito dall'utente è una classe base virtuale.|  
|[IDiaSymbol::get\_virtualBaseDispIndex](../../debugger/debug-interface-access/idiasymbol-get-virtualbasedispindex.md)|Recupera l'indice alla tabella di navigazione base virtuale.|  
|[IDiaSymbol::get\_virtualBaseOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbaseoffset.md)|Recuperare l'offset nella tabella di funzioni virtuali di una funzione virtuale.|  
|[IDiaSymbol::get\_virtualBasePointerOffset](../../debugger/debug-interface-access/idiasymbol-get-virtualbasepointeroffset.md)|Recuperare l'offset del puntatore di base virtuale.|  
|[IDiaSymbol::get\_virtualBaseTableType](../../debugger/debug-interface-access/idiasymbol-get-virtualbasetabletype.md)|Recupera il tipo di puntatore base virtuale della tabella.|  
|[IDiaSymbol::get\_virtualTableShape](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshape.md)|Recupera l'interfaccia del simbolo del tipo di tabella virtuale per un tipo definito dall'utente.|  
|[IDiaSymbol::get\_virtualTableShapeId](../../debugger/debug-interface-access/idiasymbol-get-virtualtableshapeid.md)|Recupera l'identificatore virtuale di forma della tabella dei simboli.|  
|[IDiaSymbol::get\_volatileType](../../debugger/debug-interface-access/idiasymbol-get-volatiletype.md)|Recupera un flag che indica se il tipo di dati definito dall'utente è volatile.|  
  
## Note  
  
## Note per i chiamanti  
 Leggi questa interfaccia chiamando uno dei metodi seguenti:  
  
-   [IDiaEnumSymbols::Item](../../debugger/debug-interface-access/idiaenumsymbols-item.md)  
  
-   [IDiaEnumSymbols::Next](../../debugger/debug-interface-access/idiaenumsymbols-next.md)  
  
-   [IDiaEnumSymbolsByAddr::Next](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-next.md)  
  
-   [IDiaEnumSymbolsByAddr::Prev](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-prev.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyaddr.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByRVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyrva.md)  
  
-   [IDiaEnumSymbolsByAddr::symbolByVA](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr-symbolbyva.md)  
  
-   [IDiaSession::findSymbolByAddr](../../debugger/debug-interface-access/idiasession-findsymbolbyaddr.md)  
  
-   [IDiaSession::findSymbolByRVA](../../debugger/debug-interface-access/idiasession-findsymbolbyrva.md)  
  
-   [IDiaSession::findSymbolByRVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyrvaex.md)  
  
-   [IDiaSession::findSymbolByVA](../../debugger/debug-interface-access/idiasession-findsymbolbyva.md)  
  
-   [IDiaSession::findSymbolByVAEx](../../debugger/debug-interface-access/idiasession-findsymbolbyvaex.md)  
  
-   [IDiaSession::findSymbolByToken](../../debugger/debug-interface-access/idiasession-findsymbolbytoken.md)  
  
-   [IDiaSession::symbolById](../../debugger/debug-interface-access/idiasession-symbolbyid.md)  
  
-   [IDiaStackWalkHelper::symbolForVA](../../debugger/debug-interface-access/idiastackwalkhelper-symbolforva.md)  
  
-   [IDiaSymbol::get\_types](../../debugger/debug-interface-access/idiasymbol-get-types.md)  
  
## Esempio  
 In questo esempio viene illustrato come visualizzare le variabili locali per una funzione a un indirizzo virtuale relativo specificato.  Viene inoltre illustrato come i simboli di diversi tipi correlati tra loro.  
  
> [!NOTE]
>  `CDiaBSTR` è una classe che esegue il wrapping `BSTR` e automaticamente handle che libera la stringa durante la creazione di istanze area di validità.  
  
```cpp#  
void DumpLocalVars( DWORD rva, IDiaSession *pSession )  
{  
    CComPtr< IDiaSymbol > pBlock;  
    if ( FAILED( psession->findSymbolByRVA( rva, SymTagBlock, &pBlock ) ) )  
    {  
        Fatal( "Failed to find symbols by RVA" );  
    }  
    CComPtr< IDiaSymbol > pscope;  
    for ( ; pBlock != NULL; )  
    {  
        CComPtr< IDiaEnumSymbols > pEnum;  
        // local data search  
        if ( FAILED( pBlock->findChildren( SymTagNull, NULL, nsNone, &pEnum ) ) )  
        {  
            Fatal( "Local scope findChildren failed" );  
        }  
        CComPtr< IDiaSymbol > pSymbol;  
        DWORD tag;  
        DWORD celt;  
        while ( pEnum != NULL &&  
                SUCCEEDED( pEnum->Next( 1, &pSymbol, &celt ) ) &&  
                celt == 1)  
        {  
            pSymbol->get_symTag( &tag );  
            if ( tag == SymTagData )  
            {  
                CDiaBSTR name;  
                DWORD    kind;  
                pSymbol->get_name( &name );  
                pSymbol->get_dataKind( &kind );  
                if ( name != NULL )  
                    wprintf_s( L"\t%s (%s)\n", name, szDataKinds[ kind ] );  
            }  
            else if ( tag == SymTagAnnotation )  
            {  
                CComPtr< IDiaEnumSymbols > pValues;  
                // local data search  
                wprintf_s( L"\tAnnotation:\n" );  
                if ( FAILED( pSymbol->findChildren( SymTagNull, NULL, nsNone, &pValues ) ) )  
                    Fatal( "Annotation findChildren failed" );  
                pSymbol = NULL;  
                while ( pValues != NULL &&  
                        SUCCEEDED( pValues->Next( 1, &pSymbol, &celt ) ) &&  
                        celt == 1 )  
                {  
                    CComVariant value;  
                    if ( pSymbol->get_value( &value ) != S_OK )  
                        Fatal( "No value for annotation data." );  
                    wprintf_s( L"\t\t%ws\n", value.bstrVal );  
                    pSymbol = NULL;  
                }  
            }  
            pSymbol = NULL;  
        }  
        pBlock->get_symTag( &tag );   
        if ( tag == SymTagFunction )    // stop when at function scope  
            break;  
        // move to lexical parent  
        CComPtr< IDiaSymbol > pParent;  
        if ( SUCCEEDED( pBlock->get_lexicalParent( &pParent ) )  
            && pParent != NULL ) {  
            pBlock = pParent;  
        }  
        else  
        {  
            Fatal( "Finding lexical parent failed." );  
        }  
    };  
}  
```  
  
## Requisiti  
 `Header:` Dia2.h  
  
 Raccolta: diaguids.lib  
  
 DLL: msdia80.dll  
  
## Vedere anche  
 [Interfacce \(Debug Interface Access SDK\)](../../debugger/debug-interface-access/interfaces-debug-interface-access-sdk.md)   
 [IDiaEnumSymbolsByAddr](../../debugger/debug-interface-access/idiaenumsymbolsbyaddr.md)   
 [IDiaEnumSymbols](../../debugger/debug-interface-access/idiaenumsymbols.md)   
 [IDiaSession](../../debugger/debug-interface-access/idiasession.md)   
 [Gerarchia di classi dei tipi di simboli](../../debugger/debug-interface-access/class-hierarchy-of-symbol-types.md)   
 [Simboli e relativi tag](../../debugger/debug-interface-access/symbols-and-symbol-tags.md)   
 [Compilando](../../debugger/debug-interface-access/compiland.md)