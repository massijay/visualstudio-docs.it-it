---
title: "CA2000: Eliminare gli oggetti prima di perdere l&#39;ambito | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2000"
  - "Dispose objects before losing scope"
  - "DisposeObjectsBeforeLosingScope"
helpviewer_keywords: 
  - "CA2000"
  - "DisposeObjectsBeforeLosingScope"
ms.assetid: 0c3d7d8d-b94d-46e8-aa4c-38df632c1463
caps.latest.revision: 32
caps.handback.revision: 32
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2000: Eliminare gli oggetti prima di perdere l&#39;ambito
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DisposeObjectsBeforeLosingScope|  
|CheckId|CA2000|  
|Category|Microsoft.Reliability|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Viene creato un oggetto locale di un tipo <xref:System.IDisposable>, ma l'oggetto non viene eliminato prima che tutti i riferimenti relativi siano esterni all'ambito.  
  
## Descrizione della regola  
 Se un oggetto eliminabile non viene eliminato in modo esplicito prima che tutti i riferimenti a esso siano esterni all'ambito, verrà eliminato in un momento indeterminato quando il relativo finalizzatore verrà eseguito dal Garbage Collector.  Poiché un evento eccezionale potrebbe impedire l'esecuzione del finalizzatore dell'oggetto, è preferibile che l'oggetto venga eliminato in modo esplicito.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, chiamare il metodo <xref:System.IDisposable.Dispose%2A> sull'oggetto prima che tutti i riferimenti relativi siano esterni all'ambito.  
  
 È possibile utilizzare l'istruzione `using` \(`Using` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]\) per eseguire il wrapping di oggetti che implementano `IDisposable`.  Gli oggetti di cui è stato eseguito questo tipo di wrapping vengono eliminati automaticamente alla chiusura del blocco `using`.  
  
 Le situazioni seguenti in cui l'istruzione using non è sufficiente a proteggere gli oggetti IDisposable e può comportare la generazione di CA2000.  
  
-   La restituzione di un oggetto eliminabile richiede che l'oggetto venga costruito in un blocco try\/finally esterno a un blocco using.  
  
-   L'inizializzazione dei membri di un oggetto eliminabile non deve essere eseguita nel costruttore di un'istruzione using.  
  
-   Costruttori di annidamento protetti solo da un gestore di eccezioni.  Di seguito è riportato un esempio:  
  
    ```  
    using (StreamReader sr = new StreamReader(new FileStream("C:\myfile.txt", FileMode.Create)))  
    { ... }  
    ```  
  
     fa in modo che CA2000 venga generato perché un errore nella costruzione dell'oggetto StreamReader può impedire la chiusura dell'oggetto FileStream.  
  
-   Gli oggetti dinamici devono utilizzare un oggetto ombreggiatura per implementare il modello Dispose degli oggetti IDisposable.  
  
## Esclusione di avvisi  
 Non eliminare un avviso da questa regola a meno che non sia stato chiamato un metodo sull'oggetto che chiama `Dispose`, come <xref:System.IO.Stream.Close%2A>, o se il metodo che ha generato l'avviso restituisce un oggetto IDisposable che fa il wrapping dell'oggetto.  
  
## Regole correlate  
 [CA2213: I campi Disposable devono essere eliminati](../code-quality/ca2213-disposable-fields-should-be-disposed.md)  
  
 [CA2202: Non eliminare oggetti più volte](../code-quality/ca2202-do-not-dispose-objects-multiple-times.md)  
  
## Esempio  
 Se si sta implementando un metodo che restituisce un oggetto eliminabile, utilizzare un blocco try\/finally senza un blocco catch per assicurarsi che l'oggetto venga eliminato.  Utilizzando un blocco try\/finally, si consente la generazione di eccezioni dal punto dell'errore e si garantisce che l'oggetto venga eliminato.  
  
 Nel metodo OpenPort1, la chiamata per aprire l'oggetto ISerializable SerialPort o la chiamata a SomeMethod può avere esito negativo.  Viene generato un avviso CA2000 nell'implementazione.  
  
 Nel metodo OpenPort2, due oggetti SerialPort vengono dichiarati e impostati come null:  
  
-   `tempPort`, utilizzato per verificare l'esito positivo delle operazioni del metodo.  
  
-   `port`, utilizzato per il valore restituito del metodo.  
  
 `tempPort` viene costruito e aperto in un blocco `try` e qualsiasi altra operazione richiesta viene eseguita nello stesso blocco `try`.  Alla fine del blocco `try`, la porta aperta viene assegnata all'oggetto `port` che verrà restituito e l'oggetto `tempPort` viene impostato su `null`.  
  
 Il blocco `finally` verifica il valore di `tempPort`.  Se non è null, un'operazione nel metodo ha avuto esito negativo e `tempPort` viene chiuso per garantire il rilascio delle risorse.  L'oggetto porta restituito conterrà l'oggetto SerialPort aperto se le operazioni del metodo sono riuscite, o sarà null se un'operazione non è riuscita.  
  
 [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope_1.vb)]
 [!code-vb[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/VisualBasic/ca2000-dispose-objects-before-losing-scope_1.vb)]
 [!code-cs[FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope#1](../code-quality/codesnippet/CSharp/ca2000-dispose-objects-before-losing-scope_1.cs)]  
  
## Esempio  
 Per impostazione predefinita, nel compilatore [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] tutti gli operatori aritmetici consentono di verificare l'overflow.  Pertanto, qualsiasi operazione aritmetica di Visual Basic potrebbe generare un oggetto <xref:System.OverflowException>.  Ciò può condurre a violazioni impreviste di regole, come ad esempio CA2000.  Ad esempio, nella funzione CreateReader1 seguente sarà prodotta una violazione CA2000 perché il compilatore Visual Basic sta generando un'istruzione del controllo dell'overflow per l'aggiunta, la quale potrebbe generare un'eccezione che impedirebbe la collocazione di StreamReader.  
  
 Per correggere, è possibile disabilitare l'emissione di controlli dell'overflow dal compilatore Visual Basic nel progetto o è possibile modificare il codice come la funzione CreateReader2 seguente.  
  
 Per disabilitare l'emissione dei controlli di overflow, in Esplora soluzioni fare clic con il pulsante destro del mouse sul nome del progetto, quindi fare clic su **Proprietà**.  Fare clic su **Compila**, fare clic su **Opzioni di compilazione avanzate**, quindi controllare **Rimuovi controllo dell'overflow di Integer**.  
  
 [!CODE [FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1](FxCop.Reliability.CA2000.DisposeObjectsBeforeLosingScope.VBOverflow#1)]  
  
## Vedere anche  
 <xref:System.IDisposable>   
 [Modello Dispose](../Topic/Dispose%20Pattern.md)