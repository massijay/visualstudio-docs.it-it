---
title: "CA1065: Non generare eccezioni in posizioni non previste | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1065"
  - "DoNotRaiseExceptionsInUnexpectedLocations"
helpviewer_keywords: 
  - "DoNotRaiseExceptionsInUnexpectedLocations"
  - "CA1065"
ms.assetid: 4e1bade4-4ca2-4219-abc3-c7b2d741e157
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA1065: Non generare eccezioni in posizioni non previste
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotRaiseExceptionsInUnexpectedLocations|  
|CheckId|CA1065|  
|Categoria|Microsoft.Design|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un metodo che normalmente non genera eccezioni genera un'eccezione.  
  
## Descrizione della regola  
 I metodi che normalmente non generano eccezioni possono essere suddivisi nelle categorie seguenti:  
  
-   Metodi Property Get  
  
-   Metodi della funzione di accesso agli eventi  
  
-   Metodi Equals  
  
-   Metodi GetHashCode  
  
-   Metodi ToString  
  
-   Costruttori statici  
  
-   Finalizzatori  
  
-   Metodi Dispose  
  
-   Operatori di uguaglianza  
  
-   Operatori di cast implicito  
  
 Nelle sezioni riportate di seguito vengono illustrati questi tipi di metodo.  
  
### Metodi Property Get  
 Poiché le proprietà sono sostanzialmente campi intelligenti,  dovrebbero comportarsi il più possibile come campi.  Dal momento che i campi non generano eccezioni, non dovrebbero generarne nemmeno le proprietà.  Se una proprietà genera un'eccezione, valutare di trasformarla in un metodo.  
  
 Le eccezioni seguenti possono essere generate da un metodo Property Get:  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName> e tutte le derivate \(inclusa <xref:System.ObjectDisposedException?displayProperty=fullName>\)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName> e tutte le derivate  
  
-   <xref:System.ArgumentException?displayProperty=fullName> \(solo da Get indicizzato\)  
  
-   <xref:System.Collections.Generic.KeyNotFoundException> \(solo da Get indicizzato\)  
  
### Metodi della funzione di accesso agli eventi  
 Le funzioni di accesso agli eventi devono essere operazioni semplici che non generano eccezioni.  Un evento non deve generare un'eccezione quando si tenta di aggiungere o rimuovere un gestore eventi.  
  
 Le eccezioni seguenti possono essere generate da una funzione di accesso agli eventi:  
  
-   <xref:System.InvalidOperationException?displayProperty=fullName> e tutte le derivate \(inclusa <xref:System.ObjectDisposedException?displayProperty=fullName>\)  
  
-   <xref:System.NotSupportedException?displayProperty=fullName> e tutte le derivate  
  
-   <xref:System.ArgumentException> e le derivate  
  
### Metodi Equals  
 I metodi **Equals** seguenti non dovrebbero generare eccezioni:  
  
-   <xref:System.Object.Equals%2A?displayProperty=fullName>  
  
-   [M:IEquatable.Equals](http://go.microsoft.com/fwlink/?LinkId=113472)  
  
 Un metodo **Equals** deve restituire `true` o `false` anziché generare un'eccezione.  Se, ad esempio, a Equals vengono passati due tipi non corrispondenti, il metodo deve restituire `false` anziché generare <xref:System.ArgumentException>.  
  
### Metodi GetHashCode  
 I metodi **GetHashCode** seguenti non dovrebbero normalmente generare eccezioni:  
  
-   <xref:System.Object.GetHashCode%2A>  
  
-   [M:IEqualityComparer.GetHashCode\(T\)](http://go.microsoft.com/fwlink/?LinkId=113477)  
  
 **GetHashCode** deve restituire sempre un valore.  In caso contrario, è possibile perdere elementi nella tabella hash.  
  
 Le versioni di **GetHashCode** che accettano un argomento possono generare <xref:System.ArgumentException>.  **Object.GetHashCode** tuttavia non dovrebbe mai generare un'eccezione.  
  
### Metodi ToString  
 Il debugger utilizza <xref:System.Object.ToString%2A?displayProperty=fullName> per consentire di visualizzare informazioni sugli oggetti in formato stringa.  Pertanto, **ToString** non dovrebbe modificare lo stato di un oggetto e non dovrebbe generare eccezioni.  
  
### Costruttori statici  
 La generazione di eccezioni da un costruttore statico fa sì che il tipo sia inutilizzabile nel dominio dell'applicazione corrente.  È consigliabile generare un'eccezione da un costruttore statico solo se davvero necessario, ad esempio per un problema di sicurezza.  
  
### Finalizzatori  
 La generazione di un'eccezione da un finalizzatore provoca rapidamente l'errore di CLR, che a sua volta provoca la chiusura del processo.  Pertanto, la generazione di eccezioni in un finalizzatore deve essere sempre evitata.  
  
### Metodi Dispose  
 Un metodo <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> non dovrebbe generare un'eccezione.  Dispose spesso è chiamato come parte della logica di pulizia in una clausola `finally`.  Pertanto, la generazione esplicita di un'eccezione da Dispose forza l'utente ad aggiungere la gestione delle eccezioni nella clausola `finally`.  
  
 Il percorso del codice **Dispose\(false\)** non dovrebbe mai generare eccezioni, perché viene quasi sempre chiamato da un finalizzatore.  
  
### Operatori di uguaglianza \(\=\=, \!\=\)  
 Come i metodi Equals, gli operatori di uguaglianza devono restituire `true` o `false` e non dovrebbero generare eccezioni.  
  
### Operatori di cast implicito  
 Poiché spesso l'utente non è consapevole della chiamata a un operatore di cast implicito, un'eccezione generata dall'operatore di cast implicito è completamente imprevista.  Pertanto, nessuna eccezione deve essere generata dagli operatori di cast implicito.  
  
## Come correggere le violazioni  
 Per le funzioni Get di proprietà, modificare la logica in modo che non debba più generare un'eccezione oppure trasformare la proprietà in un metodo.  
  
 Per tutti gli altri tipi di metodo elencati in precedenza, modificare la logica in modo che non debba più generare un'eccezione.  
  
## Esclusione di avvisi  
 È opportuno eliminare un avviso da questa regola se la violazione è causata da una dichiarazione dell'eccezione anziché da un'eccezione generata.  
  
## Regole correlate  
 [CA2219: Non generare eccezioni in clausole di eccezione](../code-quality/ca2219-do-not-raise-exceptions-in-exception-clauses.md)  
  
## Vedere anche  
 [Avvisi di progettazione](../code-quality/design-warnings.md)