---
title: "Metodi tag HTML (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "anchor (metodo) [JavaScript]"
  - "big (metodo) [JavaScript]"
  - "blink (metodo) [JavaScript]"
  - "bold (metodo) [JavaScript]"
  - "fixed (metodo) [JavaScript]"
  - "fontcolor (metodo) [JavaScript]"
  - "fontsize (metodo) [JavaScript]"
  - "Metodi tag HTML [JavaScript]"
  - "italics (metodo) [JavaScript]"
  - "link (metodo) [JavaScript]"
  - "small (metodo) [JavaScript]"
  - "sub (metodo) [JavaScript]"
  - "sup (metodo) [JavaScript]"
ms.assetid: 50376223-be95-4aa4-9147-9e738a5d3cfa
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Metodi tag HTML (JavaScript)
È possibile utilizzare i metodi di tag HTML per racchiudere il testo tra elementi HTML in un oggetto `String`.  
  
## Sintassi  
 Nella seguente tabella vengono elencate la sintassi e una descrizione di ciascun metodo di tag HTML.  
  
 Nella colonna Sintassi `string1` è un oggetto `String` o un valore letterale stringa.  
  
 La colonna Standard indica le raccomandazioni del [World Wide Web Consortium \(W3C\)](http://go.microsoft.com/fwlink/?LinkId=199553) per HTML 4. "  Sconsigliato" indica che l'elemento HTML è sconsigliato rispetto ai fogli di stile.  
  
|Sintassi|Descrizione del metodo|Descrizione del parametro|Standard|  
|--------------|----------------------------|-------------------------------|--------------|  
|`string1`.anchor\(`name`\)|Racchiude il testo in un ancoraggio HTML con un attributo NAME.|Il parametro `name` rappresenta il testo da inserire nell'attributo NAME dell'ancoraggio HTML.||  
|`string1`.big\(\)|Racchiude il testo tra i tag HTML \<BIG\>.||Sconsigliato|  
|`string1`.blink\(\)|Racchiude il testo tra i tag HTML \<BLINK\>.  Il tag \<BLINK\> non è supportato in Internet Explorer.||Non standard|  
|`string1`.bold\(\)|Racchiude il testo tra i tag HTML \<B\>.||Sconsigliato|  
|`string1`.fixed\(\)|Racchiude il testo tra i tag HTML \<TT\>.||Sconsigliato|  
|`string1`.fontcolor\(`color`\)|Racchiude il testo tra i tag HTML \<FONT\> con un attributo COLOR.|Il parametro `color` è un valore stringa contenente il valore esadecimale o il nome predefinito per un colore.  I nomi di colori predefiniti validi dipendono dal browser host di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] e dalla relativa versione.|Deprecato|  
|`string1`.fontsize\(`size`\)|Racchiude il testo tra i tag HTML \<FONT\> con un attributo SIZE.|Il parametro `size` è un Integer che specifica la dimensione del testo.  Gli Integer validi dipendono dal browser host di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] e dalla relativa versione.|Deprecato|  
|`string1`.italics\(\)|Racchiude il testo tra i tag HTML \<I\>.||Sconsigliato|  
|`string1`.link\(`href`\)|Racchiude il testo in un ancoraggio HTML con un attributo HREF.|Il parametro `href` rappresenta il testo da inserire nell'attributo HREF dell'ancoraggio HTML.||  
|`string1`.small\(\)|Racchiude il testo tra i tag HTML \<SMALL\>.||Sconsigliato|  
|`string1`.strike\(\)|Racchiude il testo tra i tag HTML \<STRIKE\>.||Deprecato|  
|`string1`.sub\(\)|Racchiude il testo tra i tag HTML \<SUB\>.|||  
|`string1`.sup\(\)|Racchiude il testo tra i tag HTML \<SUP\>.|||  
  
## Note  
 Non viene eseguito alcun controllo per determinare se i tag HTML sono già stati applicati alla stringa.  
  
## Esempio  
 Negli esempi seguenti viene illustrato come utilizzare i metodi di tag HTML.  
  
```javascript  
// anchor method.  
var strVariable = "This is an anchor.";  
document.write(strVariable.anchor("Anchor1"));  
// Output: <A NAME="Anchor1">This is an anchor.</A>  
  
// big method.  
var strVariable = "This is a string.";  
document.write(strVariable.big());  
// Output: <BIG>This is a string.</BIG>  
  
//  blink method.  
var strVariable = "This is a string.";  
document.write(strVariable.blink());  
// Output: <BLINK>This is a string.</BLINK>  
  
//  bold method.  
var strVariable = "This is a string.";  
document.write(strVariable.bold());  
// Output: <B>This is a string.</B>  
  
//  fixed method.  
var strVariable = "This is a string.";  
document.write(strVariable.fixed());  
// Output: <TT>This is a string.</TT>  
  
//  fontcolor method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontcolor("red"));  
// Output: <FONT COLOR="red">This is a string.</FONT>  
  
//  fontsize method.  
var strVariable = "This is a string.";  
document.write(strVariable.fontsize(-1));  
// Output: <FONT SIZE="-1">This is a string.</FONT>  
  
//  italics method  
var strVariable = "This is a string.";  
document.write(strVariable.italics());  
// Output: <I>This is a string.</I>  
  
//  link method.  
var strVariable = "This is a hyperlink.";  
document.write(strVariable.link("http://www.microsoft.com"));  
// Output: <A HREF="http://www.microsoft.com">This is a hyperlink.</A>  
  
//  small method.  
var strVariable = "This is a string.";  
document.write(strVariable.small());  
// Output: <SMALL>This is a string.</SMALL>  
  
//  strike method.  
var strVariable = "This is a string.";  
document.write(strVariable.strike());  
// Output: <STRIKE>This is a string.</STRIKE>  
  
//  sub method.  
var strVariable = "This is a string.";  
document.write(strVariable.sub());  
// Output: <SUB>This is a string.</SUB>  
  
//  sup method.  
var strVariable = "This is a string.";  
document.write(strVariable.sup());  
// Output: <SUP>This is a string.</SUP>  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Si applica a**: [Oggetto String](../../javascript/reference/string-object-javascript.md)  
  
## Vedere anche  
 [Oggetto String](../../javascript/reference/string-object-javascript.md)