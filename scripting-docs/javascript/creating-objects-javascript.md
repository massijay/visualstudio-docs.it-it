---
title: "Creazione di oggetti (JavaScript) | Microsoft Docs"
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
  - "funzioni costruttore"
  - "costruttori, inclusione di proprietà e metodi"
  - "creazione di oggetti"
  - "creazione di oggetti, informazioni sulla creazione di oggetti"
  - "creazione di oggetti, funzioni costruttore"
  - "creazione di oggetti, prototipi"
  - "oggetti personalizzati"
  - "oggetti personalizzati, creazione"
  - "costruttore (funzione)"
  - "inizializzazione di oggetti, utilizzo di costruttori"
  - "oggetti, creazione [JavaScript]"
  - "prototipo (oggetti)"
ms.assetid: 58d1baa5-4fe8-4a56-a926-5b11765df704
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Creazione di oggetti (JavaScript)
Esistono diversi modi per creare oggetti personalizzati in JavaScript.  È possibile creare direttamente un'istanza di un [Oggetto Object](../javascript/reference/object-object-javascript.md), quindi aggiungere le proprie proprietà e metodi.  In alternativa, è possibile usare un'annotazione letterale dell'oggetto per definire l'oggetto.  È anche possibile usare una funzione del costruttore per definire un oggetto.  Per altre informazioni sull'uso delle funzioni del costruttore, vedere [Utilizzo di costruttori per la definizione di tipi](../javascript/advanced/using-constructors-to-define-types.md).  
  
## Esempio  
 Il codice seguente mostra come creare un'istanza di un oggetto e come aggiungere alcune proprietà.  In questo caso, solo l'oggetto `pasta` ha proprietà `grain`, `width` e `shape`.  
  
```javascript  
var pasta = new Object();  
pasta.grain = "wheat";  
pasta.width = 0.5;  
pasta.shape = "round";  
pasta.getShape = function() {   
    return this.shape;   
};  
document.write(pasta.grain);  
document.write("<br/>");  
document.write(pasta.getShape());  
  
// Output:  
// wheat  
// round  
  
```  
  
## Valori letterali dell'oggetto  
 È anche possibile usare un'annotazione letterale dell'oggetto per creare una sola istanza di un oggetto.  Il codice seguente mostra come creare un'istanza di un oggetto usando un'annotazione letterale dell'oggetto.  
  
```javascript  
var pasta = {  
    grain: "wheat",  
    width: 0.5,  
    shape: "round"  
};  
```  
  
 È anche possibile usare un valore letterale dell'oggetto in un costruttore.  
  
> [!CAUTION]
>  Le funzionalità descritte di seguito sono supportate solo in [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  
  
 In [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)] è possibile usare la sintassi abbreviata per creare un valore letterale dell'oggetto.  
  
```javascript  
var key = 'a';  
var value = 5;  
  
// Older version  
var obj1 = {  
    key: key,  
    value: value  
};  
  
// Edge mode  
var obj2 = {key, value};  
  
console.log(obj2);  
  
// Output:  
// [object Object] {key: "a", value: 5}  
```  
  
 L'esempio seguente mostra l'uso della sintassi abbreviata per definire i metodi nei valori letterali dell'oggetto.  
  
```javascript  
// Older versions  
var obj = {  
    method1: function() {},  
    method2: function() {}  
};  
  
// Edge mode  
var obj = {  
    method1() {},  
    method2() {}  
};  
```  
  
 È anche possibile impostare dinamicamente i nomi delle proprietà nei valori letterali dell'oggetto in [!INCLUDE[jsv12text](../javascript/includes/jsv12text-md.md)].  L'esempio di codice seguente crea dinamicamente un nome della proprietà per un oggetto usando la sintassi set.  
  
```javascript  
var propName = "prop_42";  
  
var obj = {  
    value: 0,  
    set [propName](v) {  
        this.value = v;  
    }  
}  
  
console.log(obj.value);  
// Runs the setter property.  
obj.prop_42 = 777;  
console.log(obj.value);  
  
// Output:  
// 0  
// 777  
  
```  
  
 L'esempio di codice seguente crea dinamicamente un nome della proprietà per un oggetto usando la sintassi get.  
  
```javascript  
var propName = "prop_42";  
  
var obj = {  
    get [propName]() {  
        return 777;  
    }  
}  
  
console.log(obj.prop_42);  
  
// Output:  
// 777  
```  
  
 L'esempio di codice seguente crea una proprietà calcolata usando la [sintassi della funzione freccia](../javascript/functions-javascript.md) per aggiungere 42 al nome della proprietà.  
  
```javascript  
var obj = {  
    [ 'prop_' + (() => 42)() ]: 42  
};  
```