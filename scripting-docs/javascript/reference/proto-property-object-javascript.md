---
title: "Propriet&#224; __proto__ (Object) (JavaScript) | Microsoft Docs"
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
  - "__proto__"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 97c3f84d-125e-4905-b921-b021264964ee
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Propriet&#224; __proto__ (Object) (JavaScript)
Contiene un riferimento al prototipo interno dell'oggetto specificato.  
  
## Sintassi  
  
```  
object.__proto__  
```  
  
#### Parametri  
 `object`  
 Necessario.  Oggetto su cui impostare il prototipo.  
  
## Note  
 La proprietà `__proto__` viene quindi utilizzata per impostare il prototipo di un oggetto.  
  
 L'oggetto o la funzione eredita tutti i metodi e le proprietà di un nuovo prototipo, con tutti i metodi e le proprietà nella catena di prototipi del nuovo prototipo.  Un oggetto può avere un solo prototipo \(esclusi i prototipi ereditati nella catena di prototipi\), quindi quando si chiama la proprietà `__proto__`, viene sostituito il prototipo precedente.  
  
 È possibile impostare il prototipo solo su un oggetto estensibile.  Per ulteriori informazioni, vedi [Funzione Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md).  
  
> [!NOTE]
>  Il nome della proprietà `__proto__` inizia e termina con due caratteri di sottolineatura.  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato come impostare il prototipo per un oggetto.  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
if (console && console.log) {  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns true  
    rec.__proto__ = Object.prototype;  
    console.log(rec.__proto__ === Rectangle.prototype);  // Returns false  
}  
```  
  
## Esempio  
 Nell'esempio di codice riportato di seguito viene illustrato in che modo aggiungere proprietà a un oggetto aggiungendole al prototipo.  
  
```javascript  
var proto = { y: 2 };  
  
var obj = { x: 10 };  
obj.__proto__ = proto;  
  
proto.y = 20;  
proto.z = 40;  
  
if (console && console.log) {  
    console.log(obj.x === 10);  // Returns true  
    console.log(obj.y === 20);  // Returns true  
    console.log(obj.z === 40);  // Returns true  
}  
```  
  
## Esempio  
 Nell'esempio di codice vengono aggiunte proprietà all'oggetto `String` impostando un nuovo prototipo.  
  
```javascript  
var stringProp = { desc: "description" };  
  
String.__proto__ = stringProp;  
var s1 = "333";  
var s2 = new String("333");  
  
if (console && console.log) {  
  
    console.log(String.desc === "description"); // Returns true  
    console.log(s1.desc === "description");     // Returns false  
    console.log(s2.desc === "description");     // Returns false  
  
    s1.__proto__ = String;  // Can't be set.  
    s2.__proto__ = String;  
  
    console.log(s1.desc === "description"); // Returns false  
    console.log(s2.desc === "description"); // Returns true  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]  
  
## Vedere anche  
 [Prototipi ed ereditarietà del prototipo](../../javascript/advanced/prototypes-and-prototype-inheritance.md)