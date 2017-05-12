---
title: "Oggetto Date (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "Date"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Date (oggetto)"
  - "date, rilevamento"
ms.assetid: ce2202bb-7ec9-4f5a-bf48-3a04feff283e
caps.latest.revision: 29
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 29
---
# Oggetto Date (JavaScript)
Attiva la memorizzazione e il recupero di base dei valori di data e ora.  
  
## Sintassi  
  
```  
  
      dateObj = new Date()  
dateObj = new Date(dateVal)  
dateObj = new Date(year, month, date[, hours[, minutes[, seconds[,ms]]]])   
```  
  
## Parametri  
 `dateObj`  
 Necessario.  Nome della variabile a cui l'oggetto `Date` è assegnato.  
  
 `dateVal`  
 Necessario.  Se è un valore numerico `dateVal` in formato UTC \(Tempo universale coordinato, Universal Coordinated Time\) compresi tra la data specificata e la mezzanotte dell'1 gennaio 1970.  Se è una stringa, `dateVal` viene analizzata in base alle regole specificate in [Stringhe di data e ora](../../javascript/date-and-time-strings-javascript.md).  L'argomento `dateVal` può essere anche un valore VT\_DATE restituito da alcuni oggetti ActiveX.  
  
 `year`  
 Necessario.  Anno completo, ad esempio 1976 \(e non 76\).  
  
 `month`  
 Necessario.  Numero intero compreso tra 0 e 11, da gennaio a dicembre, che rappresenta il mese.  
  
 `date`  
 Necessario.  Numero intero compreso tra 1 e 31 che rappresenta il giorno.  
  
 `hours`  
 Opzionale.  Obbligatorio se si specifica `minutes`.  Numero intero compreso tra 0 e 23, da mezzanotte alle 23, che rappresenta l'ora.  
  
 minutes  
 Opzionale.  Obbligatorio se si specifica `seconds`.  Numero intero compreso tra 0 e 59 che rappresenta i minuti.  
  
 `seconds`  
 Opzionale.  Obbligatorio se si specifica `milliseconds`.  Numero intero compreso tra 0 e 59 che rappresenta i secondi.  
  
 `ms`  
 Opzionale.  Numero intero compreso tra 0 e 999 che rappresenta i millisecondi.  
  
## Note  
 Un oggetto `Date` include un numero che rappresenta un preciso istante nel tempo fino alla precisione di un millisecondo.  Se il valore di un argomento è maggiore del relativo intervallo o è un numero negativo, gli altri valori memorizzati verranno modificati di conseguenza.  Se si specifica 150 secondi, ad esempio, in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] il numero verrà convertito in due minuti e 30 secondi.  
  
 Se il numero è un valore `NaN`, l'oggetto non rappresenta un preciso istante nel tempo.  Se all'oggetto `Date` non viene passato alcun parametro, verrà inizializzato sull'ora corrente in formato UTC.  Prima di utilizzarlo deve essere fornito un valore all'oggetto.  
  
 L'intervallo di date che è possibile rappresentare in un oggetto `Date` è pari a circa 285.616 anni sia prima che dopo la data dell'1 gennaio 1970.  
  
 Per ulteriori informazioni sull'utilizzo dell'oggetto `Date` e dei metodi relativi, vedere [Calcolo di date e ore \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md).  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo dell'oggetto `Date`.  
  
```javascript  
var dateString = "Today's date is: ";  
  
var newDate = new Date();  
  
// Get the month, day, and year.  
dateString += (newDate.getMonth() + 1) + "/";  
dateString += newDate.getDate() + "/";  
dateString += newDate.getFullYear();  
  
document.write(dateString);  
  
// Output: Today's date is: <date>  
```  
  
## Requisiti  
 `Date object` è stato introdotto in [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)].  Alcuni membri della seguente lista sono stati introdotti nelle versioni successive.  Per ulteriori informazioni, vedere [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md) oppure la documentazione sui singoli membri.  
  
## Proprietà  
 La seguente tabella elenca le proprietà di `Date Object`.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|[Proprietà constructor](../../javascript/reference/constructor-property-date.md)|Specifica la funzione che crea un oggetto.|  
|[Proprietà prototype](../../javascript/reference/prototype-property-date.md)|Restituisce un riferimento al prototipo per una classe di oggetti.|  
  
## Funzioni  
 La seguente tabella elenca le funzioni di `Date Object`.  
  
