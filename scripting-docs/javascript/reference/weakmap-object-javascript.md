---
title: "Oggetto WeakMap (JavaScript) | Microsoft Docs"
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
  - "WeakMap"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 4682d2dc-caf9-4fa8-8313-a0a0b804fd1d
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Oggetto WeakMap (JavaScript)
Raccolta di coppie chiave\/valore in cui ogni chiave è un riferimento a un oggetto.  
  
## Sintassi  
  
```  
weakmapObj = new WeakMap()  
```  
  
## Note  
 Un oggetto `WeakMap` non può essere enumerato.  
  
 Se si aggiunge un valore alla raccolta utilizzando una chiave esistente, il nuovo valore sostituisce quello vecchio.  
  
 In un oggetto `WeakMap`, i riferimenti agli oggetti principali vengono conservati poco.  Ciò significa che `WeakMap` non impedirà il verificarsi di un Garbage Collection sugli oggetti chiave.  Quando non esistono riferimenti \(diversi da `WeakMap`\) agli oggetti chiave, un Garbage Collector potrebbe raccogliere gli oggetti chiave.  
  
## Proprietà  
 Nella tabella seguente sono elencate le proprietà dell'oggetto `WeakMap`.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|[Costruttore](../../javascript/reference/constructor-property-weakmap.md)|Specifica la funzione che crea un oggetto `WeakMap`.|  
|[prototipo](../../javascript/reference/prototype-property-weakmap.md)|Restituisce un riferimento al prototipo per un oggetto `WeakMap`.|  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `WeakMap`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[clear](../../javascript/reference/clear-method-weakmap-javascript.md)|Rimuove tutti gli elementi da `WeakMap`.|  
|[elimina](../../javascript/reference/delete-method-weakmap-javascript.md)|Rimuove un elemento specificato da un insieme `WeakMap`.|  
|[get](../../javascript/reference/get-method-weakmap-javascript.md)|Restituisce un elemento specificato da un oggetto `WeakMap`.|  
|[has](../../javascript/reference/has-method-weakmap-javascript.md)|Restituisce `true` se l'oggetto `WeakMap` contiene un elemento specificato.|  
|[set](../../javascript/reference/set-method-weakmap-javascript.md)|Aggiunge un nuovo elemento a `WeakMap`.|  
|[toString](../../javascript/reference/tostring-method-weakmap-javascript.md)|Restituisce una rappresentazione di stringa di un oggetto `WeakMap`.|  
|[valueOf](../../javascript/reference/valueof-method-weakmap-javascript.md)|Restituisce il valore primitivo dell'oggetto specificato.|  
  
## Esempio  
 Nell'esempio seguente viene illustrato come aggiungere dei membri a un oggetto `WeakMap` e quindi recuperarli.  
  
```javascript  
var dog = {  
    breed: "yorkie"  
}  
  
var cat = {  
    breed: "burmese"  
}  
  
var wm = new WeakMap();  
wm.set(dog, "fido");  
wm.set(cat, "pepper");  
  
document.write(wm.get(dog) + ": ");  
document.write(dog.breed);  
document.write("<br />");  
document.write(wm.get(cat) + ": ");  
document.write(cat.breed);  
  
// Output:  
// fido: yorkie  
// pepper: burmese  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv11](../../javascript/reference/includes/jsv11-md.md)]