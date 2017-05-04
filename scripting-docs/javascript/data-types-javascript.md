---
title: "Tipi di dati (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Boolean (tipo di dati), tipi di dati supportati"
ms.assetid: c7a6bd3a-4b1c-4dbe-8505-106dbf483b41
caps.latest.revision: 35
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 35
---
# Tipi di dati (JavaScript)
In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], esistono tre tipi di dati primari, due tipi di dati compositi e due tipi di dati speciali.  
  
## Tipi di dati primari  
 I tipi di dati primari \(primitivi\) sono:  
  
-   String  
  
-   Numero  
  
-   Boolean  
  
## Tipi di dati compositi  
 I tipi di dati compositi \(di riferimento\) sono:  
  
-   Object  
  
-   Matrice  
  
## Tipi di dati speciali  
 I tipi di dati speciali sono:  
  
-   Null  
  
-   Non definito  
  
## Tipo di dati String  
 Un valore stringa è composto da una serie di zero o più caratteri Unicode \(lettere, cifre e segni di punteggiatura\).  Viene utilizzato il tipo di dato stringa per rappresentare il testo in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  È possibile includere negli script valori letterali stringa racchiudendoli tra virgolette singole o doppie.  È possibile utilizzare le virgolette doppie in stringhe racchiuse tra virgolette singole o le virgolette singole in stringhe racchiuse in stringhe tra virgolette doppie.  Di seguito sono riportati alcuni esempi di stringhe:  
  
```javascript  
"Happy am I; from care I'm free!"  
'"Avast, ye lubbers!" roared the technician.'   
"45"  
'c'  
```  
  
 Notare che [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] non dispone di un tipo per rappresentare un singolo carattere.  Per rappresentare un singolo carattere in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], creare una stringa composta da un solo carattere.  Una stringa che non contiene alcun carattere \(""\) è una stringa vuota di lunghezza zero.  
  
 In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] sono disponibili sequenze di escape che possono essere incluse nelle stringhe per creare caratteri che non è possibile digitare direttamente.  Ad esempio, `\t` specifica un carattere di tabulazione.  Per ulteriori informazioni, vedere [Caratteri speciali](../javascript/advanced/special-characters-javascript.md).  
  
## Tipo di dati Number  
 In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], non esiste alcuna distinzione tra valori integer e a virgola mobile; un numero [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] può essere sia uno che l'altro \(internamente, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] rappresenta tutti i numeri come valori a virgola mobile\).  
  
