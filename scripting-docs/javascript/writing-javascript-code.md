---
title: "Scrittura di codice JavaScript | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.htmldesigner.html"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "codice, sintassi JavaScript"
  - "commenti, codice JavaScript"
  - "codice JavaScript"
ms.assetid: dde28266-0d0f-4460-a819-f931cf0911ad
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Scrittura di codice JavaScript
Come molti altri linguaggi di programmazione, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] è organizzato in istruzioni, in blocchi composti da set di istruzioni correlati e commenti.  In un'istruzione puoi utilizzare variabili, stringhe, numeri ed espressioni.  
  
## Istruzioni  
 Un programma [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] è costituito da una raccolta di istruzioni.  Nelle istruzioni [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] sono combinate espressioni in modo che queste siano in grado di eseguire un'attività completa.  
  
 Un'istruzione è composta da una o più espressioni, parole chiave o operatori \(simboli\).  In genere, un'istruzione è scritta in una singola riga, sebbene possa anche essere scritta su due o più righe.  Inoltre, due o più istruzioni possono essere scritte nella stessa riga ed essere separate da un punto e virgola.  In ogni nuova riga inizia in genere una nuova istruzione.  È consigliabile terminare le istruzioni in modo esplicito.  A questo scopo utilizza il punto e virgola \(;\) che rappresenta il carattere di terminazione delle istruzioni [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
 Ecco due esempi di istruzioni di [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  Le frasi che seguono i caratteri \/\/ sono *commenti* ovvero note esplicative nel programma.  
  
```javascript  
var aBird = "Robin"; // Assign the text "Robin" to the variable aBird.  
var today = new Date(); // Assign today's date to the variable today.  
```  
  
 Per *blocco* si intende un gruppo di istruzioni [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] racchiuso tra parentesi graffe \({}\).  Le istruzioni raggruppate all'interno di un blocco possono in genere essere considerate come un'unica istruzione.  Ciò significa che puoi utilizzare blocchi nella maggior parte dei punti di codice in cui [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] prevede una singola istruzione.  Tra le eccezioni sono incluse le intestazioni dei cicli **for** e `while`.  Si noti come le singole istruzioni all'interno di un blocco terminano con un punto e virgola, ma non il blocco stesso.  
  
 I blocchi vengono in genere utilizzati nelle funzioni e nelle istruzioni condizionali.  A differenza del linguaggio C\+\+ e di altri linguaggi, in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] un blocco non viene considerato come un nuovo ambito. Solo le funzioni consentono di creare un nuovo ambito.  
  
 Nell'esempio seguente, la clausola `else` contiene un blocco di due istruzioni racchiuso tra parentesi graffe.  Il blocco viene trattato come un'unica istruzione.  Inoltre, la funzione stessa è costituita da un blocco di istruzioni racchiuso tra parentesi graffe.  Le istruzioni al di sotto della funzione si trovano all'esterno del blocco e pertanto non sono parte della definizione di funzione.  
  
```javascript  
function inchestometers(inches)  
   {  
   if (inches < 0)  
      return -1;  
   else  
      {  
      var meters = inches / 39.37;  
      return meters;  
      }  
   }  
  
var inches = 12;  
var meters = inchestometers(inches);  
document.write("the value in meters is " + meters);  
```  
  
## Commenti  
 Un commento [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] a riga singola inizia con due barre \(\/\/\).  Ecco un esempio di un commento a riga singola.  
  
```javascript  
var aGoodIdea = "Comment your code thoroughly."; // This is a single-line comment.  
```  
  
 Un commento a righe multiple [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] inizia con una barra seguita da un asterisco \(\/\*\) e termina con la combinazione inversa \(\*\/\).  
  
```javascript  
/*  
This is a multiline comment that explains the preceding code statement.  
  
The statement assigns a value to the aGoodIdea variable. The value,   
which is contained between the quote marks, is called a literal. A   
literal explicitly and directly contains information; it does not   
refer to the information indirectly. The quote marks are not part   
of the literal.  
*/  
```  
  
> [!NOTE]
>  Se provi a incorporare un commento a righe multiple in un altro, il commento a righe multiple risultante verrà interpretato in un modo imprevisto in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  Il simbolo \*\/ che determina la fine del commento a righe multiple incorporato viene interpretato come terminazione di tutto il commento a righe multiple.  Ciò significa che il testo che segue il commento a righe multiple incorporato non verrà impostato come commento. Verrà invece interpretato come codice di [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] e verranno generati errori di sintassi.  
  
 Ti consigliamo di scrivere tutti i commenti come blocchi di commenti a riga singola.  In tal modo potrai successivamente impostare come commento segmenti di codice estesi utilizzando un commento a righe multiple.  
  
```javascript  
// This is another multiline comment, written as a series of single-line comments.  
// After the statement is executed, you can refer to the content of the   
// aGoodIdea variable by using its name.  
var extendedIdea = aGoodIdea + " You never know when you'll have to figure out what it does.";  
```  
  
## Assegnazioni e uguaglianza  
 Il segno di uguale \(\=\) viene utilizzato in istruzioni di [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] per assegnare valori alle variabili: si tratta dell'operatore di assegnazione.  L'operando di sinistra dell'operatore \= è sempre un Lvalue.  Di seguito vengono forniti alcuni esempi di Lvalue:  
  
-   variabili,  
  
-   elementi di matrice,  
  
-   proprietà dell'oggetto.  
  
 L'operando di destra dell'operatore \= è sempre un Rvalue.  Rvalue può essere un valore arbitrario di qualsiasi tipo, compreso il valore di un'espressione.  Ecco un esempio di istruzione di assegnazione [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```javascript  
var anInteger = 3;  
```  
  
 Il compilatore di [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] interpreta questa istruzione come: "Assegnare il valore 3 alla variabile **anInteger**" o "**anInteger** accetta il valore 3".  
  
 Assicurati di aver compreso correttamente la differenza tra l'operatore \= \(di assegnazione\) e l'operatore \= \= \(di uguaglianza\).  Quando desideri confrontare due valori per verificare se sono uguali, utilizza due segni di uguale \(\=\=\).  Ciò viene discusso in dettaglio in [Controllo del flusso di programma](../javascript/controlling-program-flow-javascript.md).  
  
## Espressioni  
 Un valore di un'espressione [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] può essere di qualsiasi tipo [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] valido: un numero, una stringa, un oggetto, e così via.  Le espressioni più semplici sono quelle letterali.  Ecco alcuni esempi di espressioni letterali [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```javascript  
3.9                       // numeric literal  
"Hello!"                  // string literal  
false                     // boolean literal  
null                      // literal null value  
{x:1, y:2}                // Object literal  
[1,2,3]                   // Array literal  
function(x){return x*x;}  // function literal  
```  
  
 Espressioni più complesse possono contenere variabili, chiamate di funzioni e altre espressioni.  Puoi combinare espressioni in modo da crearne di più complesse utilizzando gli operatori.  Sono esempi di operatori: `+` \(addizione\), `-` \(sottrazione\), `*` \(moltiplicazione\) e `/` \(divisione\).  
  
 Ecco alcuni esempi di espressioni complesse di [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```javascript  
var anExpression = 3 * (4 / 5) + 6;  
var aSecondExpression = Math.PI * radius * radius;  
var aThirdExpression = aSecondExpression + "%" + anExpression;  
var aFourthExpression = "(" + aSecondExpression + ") % (" + anExpression + ")";  
```