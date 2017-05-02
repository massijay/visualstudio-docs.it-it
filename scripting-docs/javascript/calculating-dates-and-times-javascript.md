---
title: "Calcolo di date e ore (JavaScript) | Microsoft Docs"
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
  - "operazioni aritmetiche con data e ora [JavaScript]"
  - "JavaScript, data e ora"
  - "confronto di date [JavaScript]"
  - "calcoli di data e ora [JavaScript]"
ms.assetid: ea976f78-d934-479b-9056-880390d8bddd
caps.latest.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 34
---
# Calcolo di date e ore (JavaScript)
Si può utilizzare l'[oggetto Date](../javascript/reference/date-object-javascript.md) per eseguire attività comuni relative a calendari e orologi, come ad esempio il confronto di date e il calcolo del tempo trascorso.  
  
## Impostazione di una data sulla data corrente  
 Quando si crea un'istanza dell'[oggetto Date](../javascript/reference/date-object-javascript.md) senza specificare una data, questo restituisce un valore che rappresenta la data e l'ora corrente, inclusi anno, mese, giorno, ora, minuto, secondo e millisecondo.  Data e ora possono quindi essere lette o modificate.  
  
 Il seguente esempio mostra come creare un'istanza di una data senza utilizzare nessun parametro e come visualizzarla nel formato *mm\-dd\-yy*.  
  
```javascript  
var dt = new Date();  
  
// Display the month, day, and year. getMonth() returns a 0-based number.  
var month = dt.getMonth()+1;  
var day = dt.getDate();  
var year = dt.getFullYear();  
document.write(month + '-' + day + '-' + year);  
  
// Output: current month, day, year  
```  
  
## Impostazione di una data specifica  
 È possibile impostare una data specifica passando una stringa di data al costruttore.  
  
```javascript  
var dt = new Date('8/24/2009');  
document.write(dt);  
  
// Output: Mon Aug 24 00:00:00 PDT 2009  
  
```  
  
> [!IMPORTANT]
>  Il fuso orario visualizzato nella stringa di data corrisponde al fuso orario impostato sul computer locale.  
>   
>  [!INCLUDE[javascript](../javascript/includes/javascript-md.md)] è flessibile sul formato della stringa utilizzata come parametro.  Ad esempio, è possibile immettere "24\-8\-2009", "August 24, 2009" o "24 Aug 2009".  
  
 Inoltre è possibile specificare un'ora.  Nell'esempio seguente viene illustrato un modo per specificare una data e ora in formato ISO.  La "Z" indica l'ora UTC.  
  
```javascript  
var dt = new Date('2010-06-09T15:20:00Z');  
document.write(dt);  
document.write("<br />");  
document.write(dt.toISOString());  
  
// Output:  
// Wed Jun 09 2010 08:20:00 GMT-0700 (Pacific Daylight Time)  
// 2010-06-09T15:20:00.000Z  
```  
  
 Per ulteriori informazioni sui formati di data come ISO, vedere [Stringhe di data e ora](../javascript/date-and-time-strings-javascript.md).  
  
 Nell'esempio seguente vengono illustrati altri modi per specificare un'ora.  
  
```javascript  
var dtA = new Date('8/24/2009 14:52:10');  
  
// The parameters are year, month, day, hours, minutes, seconds.  
var dtB = new Date(2009, 7, 24, 14, 52, 10);  
document.write(dtA);  
document.write("<br/>");  
document.write(dtB);  
  
// Output:  
// Mon Aug 24 14:52:10 PDT 2009  
// Mon Aug 24 14:52:10 PDT 2009  
  
```  
  
## Aggiunta e sottrazione di giorni, mesi e anni  
 Si possono utilizzare i metodi getX e setX dell'oggetto `Date` per impostare date e ore specifiche.  
  
 Nell'esempio seguente viene illustrato come è possibile impostare una data sul giorno precedente.  Si noti che se necessario i valori del mese e dell'anno vengono modificati.  
  
