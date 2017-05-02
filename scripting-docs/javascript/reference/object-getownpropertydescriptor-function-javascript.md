---
title: "Funzione Object.getOwnPropertyDescriptor (JavaScript) | Microsoft Docs"
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
  - "getOwnPropertyDescriptor (metodo) [JavaScript]"
ms.assetid: 8f0e1c90-c4f9-44c4-bf76-726bacecbc14
caps.latest.revision: 45
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 45
---
# Funzione Object.getOwnPropertyDescriptor (JavaScript)
Ottiene il descrittore di proprietà dell'oggetto specificato.  Un descrittore di proprietà personalizzato viene definito direttamente nell'oggetto e non viene ereditato dal prototipo dell'oggetto.  
  
## Sintassi  
  
```  
Object.getOwnPropertyDescriptor(object, propertyname)  
```  
  
## Parametri  
 `object`  
 Obbligatorio.  Oggetto che contiene la proprietà.  
  
 `propertyname`  
 Obbligatorio.  Nome della proprietà.  
  
## Valore restituito  
 Descrittore della proprietà.  
  
## Note  
 È possibile usare la funzione `Object.getOwnPropertyDescriptor` per ottenere un oggetto descrittore che descrive gli attributi della proprietà.  
  
 Il [Funzione Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md) viene usato per aggiungere o modificare le proprietà.  
  
## Esempio di proprietà di dati  
 L'esempio seguente ottiene un descrittore di proprietà di dati e lo usa per rendere la proprietà di sola lettura.  
  
```javascript  
// Create a user-defined object.  
var obj = {};  
  
// Add a data property.  
obj.newDataProperty = "abc";  
  
// Get the property descriptor.  
var descriptor = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// Change a property attribute.  
descriptor.writable = false;  
Object.defineProperty(obj, "newDataProperty", descriptor);  
  
```  
  
 Per elencare gli attributi della proprietà, è possibile aggiungere il codice seguente a questo esempio.  
  
```javascript  
// Get the descriptor from the object.  
var desc2 = Object.getOwnPropertyDescriptor(obj, "newDataProperty");  
  
// List the descriptor attributes.  
for (var prop in desc2) {  
    document.write(prop + ': ' + desc2[prop]);  
    document.write("<br />");  
}  
  
// Output:  
// value: abc  
// writable: false  
// enumerable: true  
// configurable: true  
```  
  
## Requisiti  
 Tutte le funzionalità sono supportate in [!INCLUDE[jsv9text](../../javascript/includes/jsv9text-md.md)].  
  
 [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)] supporta gli oggetti DOM ma non gli oggetti definiti dall'utente.  Gli attributi `enumerable` e `configurable` possono essere specificati, ma non vengono usati.  
  
## Vedere anche  
 [Prototipi di Document Object Model, parte 2: supporto della funzione di accesso \(getter\/setter\)](http://msdn.microsoft.com/library/dd229916\(v=VS.85\).aspx)   
 [Funzione Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)