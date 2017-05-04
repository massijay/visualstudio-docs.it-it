---
title: "Propriet&#224; name (Error) (JavaScript) | Microsoft Docs"
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
  - "name"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Name (proprietà)"
  - "name (proprietà), nome errore"
ms.assetid: 94df2d6b-f1a1-4931-a956-0a930cb87f76
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Propriet&#224; name (Error) (JavaScript)
Restituisce il nome di un errore.  
  
## Sintassi  
  
```  
  
errorObj.  
name  
  
```  
  
## Parametri  
 `errorObj`  
 Obbligatorio.  Istanza dell'oggetto `Error`.  
  
## Note  
 La proprietà **name** restituisce il nome o il tipo di eccezione di un errore.  In caso di un errore di runtime, la proprietà name viene impostata su uno dei seguenti tipi di eccezione nativi:  
  
|Tipo di eccezione|Significato|  
|-----------------------|-----------------|  
|ConversionError|Errore che si verifica quando si tenta di effettuare una conversione dell'oggetto non consentita.|  
|RangeError|Errore che si verifica quando viene specificata una funzione con un argomento che supera l'intervallo consentito,  ad esempio quando si tenta di costruire un oggetto `Array` la cui lunghezza non corrisponde a un numero intero positivo valido.|  
|ReferenceError|Errore che si verifica quando viene rilevato un riferimento non valido,  come nel caso in cui il riferimento previsto è `null`.|  
|RegExpError|Errore che si verifica quando la compilazione di un'espressione regolare non risulta corretta.  Una volta compilata l'espressione regolare, tuttavia, l'errore non può verificarsi.  È il caso, ad esempio, in cui si dichiara un'espressione regolare con un modello che presenta una sintassi non valida o flag diversi da **i**, **g** o **m** oppure se l'espressione regolare contiene più di una volta lo stesso flag.|  
|SyntaxError|Errore che si verifica quando viene analizzato il testo di origine e tale testo non presenta una sintassi corretta.  È il caso, ad esempio, in cui viene chiamata la funzione `eval` con un argomento che non rappresenta un testo di programma valido.|  
|TypeError|Errore che si verifica ogni volta che il tipo effettivo di un operando non corrisponde al tipo previsto.  È il caso, ad esempio, in cui si esegue una chiamata di funzione a un elemento che non corrisponde a un oggetto o che non supporta la chiamata.|  
|URIError|Errore che si verifica quando vengono rilevati URI \(Uniform Resource Indicator\) non validi.  È il caso, ad esempio, in cui vengono trovati caratteri non validi in una stringa codificata o decodificata.|  
  
## Esempio  
 Nell'esempio seguente viene generata un'eccezione TypeError e viene visualizzato il nome dell'errore e il relativo messaggio.  
  
```javascript  
try  
{  
    var x = y;  
}  
catch(e)  
{  
    document.write ("Error Message: " + e.message);  
    document.write ("<br />");  
    document.write ("Error Code: ");  
    document.write (e.number & 0xFFFF)  
    document.write ("<br />");  
    document.write ("Error Name: " + e.name);  
}  
```  
  
## Esempio  
 L'output del codice è il seguente.  
  
```javascript  
Error Message: 'y' is undefined  
Error Code: 5009  
Error Name: TypeError  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
 **Si applica a**: [Oggetto Error](../../javascript/reference/error-object-javascript.md)  
  
## Vedere anche  
 [Proprietà description \(Error\)](../../javascript/reference/description-property-error-javascript.md)   
 [Proprietà message \(Error\)](../../javascript/reference/message-property-error-javascript.md)   
 [Proprietà number \(Error\)](../../javascript/reference/number-property-error-javascript.md)