### Valori Integer  
 I valori integer possono essere numeri interi positivi, numeri interi negativi e 0.  Possono essere rappresentati in base 10 \(decimali\), in base 16 \(esadecimali\) e in base 8 \(ottali\).  La maggior parte dei numeri in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] viene rappresentata in formato decimale.  
  
 Gli interi esadecimali \("hex"\) vengono caratterizzati anteponendo il valore "0x" \(uno zero seguito da x&#124;X\) iniziale.  Possono includere cifre comprese tra 0 a 9 e lettere comprese tra A ad F, sia maiuscole che minuscole.  Le lettere da A ad F rappresentano, come singole cifre, i numeri da 10 a 15 in base 10.  Vale a dire, 0xF equivale a 15 e 0x10 equivale a 16.  
  
 Gli interi ottali vengono caratterizzati anteponendo uno "0" \(zero\) iniziale.  Possono includere solo i numeri da 0 a 7.  Un numero con "0" iniziale che contiene le cifre "8" e\/o "9" viene interpretato come numero decimale.  
  
 Sia i numeri esadecimali che ottali possono essere negativi, ma non possono avere una parte decimale ed essere scritti in notazione scientifica \(esponenziale\).  
  
> [!NOTE]
>  A partire da [!INCLUDE[jsv9text](../javascript/includes/jsv9text-md.md)], la [funzione parseInt](../javascript/reference/parseint-function-javascript.md) non considera una stringa con prefisso "0" come ottale.  Quando non si utilizza la funzione `parseInt`, tuttavia, le stringhe con prefisso "0" possono sempre essere interpretate come ottali.  
  
### Valori a virgola mobile  
 I valori in virgola mobile possono essere numeri interi con una parte decimale.  Inoltre, possono essere espressi in notazione scientifica,  Ovvero una "e" maiuscola o minuscola è usata per rappresentare "dieci elevato alla potenza di".  In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] i numeri vengono rappresentati utilizzando lo standard IEEE 754 dei numeri a virgola mobile di otto byte per la rappresentazione numerica.  Ciò significa che è possibile scrivere numeri grandi fino a 1,79769x10<sup>308</sup> e numeri piccoli fino a 5x10<sup>-324</sup>.  Un numero che contiene un separatore decimale con un singolo "0" prima del separatore decimale viene interpretato come numero con separatore decimale a virgola mobile.  
  
 Notare che un numero che inizia con "0x" o con "00" e contiene un separatore decimale genererà un errore.  Di seguito sono riportati alcuni esempi di numeri [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
|Numero|Descrizione|Decimale equivalente|  
|------------|-----------------|--------------------------|  
|,0001, 0,0001, 1e\-4, 1,0e\-4|Quattro numeri a virgola mobile equivalenti.|0.0001|  
|3,45e2|Numero a virgola mobile.|345|  
|45|Intero.|45|  
|0378|Intero.  Sebbene simile a un numero ottale in quanto inizia con uno zero, 8 non è una cifra ottale valida: pertanto il numero viene considerato come decimale.|378|  
|0377|Intero ottale.  Sebbene inferiore solo di un'unità rispetto al numero dell'esempio precedente, il valore di questo numero è piuttosto diverso.|255|  
|0.0001|Numero a virgola mobile.  Sebbene inizi con uno zero, questo numero non è un numero ottale perché presenta il separatore decimale.|0.0001|  
|00.0001|Errore.  I due zeri iniziali contrassegnano il numero come un ottale, ma per gli ottali non è consentita una parte decimale.|N\/D \(errore del compilatore\)|  
|0Xff|Integer esadecimale.|255|  
|0x37CF|Integer esadecimale.|14287|  
|0x3e7|Integer esadecimale.  Notare che "e" non viene considerato come fattore di elevazione a potenza.|999|  
|0x3,45e2|Errore.  I numeri esadecimali non possono contenere parti decimali.|N\/D \(errore del compilatore\)|  
  
 Inoltre, [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] contiene numeri con valori speciali.  Tali valori sono:  
  
-   NaN \(non un numero\).  Viene utilizzato quando si esegue un'operazione matematica su dati non appropriati, quali stringhe o il valore undefined  
  
-   Infinito positivo.  Viene utilizzato quando un numero positivo è troppo grande per essere rappresentato in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]  
  
-   Infinito negativo.  Viene utilizzato quando un numero negativo è troppo grande per essere rappresentato in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]  
  
-   Zero positivo e negativo.  In [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] viene operata una distinzione tra lo zero positivo e lo zero negativo.  
  