|Funzioni|Descrizione|  
|--------------|-----------------|  
|[Funzione Date.now](../../javascript/reference/date-now-function-javascript.md)|Restituisce il numero di millisecondi tra l'1 gennaio 1970 e la data e l'ora correnti.|  
|[Funzione Date.parse](../../javascript/reference/date-parse-function-javascript.md)|Analizza una stringa contenente una data e restituisce il numero di millisecondi compresi tra tale data e la mezzanotte dell'1 gennaio 1970.|  
|[Funzione Date.UTC](../../javascript/reference/date-utc-function-javascript.md)|Restituisce il numero di millisecondi che intercorrono tra la mezzanotte dell'1 gennaio 1970, data espressa in formato UTC o GMT, e la data specificata.|  
  
<a name="js56jsobjdatemeth"></a>   
## Metodi  
 Nella tabella riportata di seguito sono elencati i metodi di `Date Object`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo getDate](../../javascript/reference/getdate-method-date-javascript.md)|Restituisce il valore del giorno del mese utilizzando l'ora locale.|  
|[Metodo getDay](../../javascript/reference/getday-method-date-javascript.md)|Restituisce il valore del giorno della settimana utilizzando l'ora locale.|  
|[Metodo getFullYear](../../javascript/reference/getfullyear-method-date-javascript.md)|Restituisce il valore dell'anno utilizzando l'ora locale.|  
|[Metodo getHours](../../javascript/reference/gethours-method-date-javascript.md)|Restituisce il valore delle ore utilizzando l'ora locale.|  
|[Metodo getMilliseconds](../../javascript/reference/getmilliseconds-method-date-javascript.md)|Restituisce il valore dei millisecondi utilizzando l'ora locale.|  
|[Metodo getMinutes](../../javascript/reference/getminutes-method-date-javascript.md)|Restituisce il valore dei minuti utilizzando l'ora locale.|  
|[Metodo getMonth](../../javascript/reference/getmonth-method-date-javascript.md)|Restituisce il valore del mese utilizzando l'ora locale.|  
|[Metodo getSeconds](../../javascript/reference/getseconds-method-date-javascript.md)|Restituisce il valore dei secondi utilizzando l'ora locale.|  
|[Metodo getTime](../../javascript/reference/gettime-method-date-javascript.md)|Restituisce il valore dell'ora in un oggetto `Date` come numero di millisecondi a partire dalla mezzanotte dell'1 gennaio 1970.|  
|[Metodo getTimezoneOffset](../../javascript/reference/gettimezoneoffset-method-date-javascript.md)|Restituisce la differenza, espressa in minuti, tra l'ora sul computer host e l'ora UTC \(Tempo universale coordinato, Universal Coordinated Time\).|  
|[Metodo getUTCDate](../../javascript/reference/getutcdate-method-date-javascript.md)|Restituisce il valore del giorno del mese utilizzando il formato UTC.|  
|[Metodo getUTCDay](../../javascript/reference/getutcday-method-date-javascript.md)|Restituisce il valore del giorno della settimana utilizzando il formato UTC.|  
|[Metodo getUTCFullYear](../../javascript/reference/getutcfullyear-method-date-javascript.md)|Restituisce il valore dell'anno utilizzando il formato UTC.|  
|[Metodo getUTCHours](../../javascript/reference/getutchours-method-date-javascript.md)|Restituisce il valore delle ore utilizzando il formato UTC.|  
|[Metodo getUTCMilliseconds](../../javascript/reference/getutcmilliseconds-method-date-javascript.md)|Restituisce il valore dei millisecondi utilizzando il formato UTC.|  
|[Metodo getUTCMinutes](../../javascript/reference/getutcminutes-method-date-javascript.md)|Restituisce il valore dei minuti utilizzando il formato UTC.|  
|[Metodo getUTCMonth](../../javascript/reference/getutcmonth-method-date-javascript.md)|Restituisce il valore del mese utilizzando il formato UTC.|  
|[Metodo getUTCSeconds](../../javascript/reference/getutcseconds-method-date-javascript.md)|Restituisce il valore dei secondi utilizzando il formato UTC.|  
|[Metodo getVarDate](../../javascript/reference/getvardate-method-date-javascript.md)|Restituisce il valore VT\_DATE in un oggetto `Date`.|  
|[Metodo getYear](../../javascript/reference/getyear-method-date-javascript.md)|Restituisce il valore dell'anno.|  
|[Metodo hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Restituisce un valore booleano che indica se per un oggetto è disponibile una proprietà con il nome specificato.|  
|[Metodo isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Restituisce un valore booleano che indica se un oggetto esiste nella catena di prototipi di un altro oggetto.|  
|[Metodo propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Restituisce un valore booleano che indica se una proprietà specificata è parte di un oggetto e se è enumerabile.|  
|[Metodo setDate](../../javascript/reference/setdate-method-date-javascript.md)|Imposta il valore numerico del giorno del mese utilizzando l'ora locale.|  
|[Metodo setFullYear](../../javascript/reference/setfullyear-method-date-javascript.md)|Imposta il valore dell'anno utilizzando l'ora locale.|  
|[Metodo setHours](../../javascript/reference/sethours-method-date-javascript.md)|Imposta il valore delle ore utilizzando l'ora locale.|  
|[Metodo setMilliseconds](../../javascript/reference/setmilliseconds-method-date-javascript.md)|Imposta il valore dei millisecondi utilizzando l'ora locale.|  
|[Metodo setMinutes](../../javascript/reference/setminutes-method-date-javascript.md)|Imposta il valore dei minuti utilizzando l'ora locale.|  
|[Metodo setMonth](../../javascript/reference/setmonth-method-date-javascript.md)|Imposta il valore del mese utilizzando l'ora locale.|  
|[Metodo setSeconds](../../javascript/reference/setseconds-method-date-javascript.md)|Imposta il valore dei secondi utilizzando l'ora locale.|  
|[Metodo setTime](../../javascript/reference/settime-method-date-javascript.md)|Consente di impostare i valori di data e ora nell'oggetto `Date`.|  
|[Metodo setUTCDate](../../javascript/reference/setutcdate-method-date-javascript.md)|Imposta il valore numerico del giorno del mese utilizzando il formato UTC.|  
|[Metodo setUTCFullYear](../../javascript/reference/setutcfullyear-method-date-javascript.md)|Imposta il valore dell'anno utilizzando il formato UTC.|  
|[Metodo setUTCHours](../../javascript/reference/setutchours-method-date-javascript.md)|Imposta il valore delle ore utilizzando il formato UTC.|  
|[Metodo setUTCMilliseconds](../../javascript/reference/setutcmilliseconds-method-date-javascript.md)|Imposta il valore dei millisecondi utilizzando il formato UTC.|  
|[Metodo setUTCMinutes](../../javascript/reference/setutcminutes-method-date-javascript.md)|Imposta il valore dei minuti utilizzando il formato UTC.|  
|[Metodo setUTCMonth](../../javascript/reference/setutcmonth-method-date-javascript.md)|Imposta il valore del mese utilizzando il formato UTC.|  
|[Metodo setUTCSeconds](../../javascript/reference/setutcseconds-method-date-javascript.md)|Imposta il valore dei secondi utilizzando il formato UTC.|  
|[Metodo setYear](../../javascript/reference/setyear-method-date-javascript.md)|Imposta il valore dell'anno utilizzando l'ora locale.|  
|[Metodo toDateString](../../javascript/reference/todatestring-method-date-javascript.md)|Restituisce una data come valore stringa.|  
|[Metodo toGMTString](../../javascript/reference/togmtstring-method-date-javascript.md)|Restituisce una data convertita in una stringa in base all'ora di Greenwich \(GMT, Greenwich Mean Time\).|  
|[Metodo toISOString](../../javascript/reference/toisostring-method-date-javascript.md)|Restituisce una data come valore stringa in formato ISO.|  
|[Metodo toJSON](../../javascript/reference/tojson-method-date-javascript.md)|Utilizzato per trasformare i dati di un tipo di oggetto prima della serializzazione JSON.|  
|[Metodo toLocaleDateString](../../javascript/reference/tolocaledatestring-method-date-javascript.md)|Restituisce una data come valore stringa appropriato per le impostazioni locali correnti dell'ambiente host.|  
|[Metodo toLocaleString](../../javascript/reference/tolocalestring-date.md)|Restituisce un oggetto convertito in una stringa utilizzando le impostazioni locali correnti.|  
|[Metodo toLocaleTimeString](../../javascript/reference/tolocaletimestring-method-date-javascript.md)|Restituisce un'ora come valore stringa appropriato per le impostazioni locali correnti dell'ambiente host.|  
|[Metodo toString](../../javascript/reference/tostring-method-date.md)|Restituisce la rappresentazione in forma di stringa di un oggetto.|  
|[Metodo toTimeString](../../javascript/reference/totimestring-method-date-javascript.md)|Restituisce un'ora come valore stringa.|  
|[Metodo toUTCString](../../javascript/reference/toutcstring-method-date-javascript.md)|Restituisce una data convertita in una stringa utilizzando il formato UTC.|  
|[Metodo valueOf](../../javascript/reference/valueof-method-date.md)|Restituisce il valore primitivo dell'oggetto specificato.|  
  
## Vedere anche  
 [Calcolo di date e ore \(JavaScript\)](../../javascript/calculating-dates-and-times-javascript.md)   
 [Stringhe di data e ora](../../javascript/date-and-time-strings-javascript.md)