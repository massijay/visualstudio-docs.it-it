---
title: "Funzione Object.setPrototypeOf (JavaScript) | Microsoft Docs"
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
ms.assetid: a2609f6e-aeee-4c13-b7cf-c31ddf58ff35
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funzione Object.setPrototypeOf (JavaScript)
Imposta il prototipo di un oggetto.  
  
## Sintassi  
  
```  
Object.setPrototypeOf(obj, proto);  
```  
  
#### Parametri  
 `obj`  
 Necessario.  L’oggetto per cui si imposta il prototipo.  
  
 `proto`  
 Necessario.  Il nuovo prototipo dell'oggetto.  
  
## Note  
  
> [!WARNING]
>  Con l'impostazione del prototipo è possibile che vengano ridotte le prestazioni in tutto il codice JavaScript che ha l'accesso a un oggetto il cui prototipo è stato modificato.  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato come impostare la proprietà.  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(Object.getPrototypeOf(rec) === Rectangle.prototype);  // Returns true  
    Object.getPrototypeOf(rec, Object.prototype);  
    console.log(Object.getPrototypeOf(rec) === Rectangle.prototype);  // Returns false  
}  
```  
  
## Esempio  
 Esempio di codice seguente viene illustrato come aggiungere proprietà a un oggetto aggiungendoli al prototipo.  
  
```javascript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
Object.getPrototypeOf(obj, proto);  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## Esempio  
 Esempio di codice seguente aggiunge il `String` oggetto impostando un nuovo prototipo su di esso.  
  
```javascript  
var stringProp = { desc: "description" };  
  
Object.getPrototypeOf(String, stringProp);  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    Object.getPrototypeOf(s1, String); // Can't be set.  
    Object.getPrototypeOf(s2, String);  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]