```javascript  
var myDate = new Date("1/1/1990");  
var dayOfMonth = myDate.getDate();  
myDate.setDate(dayOfMonth - 1);  
  
document.write(myDate);  
  
// Output: Sun Dec 31 00:00:00 PST 1989  
```  
  
 L'esempio seguente consente di impostare la data dell'ultimo giorno del mese sottraendo un giorno dal primo giorno del mese successivo.  
  
> [!TIP]
>  I mesi dell'anno sono numerati da 0 \(gennaio\) a 11 \(dicembre\).  I giorni della settimana sono numerati da 0 \(domenica\) a 6 \(sabato\).  
  
```javascript  
var myDate = new Date("1/1/1990")  
myDate.setMonth(myDate.getMonth() + 1);  
  
myDate.setDate (myDate.getDate() - 1);  
  
document.write(myDate);  
  
// Output: Wed Jan 31 00:00:00 PST 1990  
  
```  
  
## Utilizzo di giorni della settimana  
 Il [metodo getDay](../javascript/reference/getday-method-date-javascript.md) ottiene il giorno della settimana come numero compreso tra 0 \(Domenica\) e 6 \(Sabato\). Questo non è uguale al [metodo getDate](../javascript/reference/getdate-method-date-javascript.md), che permette di ottenere il giorno del mese come numero compreso tra 1 e 31.  
  
 L'esempio seguente consente di impostare la data per il giorno del ringraziamento, che negli Stati Uniti è il quarto giovedì di novembre.  Lo script trova l'1 novembre dell'anno corrente, quindi il primo giovedì e infine aggiunge tre settimane.  
  
```javascript  
var myDate = new Date();  
myDate.setHours(0, 0, 0, 0);  
  
myDate.setYear(2013);  
  
// Determine November 1.  
myDate.setDate(1);  
myDate.setMonth(10);  
  
// Find Thursday.  
var thursday = 4;  
while(myDate.getDay() != thursday) {  
    myDate.setDate(myDate.getDate() + 1);  
}  
  
// Add 3 weeks.  
myDate.setDate(myDate.getDate() + 21);  
  
document.write(myDate);  
  
// Output: Thu Nov 28 00:00:00 <time zone> 2013  
  
```  
  
## Calcolo del tempo trascorso  
 Il [metodo getTime](../javascript/reference/gettime-method-date-javascript.md) restituisce il numero di millisecondi trascorsi dalla mezzanotte dell'1 gennaio 1970.  Per qualsiasi data precedente a tale data restituisce un numero negativo.  
  
 Si può utilizzare il [metodo getTime](../javascript/reference/gettime-method-date-javascript.md) per impostare un'ora di inizio e di fine per il calcolo del tempo trascorso.  Questo metodo può essere utilizzato per misurare piccole unità, ad esempio alcuni secondi, e grandi unità, ad esempio giorni.  
  
 Nell'esempio seguente viene calcolato il tempo trascorso in secondi.  Il [metodo getTime](../javascript/reference/gettime-method-date-javascript.md) permette di ottenere il numero di millisecondi trascorsi dalla data zero.  
  
```javascript  
var startTime = new Date('1/1/1990');  
var startMsec = startTime.getMilliseconds();  
startTime.setTime(5000000);  
var elapsed = (startTime.getTime() - startMsec) / 1000;   
document.write(elapsed);  
  
// Output: 5000  
  
```  
  
 Per utilizzare unità più facilmente gestibili, è possibile dividere i millisecondi restituiti dal [metodo getTime](../javascript/reference/gettime-method-date-javascript.md) per un numero appropriato.  Ad esempio, per trasformare millisecondi in giorni, dividere il numero per 86.400.000 \(1000 millisecondi x 60 secondi x 60 minuti x 24 ore\).  
  
 Nell'esempio seguente viene illustrata la quantità di tempo trascorsa dal primo giorno dell'anno specificato.  Per calcolare il tempo trascorso in giorni, ore, minuti e secondi, vengono utilizzate operazioni di divisione.  Non viene tenuto conto dell'ora legale.  
  
