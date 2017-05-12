---
title: "Raccolte (JavaScript) | Microsoft Docs"
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
ms.assetid: 23c26185-6a7b-4b69-9d22-63e1841b4905
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Raccolte (JavaScript)
È possibile utilizzare gli oggetti raccolta [Map](../../javascript/reference/map-object-javascript.md), [Set](../../javascript/reference/set-object-javascript.md) e [WeakMap](../../javascript/reference/weakmap-object-javascript.md) per archiviare valori e oggetti.  Questi oggetti forniscono metodi pratici per l'aggiunta e il recupero dei membri tramite una chiave o un valore anziché un indice.  Per accedere ai membri di una raccolta utilizzando un indice, utilizzare un oggetto `Array`.  Per ulteriori informazioni, vedere [Utilizzo di matrici](../../javascript/advanced/using-arrays-javascript.md).  
  
> [!CAUTION]
>  `Map`, `Set` e `WeakMap` non sono supportati nelle versioni del browser precedenti a Internet Explorer 11.  Per ulteriori informazioni sul supporto del controllo delle versioni, vedere [Informazioni sulla versione](../../javascript/reference/javascript-version-information.md).  
  
## Utilizzo di raccolte  
 Gli oggetti `Map` e `WeakMap` archiviano coppie di chiave\/valore e consentono di aggiungere, recuperare e rimuovere membri mediante la chiave.  La chiave e il valore possono essere di qualsiasi tipo.  L'oggetto `Set` archivia valori di qualsiasi tipo.  
  
 Gli oggetti `Map` e `Set` consentono di enumerare i membri della raccolta mediante il metodo `forEach` e di verificare le dimensioni della raccolta tramite il metodo `size`.  Al contrario, l'oggetto `WeakMap` non è enumerabile.  Per questa raccolta, i riferimenti alle chiavi sono inclusi in modo debole.  Utilizzare `WeakMap` se si desidera che il Garbage Collector determini se l'app deve mantenere ogni membro della raccolta in memoria.  Ad esempio, ciò può essere utile negli scenari di memorizzazione nella cache in cui gli oggetti memorizzati sono molto grandi e non si desidera tenerli in memoria se non è necessario.  In alcuni scenari, è possibile utilizzare questo oggetto per impedire perdite di memoria.  
  
 Nell'esempio che segue viene illustrato come utilizzare l'oggetto `Map`:  In questo esempio, si accede ai membri tramite `get` e `forEach`.  La funzione di callback in `forEach` può accettare fino a tre parametri, che forniscono il valore dell'elemento della raccolta corrente, la chiave dell'elemento corrente e l'oggetto raccolta stesso.  
  
```javascript  
var m = new Map();  
m.set(1, "black");  
m.set(2, "red");  
m.set("colors", 2);  
m.set({x:1}, 3);  
  
document.write(m.get(2));  
document.write("<br />");  
  
m.forEach(function (value, key, mapObj) {  
    document.write(item.toString() + "<br />");  
});  
  
// Output:  
// red  
  
// black  
// red  
// 2  
// 3  
  
```  
  
 L'utilizzo di `WeakMap` è simile a `Map`, ma è possibile recuperare i membri solo utilizzando `get`.  Per un esempio, vedere l'oggetto [WeakMap](../../javascript/reference/weakmap-object-javascript.md).  
  
 Nell'esempio che segue viene illustrato come utilizzare l'oggetto `Set`:  In questo esempio, la funzione di callback accetta un parametro, che corrisponde al valore dell'elemento della raccolta corrente.  
  
```javascript  
var s = new Set();  
s.add("Thomas Jefferson");  
s.add(1776);  
s.add("founding father");  
  
s.forEach(function (value) {  
    document.write(item.toString() + ", ");  
});  
  
// Output:  
// Thomas Jefferson, 1776, founding father,  
  
```  
  
## Vedere anche  
 [JavaScript avanzato](../../javascript/advanced/advanced-javascript.md)