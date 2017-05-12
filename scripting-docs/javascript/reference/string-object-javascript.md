---
title: "Oggetto String (JavaScript) | Microsoft Docs"
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
  - "String_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "String (oggetto)"
  - "String (oggetto), panoramica"
ms.assetid: 8063ecd5-5778-4e87-b985-b21420171914
caps.latest.revision: 32
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 32
---
# Oggetto String (JavaScript)
Consente di modificare e formattare stringhe di testo e di determinare e individuare le sottostringhe in esse contenute.  
  
## Sintassi  
  
```  
  
newString = new String(["stringLiteral"])  
```  
  
## Parametri  
 `newString`  
 Obbligatorio.  Nome della variabile a cui l'oggetto `String` è assegnato.  
  
 `stringLiteral`  
 Facoltativo.  Qualsiasi gruppo di caratteri Unicode.  
  
## Note  
 In [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sono disponibili sequenze di escape che possono essere incluse nelle stringhe per creare caratteri che non è possibile digitare direttamente.  Ad esempio, `\t` specifica un carattere di tabulazione.  Per altre informazioni, vedere [Caratteri speciali](../../javascript/advanced/special-characters-javascript.md).  
  
## Valori letterali di stringa  
 Un *valore letterale stringa* è composto da zero o più caratteri racchiusi tra virgolette singole o doppie.  Un valore letterale stringa è un tipo di dati principale \(primitivo\) di `string`.  Un *oggetto String* viene creato usando l'[operatore new](../../javascript/reference/new-operator-decrementjavascript.md) e ha come tipo di dati `Object`.  
  
 L'esempio seguente mostra che il tipo di dati del valore letterale stringa non corrisponde a quello di un oggetto `String`.  
  
```javascript  
var strLit = "This is a string literal.";  
var strObj = new String("This is a string object.");  
  
document.write(typeof strLit);  
document.write("<br/>");  
document.write(typeof strObj);  
// Output:  
// string  
// object  
```  
  
## Metodi per i valori letterali stringa  
 Quando si chiama un metodo su un valore letterale stringa, questo viene temporaneamente convertito in un oggetto stringa wrapper.  Il valore letterale stringa viene considerato come se fosse stato creato attraverso l'operatore `new`.  
  
 Nel seguente esempio viene applicato il metodo `toUpperCase` a un valore letterale stringa.  
  
```javascript  
var strLit = "This is a string literal.";  
  
var result1 = strLit.toUpperCase();  
  
var result2 = (new String(strLit)).toUpperCase();  
  
document.write(result1);  
document.write("<br/>");  
document.write(result2);  
// Output:   
// THIS IS A STRING LITERAL.  
// THIS IS A STRING LITERAL.  
```  
  
## Accesso a un singolo carattere  
 È possibile accedere a un singolo carattere di una stringa come proprietà di sola lettura indicizzata in una matrice.  Questa funzionalità è stata introdotta in [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)].  Nell'esempio seguente si accede ai singoli caratteri della stringa.  
  
```javascript  
var str = "abcd";  
var result = str[2];  
document.write (result);  
// Output: c  
  
var result = "the"[0];  
document.write(result);  
// Output: t  
```  
  
## Requisiti  
 `String Object` è stato introdotto in [!INCLUDE[jsv1text](../../javascript/reference/includes/jsv1text-md.md)].  Alcuni membri dell'elenco seguente sono stati introdotti nelle versioni successive.  
  
<a name="js56jsobjstringprop"></a>   
## Proprietà  
 La tabella seguente elenca le proprietà dell'oggetto `String`.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|[Proprietà constructor](../../javascript/reference/constructor-property-string.md)|Specifica la funzione che crea un oggetto.|  
|[Proprietà length \(String\)](../../javascript/reference/length-property-string-javascript.md)|Restituisce la lunghezza di un oggetto `String`.|  
|[Proprietà prototype](../../javascript/reference/prototype-property-string.md)|Restituisce un riferimento al prototipo per una classe di oggetti.|  
  