```javascript  
// Set the unit values in milliseconds.  
var msecPerMinute = 1000 * 60;  
var msecPerHour = msecPerMinute * 60;  
var msecPerDay = msecPerHour * 24;  
  
// Set a date and get the milliseconds  
var date = new Date('6/15/1990');  
var dateMsec = date.getTime();  
  
// Set the date to January 1, at midnight, of the specified year.  
date.setMonth(0);  
date.setDate(1);  
date.setHours(0, 0, 0, 0);  
  
// Get the difference in milliseconds.  
var interval = dateMsec - date.getTime();  
  
// Calculate how many days the interval contains. Subtract that  
// many days from the interval to determine the remainder.  
var days = Math.floor(interval / msecPerDay );  
interval = interval - (days * msecPerDay );  
  
// Calculate the hours, minutes, and seconds.  
var hours = Math.floor(interval / msecPerHour );  
interval = interval - (hours * msecPerHour );  
  
var minutes = Math.floor(interval / msecPerMinute );  
interval = interval - (minutes * msecPerMinute );  
  
var seconds = Math.floor(interval / 1000 );  
  
// Display the result.  
document.write(days + " days, " + hours + " hours, " + minutes + " minutes, " + seconds + " seconds.");  
  
//Output: 164 days, 23 hours, 0 minutes, 0 seconds.  
```  
  
### Definizione dell'età dell'utente  
 Nell'esempio seguente viene utilizzato il compleanno dell'utente per calcolare l'età di quell'utente in anni.  L'anno di nascita viene sottratto dall'anno corrente quindi, se il compleanno non è ancora avvenuto nell'anno corrente, viene sottratto 1.  
  
```javascript  
var birthday = new Date("8/1/1985");  
var today = new Date();  
var years = today.getFullYear() - birthday.getFullYear();  
  
// Reset birthday to the current year.  
birthday.setFullYear(today.getFullYear());  
  
// If the user's birthday has not occurred yet this year, subtract 1.  
if (today < birthday)  
{  
    years--;  
}  
document.write("You are " + years + " years old.");  
  
// Output: You are <number of years> years old.  
  
```  
  
## Confronto di date  
 Quando si confrontano date in [!INCLUDE[javascript](../javascript/includes/javascript-md.md)], è necessario ricordare che l'operatore `==` restituisce `true` solo se le date da entrambi i lati dell'operatore fanno riferimento allo stesso oggetto.  Pertanto, se si dispone di due oggetti `Date` distinti impostati con la stessa data, `date1 == date2` restituisce `false`.  Inoltre, se un oggetto `Date` è impostato solo con la data ma non con l'ora, viene inizializzato alla mezzanotte di tale data.  Se pertanto si confrontano un oggetto `Date` impostato senza l'ora e `Date.now`, ad esempio, tenere presente che il primo `Date` viene impostato sulla mezzanotte mentre `Date.now` no.  
  
 Nell'esempio seguente viene controllato se la data corrente corrisponde, è antecedente o è successiva a una data specificata.  Per impostare la data corrente in `todayAtMidn`, lo script crea un oggetto `Date` per l'anno, il mese e il giorno correnti.  
  
```javascript  
// Get the current date at midnight.  
var now = new Date();   
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set specificDate to a specified date at midnight.  
var specificDate = new Date("9/21/2009");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() == specificDate.getTime())  
{  
    document.write("Same");  
}  
else  
{  
    document.write("Different");  
}  
  
//Output: Different  
```  
  
 Modificando l'esempio precedente, è possibile controllare se una data fornita rientra in un particolare intervallo.  
  
```javascript  
// Get the current date at midnight.  
var now = new Date();  
var todayAtMidn = new Date(now.getFullYear(), now.getMonth(), now.getDate());  
  
// Set start/end dates to a specified date (ISO format).  
var startDate = new Date("2009-06-09T15:20:00Z");  
var endDate = new Date("2011-06-09T15:20:00Z");  
  
// Compare the two dates by comparing the millisecond  
// representations.  
if (todayAtMidn.getTime() > startDate.getTime() &&   
    todayAtMidn.getTime() < endDate.getTime()) {  
    document.write("Specified date is within this range.");  
}  
else {  
    document.write("Specified date is not in this range.");  
}  
  
// Output: Specified date is not in this range.  
```  
  
## Vedere anche  
 [Oggetto Date](../javascript/reference/date-object-javascript.md)