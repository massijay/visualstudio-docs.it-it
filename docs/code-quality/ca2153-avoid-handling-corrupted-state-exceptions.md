---
title: "CA2153: Evitare la gestione delle eccezioni in stato danneggiato | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 418cc9cb-68ad-47e9-a6c8-a48b9c35db45
caps.latest.revision: 5
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 5
---
# CA2153: Evitare la gestione delle eccezioni in stato danneggiato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidHandlingCorruptedStateExceptions|  
|CheckId|CA2153|  
|Categoria|Microsoft.Security|  
|Modifica importante|Non importante|  
  
## Causa  
 Le [eccezioni in stato danneggiato \(CSE, Corrupted State Exception\)](https://msdn.microsoft.com/en-us/magazine/dd419661.aspx) indicano che sono presenti danni nella memoria del processo. Se si prova a intercettare tali eccezioni, invece di lasciare che il processo venga arrestato in modo anomalo, può portare a vulnerabilità di sicurezza nel caso in cui un utente malintenzionato riesca a inserire un exploit nell'area della memoria danneggiata.  
  
## Descrizione della regola  
 CSE indica che lo stato di un processo è stato danneggiato e non è stato recuperato dal sistema. Nello scenario di stato danneggiato, un gestore generale recupera l'eccezione solo se si contrassegna il metodo con l'attributo `HandleProcessCorruptedStateExceptions` appropriato. Per impostazione predefinita, [Common Language Runtime \(CLR\)](https://msdn.microsoft.com/en-us/library/8bs2ecf4.aspx) non richiama i gestori catch per le eccezioni CSE.  
  
 Consentire l'arresto anomalo del processo senza tentare il recupero di queste eccezioni è l'opzione più sicura, sebbene anche la registrazione del codice possa consentire agli utenti malintenzionati di sfruttare i bug associati al danneggiamento della memoria.  
  
 Questo avviso viene attivato quando si recuperano le eccezioni CSE con un gestore generale che recupera tutte le eccezioni, ad esempio catch\(exception\) o catch\(no exception specification\).  
  
## Come correggere le violazioni  
 Per risolvere questo avviso scegliere una delle opzioni seguenti:  
  
 1. Rimuovere l'attributo `HandleProcessCorruptedStateExceptions`. Viene ripristinato il comportamento di runtime predefinito che prevede che le eccezioni CSE non vengano passate ai gestori catch.  
  
 2. Rimuovere il gestore catch generale nella preferenza dei gestori che recuperano tipi di eccezione specifici.  Può includere le eccezioni CSE, presupponendo che il codice del gestore sia in grado di gestirle in modo sicuro \(molto raro\).  
  
 3. Generare di nuovo l'eccezione CSE nel gestore catch che assicura che l'eccezione venga passata al chiamante e che il processo in esecuzione venga terminato.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio di pseudocodice  
  
### Violazione  
 Lo pseudocodice seguente illustra il modello rilevato da questa regola.  
  
```  
[HandleProcessCorruptedStateExceptions] //method to handle and log CSE exceptions void TestMethod1() { try { FileStream fileStream = new FileStream("name", FileMode.Create); } catch (Exception e) { // Handle error } }  
```  
  
### Soluzione 1  
 La rimozione dell'attributo HandleProcessCorruptedExceptions assicura che le eccezioni non verranno gestite.  
  
```  
void TestMethod1() { try { FileStream fileStream = new FileStream("name", FileMode.Create); } catch (IOException e) { // Handle error } catch (UnauthorizedAccessException e) { // Handle error } }  
```  
  
### Soluzione 2  
 Rimuovere il gestore catch generale e recuperare solo tipi specifici di eccezioni.  
  
```  
void TestMethod1() { try { FileStream fileStream = new FileStream("name", FileMode.Create); } catch (IOException e) { // Handle error } catch (UnauthorizedAccessException e) { // Handle error } }  
```  
  
### Soluzione 3  
 Generare di nuovo l'eccezione.  
  
```  
void TestMethod1() { try { FileStream fileStream = new FileStream("name", FileMode.Create); } catch (Exception e) { // Handle error throw; } }  
```