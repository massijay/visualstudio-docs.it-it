---
title: "Metodo isPrototypeOf (Object) (JavaScript) | Microsoft Docs"
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
  - "isPrototypeOf"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "isPrototypeOf (metodo)"
ms.assetid: 9c821319-c208-480f-915e-565ef6e017b6
caps.latest.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 12
---
# Metodo isPrototypeOf (Object) (JavaScript)
Determina se un oggetto esiste nella catena di prototipi di un altro oggetto.  
  
## Sintassi  
  
```  
  
prototype.isPrototypeOf(object)  
```  
  
## Parametri  
 `prototype`  
 Obbligatorio.  Prototipo di oggetto.  
  
 `object`  
 Obbligatorio.  Altro oggetto di cui è necessario verificare la catena di prototipi.  
  
## Note  
 Il metodo `isPrototypeOf` restituisce `true` se `object` include `prototype` nella catena di prototipi.  La catena di prototipi viene utilizzata per condividere funzionalità tra istanze dello stesso tipo di oggetto.  Il metodo `isPrototypeOf` restituisce `false` se `object` non è un oggetto oppure se `prototype` non è presente nella catena di prototipi di `object`.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato l'utilizzo del metodo `isPrototypeOf`.  
  
```javascript  
function Rectangle() {  
}  
  
var rec = new Rectangle();  
  
document.write(Rectangle.prototype.isPrototypeOf(rec));  
  
// Output: true  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vedere anche  
 [Proprietà prototype \(Object\)](../../javascript/reference/prototype-property-object-javascript.md)