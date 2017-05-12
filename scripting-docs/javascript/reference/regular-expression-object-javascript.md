---
title: "Oggetto Regular Expression (JavaScript) | Microsoft Docs"
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
  - "RegularExpression_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "RegExp (oggetto), panoramica"
  - "Regular Expression (oggetto)"
  - "espressioni regolari, RegExp (oggetto)"
ms.assetid: 346aa83e-a045-47ea-acae-b42c7b121534
caps.latest.revision: 21
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 21
---
# Oggetto Regular Expression (JavaScript)
Un oggetto che contiene un modello di espressione regolare e i flag che specificano come applicare il modello.  
  
## Sintassi  
  
```  
re = /pattern/[flags]  
```  
  
## Sintassi  
  
```  
re = new RegExp("pattern"[,"flags"])   
```  
  
## Parametri  
 *re*  
 Necessario.  Il nome della variabile a cui è assegnato il modello di espressione regolare.  
  
 *pattern*  
 Necessario.  Il modello di espressione regolare da usare.  Se si usa la sintassi 1, delimitare il modello con i caratteri "\/".  Se si usa la sintassi 2, racchiudere il modello tra virgolette.  
  
 `flags`  
 Parametro facoltativo.  Racchiudere il flag tra virgolette se si usa la sintassi 2.  I flag disponibili, che possono essere combinati, sono:  
  
-   g \(ricerca globale per tutte le occorrenze di *pattern*\)  
  
-   i \(ignora maiuscole\/minuscole\)  
  
-   m \(ricerca su più righe\)  
  
-   u \(unicode\), abilita le [funzionalità Unicode](../../javascript/advanced/special-characters-javascript.md) di EcmaScript 6.  Supportato solo in [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)].  
  
-   y \(corrispondenza temporanea\), ricerca le corrispondenze nella proprietà `lastIndex` dell'espressione regolare \(e non esegue la ricerca negli indici successivi\).  Supportato in [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## Note  
 L'oggetto **Regular Expression** non deve essere confuso con l'oggetto globale `RegExp`.  Anche se sembrano uguali, sono distinti e separati.  Le proprietà dell'oggetto **Regular Expression** contengono solo informazioni su una particolare istanza di **Regular Expression**, mentre le proprietà dell'oggetto globale `RegExp` contengono informazioni continuamente aggiornate su ogni corrispondenza non appena si verifica.  
  
 Gli oggetti **Regular Expression** archiviano i modelli usati nella ricerca di stringhe con specifiche combinazioni di caratteri.  Dopo la creazione, l'oggetto  **Regular Expression** viene passato a un metodo string oppure una stringa viene passata a uno dei metodi delle espressioni regolari.  Le informazioni sull'ultima ricerca eseguita vengono archiviate nell'oggetto globale `RegExp`.  
  
 Usare la sintassi 1 quando si conosce in anticipo la stringa di ricerca.  Usare la sintassi 2 quando la stringa di ricerca cambia di frequente oppure è sconosciuta, come nel caso di stringhe ricavate dall'input dell'utente.  
  
 L'argomento *pattern*, prima di essere usato, viene compilato in un formato interno.  Se si usa la sintassi 1, *pattern* viene compilato al caricamento dello script.  Se si usa la sintassi 2, *pattern* viene compilato immediatamente prima di essere usato oppure quando si chiama il metodo **compile**.  
  
## Esempio  
 L'esempio seguente illustra l'uso dell'oggetto **Regular Expression** creando un oggetto \(re\) contenente un criterio di espressione regolare con i flag associati.  In questo caso, l'oggetto **Regular Expression** risultante viene usato dal metodo `match`:  
  
```javascript  
var s = "through the pages of the book";  
  
// Create regular expression pattern.  
var re = new RegExp("the", "i");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return first occurrence of "the".  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
//   
```  
  
## Esempio  
 L'esempio seguente aggiorna il modello di espressione regolare per la ricerca di più istanze.  
  
```javascript  
// Create regular expression pattern using the i and g flags.  
var re = new RegExp("the", "ig");  
  
// Attempt match on search string.  
var r = s.match(re);     
  
// Return the two occurrences of "the".  
if(console && console.log) {  
    console.log(r.length);  
    console.log(r);  
}  
  
// Output:  
// 2  
// [object Array] ["the", "the"]  
```  
  
## Esempio  
 Quando si usa il flag \/y, se viene trovata una corrispondenza, aggiorna `lastindex` all'indice del carattere successivo dopo l'ultima corrispondenza.  Se la corrispondenza non viene trovata, reimposta `lastindex` su 0.  
  
 L'esempio seguente cerca una corrispondenza in un indice specifico usando il flag \/y e la proprietà `lastIndex`.  
  
```javascript  
// Create regular expression pattern using the i and y flags.  
var re = new RegExp("the", "iy");  
  
// Set the lastIndex property and attempt a match  
// at the specified index.  
re.lastIndex = 20;  
var r = s.match(re);     
  
// No matches returned.  
if(console && console.log) {  
    console.log(r);  
}  
// Reset the lastIndex property and attempt a match.  
re.lastIndex = 21;  
var r = s.match(re);  
  
// Return occurrence of "the" starting at index 21.  
if(console && console.log) {  
    console.log(r);  
}  
  
// Output:  
// null  
// [object Array] ["the"]  
```  
  
<a name="js56jsobjregexpressionprop"></a>   
## Proprietà  
 [Proprietà global](../../javascript/reference/global-property-regular-expression-javascript.md) &#124; [Proprietà ignoreCase](../../javascript/reference/ignorecase-property-regular-expression-javascript.md) &#124; [Proprietà multiline](../../javascript/reference/multiline-property-regular-expression-javascript.md) &#124; [Proprietà source](../../javascript/reference/source-property-regular-expression-javascript.md)  
  
<a name="js56jsobjregexpressionmeth"></a>   
## Metodi  
 [Metodo compile](../../javascript/reference/compile-method-regular-expression-javascript.md) &#124; [Metodo exec](../../javascript/reference/exec-method-regular-expression-javascript.md) &#124; [Metodo test](../../javascript/reference/test-method-regular-expression-javascript.md)  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 Il flag u è supportato in [!INCLUDE[jsv12text](../../javascript/includes/jsv12text-md.md)].  
  
 Il flag y è supportato in [!INCLUDE[jsv12textExp](../../javascript/includes/jsv12textexp-md.md)].  
  
## Vedere anche  
 [Oggetto RegExp](../../javascript/reference/regexp-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/it-it/ab0766e1-7037-45ed-aa23-706f58358c0e)   
 [Oggetto String](../../javascript/reference/string-object-javascript.md)