## Tipo di dati booleani  
 Mentre i tipi di dati stringa e i numeri possono presentare un numero virtualmente illimitato di valori differenti, il tipo di dati booleano dispone di due soli valori.  Sono valori letterali `true` e `false`.  Un valore booleano è un valore reale: specifica se la condizione è vera o no.  
  
 I confronti eseguiti negli script determinano sempre un risultato booleano.  Si consideri la seguente riga di codice [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```javascript  
y = (x == 2000);  
```  
  
 In questo caso, il valore della variabile `x` viene confrontato con il numero 2000.  Se lo è, il risultato del confronto sarà il valore booleano **true**, il quale è assegnato alla variabile `y`.  Se invece il valore di `x` non è uguale a 2000, il risultato del confronto sarà il valore booleano `false`.  
  
 I valori booleani sono particolarmente utili nelle strutture di controllo.  Il seguente codice combina un confronto che crea un valore booleano direttamente con un'istruzione che lo utilizza.  Si consideri il seguente esempio di codice [!INCLUDE[javascript](../javascript/includes/javascript-md.md)].  
  
```javascript  
if (x == 2000) {  
    z = z + 1;  
}  
else {  
    x = x + 1;  
}  
```  
  
 L'istruzione `if/else` in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] esegue un'azione se un valore booleano è `true` \(`z = z + 1`\) e un'azione alternativa se il valore booleano è `false` \(`x = x + 1`\).  
  
 È possibile utilizzare qualsiasi espressione come espressione di confronto.  Qualsiasi espressione che restituisce 0, null, non definito o una stringa vuota viene interpretata come `false`.  Un'espressione che restituisce qualsiasi altro valore viene interpretata come `true`.  È ad esempio possibile utilizzare un'espressione quale la seguente:  
  
```javascript  
// This may not do what you expect. See below!  
if (x = y + z)   
```  
  
 Notare che la riga precedente non consente di verificare se `x` è uguale a `y + z`, poiché è stato utilizzato un unico segno uguale \(operatore di assegnazione\).  Al contrario, il codice sopra riportato consente invece di assegnare il valore `y + z` alla variabile `x`, quindi di verificare se il risultato dell'intera espressione \(il valore di `x`\) è zero.  Per verificare se `x` è uguale a `y + z`, è necessario utilizzare il codice seguente.  
  
```javascript  
// This is different from the code above!  
if (x == y + z)   
```  
  
 Per ulteriori informazioni sui confronti, vedere [Controllo del flusso di programma](../javascript/controlling-program-flow-javascript.md).  
  
## Il tipo di dati NULL  
 Il tipo di dati `null` ha solo un valore in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)]: null.  La parola chiave `null` non può essere utilizzata come nome di funzione o di variabile.  
  
 Una variabile contenente `null` non contiene numeri, stringhe, valori booleani, matrici o oggetti validi.  È possibile assegnare il valore `null` a una variabile per cancellarne il contenuto senza eliminare la variabile stessa.  
  
 Notare che in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], `null` non è uguale a 0 \(come avviene in C e C\+\+\).  Si noti inoltre che l'operatore `typeof` in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] restituisce valori `null` come di tipo `Object` e non di tipo `null`.  Per quanto possa disorientare, questo comportamento garantisce la compatibilità con le versioni precedenti.  
  
## Il tipo di dati non definito  
 Il valore `undefined` viene restituito quando si utilizza una proprietà di un oggetto che non esiste o una variabile dichiarata, ma alla quale non è mai stato assegnato un valore.  
  
 è possibile verificare se una variabile esiste confrontandola con `undefined`, ed è possibile controllare se il suo tipo è `undefined` confrontandolo con la stringa "undefined".  L'esempio seguente mostra come verificare che la variabile `x` è stata dichiarata:  
  
```javascript  
  
var x;  
  
// This method works.  
if (x == undefined) {  
    document.write("comparing x to undefined <br/>");  
}  
.  
// This method doesn't work - you must check for the string "undefined".  
if (typeof(x) == undefined) {  
    document.write("comparing the type of x to undefined <br/>");  
}  
// This method does work.   
if (typeof(x) == "undefined") {  
    document.write("comparing the type of x to the string 'undefined'");  
}  
  
// Output:   
// comparing x to undefined   
// comparing the type of x to the string 'undefined'  
  
```  
  
 È inoltre possibile confrontare il valore non definito con `null`.  Questo confronto è `true` se la proprietà `someObject.prop` è `null` o se la proprietà `someObject.prop` non esiste.  
  
```javascript  
someObject.prop == null;  
```  
  
 Per scoprire se una proprietà di un oggetto esiste, è possibile utilizzare l'operatore **in** :  
  
```javascript  
if ("prop" in someObject)  
    // someObject has the property 'prop'  
```  
  
## Vedere anche  
 [Oggetti e matrici](../javascript/objects-and-arrays-javascript.md)   
 [Operatore typeof](../javascript/reference/typeof-operator-decrementjavascript.md)