---
title: "Set di regole minime native | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2d898bc4-fba5-472e-8f09-b0c6b511c5a3
caps.latest.revision: 3
caps.handback.revision: 3
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Set di regole minime native
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le regole Microsoft Native Minimum Rules sono orientate ai problemi più critici del codice nativo, inclusi i potenziali problemi di sicurezza e gli arresti anomali delle applicazioni.  È necessario includere questo set di regole in ogni set di regole personalizzato, creato per i progetti nativi.  
  
|Regola|Descrizione|  
|------------|-----------------|  
|[C6001](../code-quality/c6001.md)|Utilizzo di memoria non inizializzata.|  
|[C6011](../code-quality/c6011.md)|Dereferenziazione del puntatore NULL.|  
|[C6029](../code-quality/c6029.md)|Utilizzo del valore non verificato.|  
|[C6053](../code-quality/c6053.md)|Terminazione zero da chiamata|  
|[C6059](../code-quality/c6059.md)|Concatenazione non valida|  
|[C6063](../code-quality/c6063.md)|Argomento di tipo stringa mancante per formattare la funzione|  
|[C6064](../code-quality/c6064.md)|Argomento Integer mancante per formattare la funzione|  
|[C6066](../code-quality/c6066.md)|Argomento puntatore mancante per formattare la funzione|  
|[C6067](../code-quality/c6067.md)|Argomento puntatore a stringa mancante per formattare la funzione|  
|[C6101](../code-quality/c6101.md)|Restituzione di memoria non inizializzata|  
|[C6200](../code-quality/c6200.md)|L'indice supera il limite massimo del buffer|  
|[C6201](../code-quality/c6201.md)|L'indice supera il limite massimo del buffer di stack|  
|[C6270](../code-quality/c6270.md)|Argomento Float mancante per formattare la funzione|  
|[C6271](../code-quality/c6271.md)|Argomento aggiuntivo per formattare la funzione|  
|[C6272](../code-quality/c6272.md)|Argomento non di tipo float per formattare funzione|  
|[C6273](../code-quality/c6273.md)|Argomento non Integer per formattare la funzione|  
|[C6274](../code-quality/c6274.md)|Argomento non di tipo Carattere per formattare la funzione|  
|[C6276](../code-quality/c6276.md)|Cast della stringa non valido|  
|[C6277](../code-quality/c6277.md)|Chiamata CreateProcess non valida|  
|[C6284](../code-quality/c6284.md)|Argomento oggetto non valido per formattare la funzione|  
|[C6290](../code-quality/c6290.md)|Precedenza Logical\-Not Bitwise\-And|  
|[C6291](../code-quality/c6291.md)|Precedenza Logical\-Not Bitwise\-Or|  
|[C6302](../code-quality/c6302.md)|Argomento stringa di caratteri non valido per formattare la funzione|  
|[C6303](../code-quality/c6303.md)|Argomento non valido per una stringa con caratteri estesi per formattare la funzione|  
|[C6305](../code-quality/c6305.md)|Utilizzo non corrispondente di conteggio e di dimensione|  
|[C6306](../code-quality/c6306.md)|Chiamata di funzione dell'argomento variabile non corretto|  
|[C6328](../code-quality/c6328.md)|Tipo argomento potenzialmente non corrispondente|  
|[C6385](../code-quality/c6385.md)|Sovraccarico di lettura|  
|[C6386](../code-quality/c6386.md)|Sovraccarico di scrittura|  
|[C6387](../code-quality/c6387.md)|Valore del parametro non valido|  
|[C6500](../code-quality/c6500.md)|Proprietà di attributo non valida|  
|[C6501](../code-quality/c6501.md)|Valori delle proprietà di attributo in conflitto|  
|[C6503](../code-quality/c6503.md)|Riferimenti non possono essere null.|  
|[C6504](../code-quality/c6504.md)|Null su tipo non Puntatore|  
|[C6505](../code-quality/c6505.md)|MustCheck su void|  
|[C6506](../code-quality/c6506.md)|Dimensione del buffer non su tipo Puntatore o Vettore|  
|[C6507](http://msdn.microsoft.com/it-it/18f88cd1-d035-4403-a6a4-12dd0affcf21)|Mancata corrispondenza di Null in dereferenza a zero|  
|[C6508](../code-quality/c6508.md)|Accesso alla costante in scrittura|  
|[C6509](../code-quality/c6509.md)|Ritorno utilizzato in precondizione|  
|[C6510](../code-quality/c6510.md)|Null terminato su non puntatore|  
|[C6511](../code-quality/c6511.md)|MustCheck deve essere Yes o No|  
|[C6513](../code-quality/c6513.md)|Dimensione elemento senza dimensioni del buffer|  
|[C6514](../code-quality/c6514.md)|Le dimensioni del buffer superano le dimensioni dell'array|  
|[C6515](../code-quality/c6515.md)|Dimensione del buffer su Non Puntatore|  
|[C6516](../code-quality/c6516.md)|Nessuna proprietà sull'attributo|  
|[C6517](../code-quality/c6517.md)|Dimensione valida nel buffer non leggibile|  
|[C6518](../code-quality/c6518.md)|Dimensioni scrivibili su buffer non scrivibile|  
|[C6519](http://msdn.microsoft.com/it-it/2b6326b0-0539-4d26-8fb1-720114933232)|Annotazione non valida: il valore della proprietà 'NeedsRelease' deve essere Yes o No.|  
|[C6521](http://msdn.microsoft.com/it-it/e98d0ae3-6f13-47b2-9a15-15d4055af9ef)|Dereferenziazione non valida della stringa di dimensione|  
|[C6522](../code-quality/c6522.md)|Tipo della dimensione della stringa non valido|  
|[C6523](http://msdn.microsoft.com/it-it/11397a31-b224-46b0-afb7-d49ca576a3bb)|Parametro della dimensione della stringa non valido|  
|[C6525](../code-quality/c6525.md)|Percorso della dimensione della stringa irraggiungibile|  
|[C6526](http://msdn.microsoft.com/it-it/59c590c7-0098-4166-a1ac-87f324596002)|Tipo della dimensione del buffer della stringa non valido|  
|[C6527](../code-quality/c6527.md)|Annotazione non valida: la proprietà 'NeedsRelease' non può essere utilizzata con valori di tipo void.|  
|[C6530](../code-quality/c6530.md)|Stile formato stringa non riconosciuto|  
|[C6540](../code-quality/c6540.md)|L'utilizzo delle annotazioni di attributo in questa funzione invalida tutte le relative annotazioni \_\_declspec esistenti.|  
|[C6551](../code-quality/c6551.md)|Specifica di dimensione non valida: espressione non analizzabile|  
|[C6552](../code-quality/c6552.md)|Deref\= o Notref\= non valido : espressione non analizzabile|  
|[C6701](../code-quality/c6701.md)|Il valore non è un valore Yes\/No\/Maybe valido:|  
|[C6702](../code-quality/c6702.md)|Il valore non è una stringa.|  
|[C6703](../code-quality/c6703.md)|Il valore non è un numero.|  
|[C6704](../code-quality/c6704.md)|Errore imprevisto di espressione di annotazione:|  
|[C6705](../code-quality/c6705.md)|Il numero degli argomenti previsto per l'annotazione non corrisponde all'effettivo numero di argomenti per l'annotazione|  
|[C6706](../code-quality/c6706.md)|Errore di annotazione imprevisto per l'annotazione|  
|[C28021](../code-quality/c28021.md)|Il parametro che viene annotato deve essere un puntatore|  
|[C28182](../code-quality/c28182.md)|Deferenziazione del puntatore NULL.  Il puntatore contiene lo stesso valore null come su un altro puntatore.|  
|[C28202](../code-quality/c28202.md)|Riferimento non valido al membro non statico.|  
|[C28203](../code-quality/c28203.md)|Riferimento ambiguo al membro di classe.|  
|[C28205](../code-quality/c28205.md)|\_Success\_ or \_On\_failure\_ utilizzato in un contesto non valido|  
|[C28206](../code-quality/c28206.md)|L'operando sinistro punta a uno struct. Utilizzare '\-\>'|  
|[C28207](../code-quality/c28207.md)|L'operando sinistro è uno struct. Utilizzare '.'|  
|[C28210](../code-quality/c28210.md)|Le annotazioni per il contesto \_\_on\_failure non devono trovarsi in un pre\-contesto esplicito:|  
|[C28211](../code-quality/c28211.md)|Nome di contesto statico previsto per SAL\_context|  
|[C28212](../code-quality/c28212.md)|Espressione del puntatore prevista per l'annotazione|  
|[C28213](../code-quality/c28213.md)|L'annotazione \_Use\_decl\_annotations\_ deve essere utilizzata per fare riferimento, senza alcuna modifica, a una dichiarazione precedente.|  
|[C28214](../code-quality/c28214.md)|I nomi di parametro di attributo devono essere p1...p9|  
|[C28215](../code-quality/c28215.md)|Impossibile applicare typefix a un parametro che già dispone di un typefix|  
|[C28216](../code-quality/c28216.md)|L'annotazione di checkReturn viene applicata solo alle post\-condizioni per il parametro di funzione specifico.|  
|[C28217](../code-quality/c28217.md)|Per la funzione il numero di parametri per l'annotazione non corrisponde con quello trovato nel file|  
|[C28218](../code-quality/c28218.md)|Per il parametro della funzione, il parametro di annotazione non corrisponde a quello trovato sul file|  
|[C28219](../code-quality/c28219.md)|Membro di enumerazione previsto per l'annotazione del parametro nell'annotazione|  
|[C28220](../code-quality/c28220.md)|Espressione Integer prevista per annotare il parametro nell'annotazione|  
|[C28221](../code-quality/c28221.md)|Espressione stringa prevista per il parametro nell'annotazione|  
|[C28222](../code-quality/c28222.md)|Previsto \_\_yes, \_\_no, o \_\_maybe per l'annotazione|  
|[C28223](../code-quality/c28223.md)|Impossibile trovare parametro Token o identificatore previsto per l'annotazione|  
|[C28224](../code-quality/c28224.md)|L'annotazione richiede parametri.|  
|[C28225](../code-quality/c28225.md)|Non è stato trovato il numero corretto di parametri necessari nell'annotazione|  
|[C28226](../code-quality/c28226.md)|L'annotazione non può essere anche un PrimOp \(nella dichiarazione corrente\).|  
|[C28227](../code-quality/c28227.md)|L'annotazione non può essere anche un PrimOp \(vedere la dichiarazione precedente\).|  
|[C28228](../code-quality/c28228.md)|Parametro di annotazioni: impossibile utilizzare il tipo nelle annotazioni|  
|[C28229](../code-quality/c28229.md)|L'annotazione non supporta parametri.|  
|[C28230](../code-quality/c28230.md)|Il tipo del parametro non include membri.|  
|[C28231](../code-quality/c28231.md)|L'annotazione è valida soltanto su array|  
|[C28232](../code-quality/c28232.md)|pre, post o deref non applicato ad alcuna annotazione.|  
|[C28233](../code-quality/c28233.md)|pre, post o deref applicato a un blocco.|  
|[C28234](../code-quality/c28234.md)|L'espressione \_\_at non si applica alla funzione corrente.|  
|[C28235](../code-quality/c28235.md)|La funzione non può fungere autonomamente da annotazione.|  
|[C28236](../code-quality/c28236.md)|L'annotazione non può essere utilizzata in un'espressione.|  
|[C28237](../code-quality/c28237.md)|L'annotazione sul parametro non è più supportata|  
|[C28238](../code-quality/c28238.md)|L'annotazione sul parametro presenta più di un valore, stringValue e longValue.  Utilizzare paramn\=xxx.|  
|[C28239](../code-quality/c28239.md)|L'annotazione sul parametro presenta sia stringValue, o longValue, che paramn\=xxx.  Utilizzare solo paramn\=xxx.|  
|[C28240](../code-quality/c28240.md)|L'annotazione sul parametro presenta param2 ma nessun param1.|  
|[C28241](../code-quality/c28241.md)|L'annotazione per la funzione sul parametro non è riconosciuto|  
|[C28243](../code-quality/c28243.md)|L'annotazione per la funzione sul parametro richiede più dereferenziazioni di quante ne siano consentite dall'effettivo tipo annotato|  
|[C28245](../code-quality/c28245.md)|L'annotazione per la funzione annota 'this' in una funzione non membro.|  
|[C28246](../code-quality/c28246.md)|Il parametro dell'annotazione per la funzione non corrisponde al tipo del parametro.|  
|[C28250](../code-quality/c28250.md)|Annotazione non coerente per la funzione: l'istanza precedente ha un errore.|  
|[C28251](../code-quality/c28251.md)|Annotazione non coerente per la funzione: questa istanza ha un errore.|  
|[C28252](../code-quality/c28252.md)|Annotazione non coerente per la funzione: il parametro include altre annotazioni in questa istanza.|  
|[C28253](../code-quality/c28253.md)|Annotazione non coerente per la funzione: il parametro include altre annotazioni in questa istanza.|  
|[C28254](../code-quality/c28254.md)|dynamic\_cast\<\>\(\) non è supportato nelle annotazioni.|  
|[C28262](../code-quality/c28262.md)|Errore di sintassi nell'annotazione rilevato nella funzione per l'annotazione|  
|[C28263](../code-quality/c28263.md)|Errore di sintassi in un'annotazione condizionale rilevato per l'annotazione intrinseca|  
|[C28264](http://msdn.microsoft.com/it-it/bf6ea983-a06e-4752-a042-747a7dbf338c)|I valori sell'elenco dei risultati devono essere costanti.|  
|[C28267](../code-quality/c28267.md)|Errore di sintassi nell'annotazione rilevato nella funzione per l'annotazione|  
|[C28272](../code-quality/c28272.md)|L'annotazione per la funzione, il parametro durante l'analisi non è coerente con la dichiarazione della funzione.|  
|[C28273](../code-quality/c28273.md)|Per la funzione, le tracce non sono coerenti con la dichiarazione della funzione.|  
|[C28275](../code-quality/c28275.md)|Il parametro per \_Macro\_value\_ è null.|  
|[C28279](../code-quality/c28279.md)|Per il simbolo, è stato trovato un 'begin' senza il corrispondente 'end'.|  
|[C28280](../code-quality/c28280.md)|Per il simbolo, è stato trovato un 'end' senza un 'begin' corrispondente.|  
|[C28282](../code-quality/c28282.md)|Le stringhe di formato devono essere presenti nelle precondizioni|  
|[C28285](../code-quality/c28285.md)|Per la funzione, errore di sintassi nel parametro|  
|[C28286](../code-quality/c28286.md)|Per la funzione, errore di sintassi nei pressi della fine|  
|[C28287](../code-quality/c28287.md)|Per la funzione, errore di sintassi nell'annotazione \_At\_\(\) \(nome parametro non riconosciuto\).|  
|[C28288](../code-quality/c28288.md)|Per la funzione, errore di sintassi nell'annotazione \_At\_\(\) \(nome parametro non valido\).|  
|[C28289](../code-quality/c28289.md)|Per la funzione: ReadableTo o WritableTo non dispone di limit\-spec come parametro.|  
|[C28290](../code-quality/c28290.md)|L'annotazione per la funzione contiene un numero di riferimenti esterni maggiore del numero di parametri effettivi.|  
|[C28291](../code-quality/c28291.md)|Il post null\/notnull al livello deref 0 è privo di significato per la funzione.|  
|[C28300](../code-quality/c28300.md)|Operandi dell'espressione di tipi incompatibili per l'operatore|  
|[C28301](../code-quality/c28301.md)|Nessun annotazione per la prima dichiarazione di funzione.|  
|[C28302](../code-quality/c28302.md)|Un operatore aggiuntivo di \_Deref\_ è stato rilevato nell'annotazione.|  
|[C28303](../code-quality/c28303.md)|Un operatore ambiguo di \_Deref\_ è stato trovato nell'annotazione.|  
|[C28304](../code-quality/c28304.md)|Un operatore \_Notref\_ non correttamente posizionato è stato trovato applicato al token.|  
|[C28305](../code-quality/c28305.md)|E' stato individuato un errore durante l'analisi di un token.|  
|[C28350](../code-quality/c28350.md)|L'annotazione descrive una situazione non applicabile in modo condizionale.|  
|[C28351](../code-quality/c28351.md)|L'annotazione descrive dove non è possibile utilizzare un valore dinamico \(variabile\) nella condizione.|