## Funzioni  
 La tabella seguente elenca le funzioni dell'oggetto `String`.  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|[Funzione String.fromCharCode](../../javascript/reference/string-fromcharcode-function-javascript.md)|Restituisce una stringa a partire da un numero di valori dei caratteri Unicode.|  
|[Funzione String.fromCodePoint](../../javascript/reference/string-fromcodepoint-function-javascript.md)|Restituisce la stringa associata a un punto di codice UTF\-16 Unicode.|  
|[Funzione String.raw](../../javascript/reference/string-raw-function-javascript.md)|Restituisce il formato di stringa non elaborata di una stringa di modello.|  
  
<a name="js56jsobjstringmeth"></a>   
## Metodi  
 La tabella seguente elenca i metodi dell'oggetto `String`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo anchor](../../javascript/reference/html-tag-methods-javascript.md)|Racchiude il testo in un ancoraggio HTML con un attributo NAME.|  
|[Metodo big](../../javascript/reference/html-tag-methods-javascript.md)|Racchiude il testo tra i tag HTML \<BIG\>.|  
|[Metodo blink](../../javascript/reference/html-tag-methods-javascript.md)|Racchiude il testo tra i tag HTML \<BLINK\>.|  
|[Metodo bold](../../javascript/reference/html-tag-methods-javascript.md)|Racchiude il testo tra i tag HTML \<B\>.|  
|[Metodo charAt](../../javascript/reference/charat-method-string-javascript.md)|Restituisce il carattere in corrispondenza dell'indice specificato.|  
|[Metodo charCodeAt](../../javascript/reference/charcodeat-method-string-javascript.md)|Restituisce la codifica Unicode del carattere specificato.|  
|[Metodo codePointAt](../../javascript/reference/codepointat-method-string-javascript.md)|Restituisce il punto di codice relativo a un carattere UTF\-16 Unicode.|  
|[Metodo concat \(String\)](../../javascript/reference/concat-method-string-javascript.md)|Restituisce una stringa che contiene la concatenazione di due stringhe specificate.|  
|[Metodo endsWith](../../javascript/reference/endswith-method-string-javascript.md)|Restituisce un valore booleano che indica se una stringa o una sottostringa termina con la stringa passata.|  
|[Metodo includes](../../javascript/reference/includes-method-string-javascript.md)|Restituisce un valore booleano che indica se la stringa passata è contenuta nell'oggetto string.|  
|[Metodo fixed](../../javascript/reference/html-tag-methods-javascript.md)|Racchiude il testo tra i tag HTML \<TT\>.|  
|[Metodo fontcolor](../../javascript/reference/html-tag-methods-javascript.md)|Racchiude il testo tra i tag HTML \<FONT\> con un attributo COLOR.|  
|[Metodo fontsize](../../javascript/reference/html-tag-methods-javascript.md)|Racchiude il testo tra i tag HTML \<FONT\> con un attributo SIZE.|  
|[Metodo hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Restituisce un valore booleano che indica se per un oggetto è disponibile una proprietà con il nome specificato.|  
|[Metodo indexOf \(String\)](../../javascript/reference/indexof-method-string-javascript.md)|Restituisce la posizione del carattere da cui inizia la prima occorrenza di una sottostringa all'interno di una stringa.|  
|[Metodo isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Restituisce un valore booleano che indica se un oggetto esiste nella catena di prototipi di un altro oggetto.|  
|[Metodo italics](../../javascript/reference/html-tag-methods-javascript.md)|Racchiude il testo tra i tag HTML \<I\>.|  
|[Metodo lastIndexOf \(String\)](../../javascript/reference/lastindexof-method-string-javascript.md)|Restituisce l'ultima occorrenza di una sottostringa all'interno di una stringa.|  
|[Metodo link](../../javascript/reference/html-tag-methods-javascript.md)|Racchiude il testo in un ancoraggio HTML con un attributo HREF.|  
|[Metodo localeCompare](../../javascript/reference/localecompare-method-string-javascript.md)|Restituisce un valore che indica se due stringhe sono equivalenti nelle impostazioni locali correnti.|  
|[Metodo match](../../javascript/reference/match-method-string-javascript.md)|Ricerca una stringa usando un oggetto **Regular Expression** specificato e restituisce il risultato in forma di matrice.|  
|[Metodo normalize](../../javascript/reference/normalize-method-string-javascript.md)|Restituisce il formato di normalizzazione Unicode di una stringa specificata.|  
|[Metodo propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Restituisce un valore booleano che indica se una proprietà specificata è parte di un oggetto e se è enumerabile.|  
|[Metodo repeat](../../javascript/reference/repeat-method-string-javascript.md)|Restituisce un nuovo oggetto stringa con un valore uguale alla stringa originale ripetuto per il numero specificato di volte.|  
|[Metodo replace](../../javascript/reference/replace-method-string-javascript.md)|Usa un'espressione regolare per sostituire il testo in una stringa e restituisce il risultato.|  
|[Metodo search](../../javascript/reference/search-method-string-javascript.md)|Restituisce la posizione della prima corrispondenza di una sottostringa in una ricerca di espressione regolare.|  
|[Metodo slice \(String\)](../../javascript/reference/slice-method-string-javascript.md)|Restituisce una sezione di una stringa.|  
|[Metodo small](../../javascript/reference/html-tag-methods-javascript.md)|Racchiude il testo tra i tag HTML \<SMALL\>.|  
|[Metodo split](../../javascript/reference/split-method-string-javascript.md)|Restituisce la matrice di stringhe risultante dalla suddivisione di una stringa in sottostringhe.|  
|[Metodo startsWith](../../javascript/reference/startswith-method-string-javascript.md)|Restituisce un valore booleano che indica se una stringa o una sottostringa inizia con la stringa passata.|  
|[Metodo strike](../../javascript/reference/html-tag-methods-javascript.md)|Racchiude il testo tra i tag HTML \<STRIKE\>.|  
|[Metodo sub](../../javascript/reference/html-tag-methods-javascript.md)|Racchiude il testo tra i tag HTML \<SUB\>.|  
|[Metodo substr](../../javascript/reference/substr-method-string-javascript.md)|Restituisce una sottostringa di lunghezza specifica che inizia dalla posizione specificata.|  
|[Metodo substring](../../javascript/reference/substring-method-string-javascript.md)|Restituisce la sottostringa in corrispondenza della posizione specificata in un oggetto `String`.|  
|[Metodo sup](../../javascript/reference/html-tag-methods-javascript.md)|Racchiude il testo tra i tag HTML \<SUP\>.|  
|[Metodo toLocaleLowerCase](../../javascript/reference/tolocalelowercase-method-string-javascript.md)|Restituisce una stringa in cui tutti i caratteri alfabetici sono stati convertiti in minuscolo a seconda delle impostazioni locali correnti dell'ambiente host.|  
|[Metodo toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Restituisce un oggetto convertito in una stringa usando le impostazioni locali correnti.|  
|[Metodo toLocaleUpperCase](../../javascript/reference/tolocaleuppercase-method-string-javascript.md)|Restituisce una stringa in cui tutti i caratteri alfabetici sono stati convertiti in maiuscolo a seconda delle impostazioni locali correnti dell'ambiente host.|  
|[Metodo toLowerCase](../../javascript/reference/tolowercase-method-javascript.md)|Restituisce una stringa in cui tutti i caratteri alfabetici sono stati convertiti in minuscolo.|  
|[Metodo toString](../../javascript/reference/tostring-method-string-1.md)|Restituisce la stringa.|  
|[Metodo toUpperCase](../../javascript/reference/touppercase-method-string-javascript.md)|Restituisce una stringa in cui tutti i caratteri alfabetici sono stati convertiti in maiuscolo.|  
|[Metodo trim](../../javascript/reference/trim-method-string-javascript.md)|Restituisce una stringa in cui sono stati rimossi gli spazi iniziali e finali e il carattere terminatore di riga.|  
|[Metodo valueOf](../../javascript/reference/valueof-method-string.md)|Restituisce la stringa.|  
  
## Vedere anche  
 [Operatore new](../../javascript/reference/new-operator-decrementjavascript.md)   
 [Applicazione di esempio per scorrimento, panoramica e zoom](http://code.msdn.microsoft.com/ie/Scrolling-panning-and-6834aaf9)