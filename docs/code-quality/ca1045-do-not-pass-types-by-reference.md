---
title: "CA1045: Non passare i tipi per riferimento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1045"
  - "DoNotPassTypesByReference"
helpviewer_keywords: 
  - "CA1045"
  - "DoNotPassTypesByReference"
ms.assetid: bcc3900a-e092-4bb8-896f-cb83f6289968
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 18
---
# CA1045: Non passare i tipi per riferimento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotPassTypesByReference|  
|CheckId|CA1045|  
|Categoria|Microsoft.Design|  
|Breaking Change|Breaking|  
  
## Causa  
 Un metodo pubblico o protetto in un tipo pubblico presenta un parametro `ref` che accetta un tipo primitivo, un tipo di riferimento o un tipo di valore non costituito da uno dei tipi incorporati.  
  
## Descrizione della regola  
 Il passaggio di tipi per riferimento \(mediante `out` o `ref`\) richiede esperienza nell'utilizzo dei puntatori, nonché la conoscenza delle differenze tra tipi di valore e tipi di riferimento e dei metodi di gestione con più valori restituiti.  La differenza tra parametri `out` e `ref` spesso non è compresa.  
  
 Quando un tipo di riferimento viene passato "per riferimento", il metodo utilizza il parametro per restituire un'istanza diversa dell'oggetto. Il passaggio di un tipo di riferimento per riferimento è anche noto come utilizzo di un doppio puntatore, di un puntatore a un puntatore o di un doppio riferimento indiretto. Utilizzando la convenzione di chiamata predefinita, ovvero il passaggio "per valore", un parametro che accetta un tipo di riferimento riceve già un puntatore all'oggetto.  Il puntatore, non l'oggetto a cui punta, viene passato per valore.  Nel passaggio per valore il metodo non può modificare il puntatore affinché faccia riferimento a una nuova istanza del tipo di riferimento, ma può modificare il contenuto dell'oggetto a cui punta.  Per la maggior parte delle applicazioni questo è sufficiente e fornisce il comportamento desiderato.  
  
 Se un metodo deve restituire un'istanza diversa, utilizzare a tale scopo il valore restituito del metodo.  Per apprendere diversi metodi che operano su stringhe e restituiscono una nuova istanza di una stringa, vedere la classe <xref:System.String?displayProperty=fullName>.  Se si utilizza questo modello, sarà il chiamante a dovere decidere se conservare l'oggetto originale.  
  
 Sebbene i valori restituiti siano comuni e ampiamente utilizzati, l'applicazione corretta dei parametri `out` e `ref` richiede competenze in progettazione intermedia e codifica.  I progettisti di librerie che progettano per destinatari generici non possono prevedere che gli utenti utilizzino in modo professionale i parametri `out` o `ref`.  
  
> [!NOTE]
>  Quando si utilizzano parametri costituiti da strutture di grandi dimensioni, le risorse aggiuntive necessarie per copiare queste strutture potrebbero ridurre le prestazioni quando si esegue il passaggio per valore.  In questi casi, è possibile utilizzare i parametri `ref` o `out`.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola causata da un tipo valore, fare in modo che il metodo restituisca l'oggetto come valore restituito.  Se è necessario che il metodo restituisca più valori, riprogettarlo affinché restituisca una sola istanza di un oggetto contenente i valori.  
  
 Per correggere una violazione di questa regola causata da un tipo riferimento, assicurarsi che la restituzione di una nuova istanza del riferimento sia il comportamento desiderato.  In questo caso, il metodo deve utilizzare a tale scopo il proprio valore restituito.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sempre sicura, tuttavia questa progettazione potrebbe causare problemi di utilizzabilità.  
  
## Esempio  
 Nella seguente libreria sono illustrate due implementazioni di una classe che genera risposte al feedback dell'utente.  La prima implementazione \(`BadRefAndOut`\) impone all'utente della libreria di gestire tre valori restituiti.  La seconda implementazione \(`RedesignedRefAndOut`\) semplifica l'utilizzo da parte dell'utente restituendo un'istanza di una classe contenitore \(`ReplyData`\) che gestisce i dati come una singola unità.  
  
 [!code-cs[FxCop.Design.NoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_1.cs)]  
  
## Esempio  
 L'applicazione riportata di seguito illustra l'attività dell'utente.  La chiamata alla libreria riprogettata \(metodo `UseTheSimplifiedClass`\) è più semplice e le informazioni restituite dal metodo vengono gestite in modo più agevole.  L'output dei due metodi è identico.  
  
 [!code-cs[FxCop.Design.TestNoRefOrOut#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_2.cs)]  
  
## Esempio  
 La libreria di esempio riportata di seguito illustra l'utilizzo dei parametri `ref` per i tipi di riferimento e mostra un modo migliore per implementare questa funzionalità.  
  
 [!code-cs[FxCop.Design.RefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_3.cs)]  
  
## Esempio  
 L'applicazione riportata di seguito chiama ogni metodo della libreria e ne illustra il comportamento.  
  
 [!code-cs[FxCop.Design.TestRefByRefNo#1](../code-quality/codesnippet/CSharp/ca1045-do-not-pass-types-by-reference_4.cs)]  
  
 Questo esempio produce l'output che segue.  
  
  **Changing pointer \- passed by value:**  
**12345**  
**12345**  
**Changing pointer \- passed by reference:**  
**12345**  
**12345 ABCDE**  
**Passaggio per valore restituito:**  
**12345 ABCDE**   
## Regole correlate  
 [CA1021: Evitare parametri out](../code-quality/ca1021-avoid-out-parameters.md)