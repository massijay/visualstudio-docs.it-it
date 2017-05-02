---
title: "Metodo toJSON (Date) (JavaScript) | Microsoft Docs"
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
  - "toJSON (metodo)"
ms.assetid: f91df030-e9c9-425e-8e6d-b46bdda66cb6
caps.latest.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 27
---
# Metodo toJSON (Date) (JavaScript)
Utilizzato dal metodo [JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md) per abilitare la trasformazione dei dati di un oggetto per la serializzazione JSON \(JavaScript Object Notation\).  
  
## Sintassi  
  
```  
  
objectname.toJSON()  
```  
  
## Parametri  
 `objectname`  
 Obbligatorio.  Un oggetto per il quale si desidera la serializzazione JSON.  
  
## Note  
 Il metodo `toJSON` viene utilizzato dalla funzione `JSON.stringify`.  `JSON.stringify` serializza un valore [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] nel testo JSON.  Se viene fornito un metodo `toJSON` per `JSON.stringify`, il metodo `toJSON` viene chiamato insieme a `JSON.stringify`.  
  
 Il metodo `toJSON` è un membro incorporato dell'oggetto [Date](../../javascript/reference/date-object-javascript.md) [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Restituisce una stringa data formattata in ISO per il fuso orario UTC \(indicato dal suffisso Z\).  
  
 Puoi eseguire l'override del metodo `toJSON` per il tipo `Date` o definire un metodo `toJSON` per altri tipi di oggetto in modo da raggiungere la trasformazione dei dati per il tipo di oggetto specifico prima della serializzazione JSON.  
  
## Esempio  
 Nell'esempio seguente viene utilizzato il metodo `toJSON` per serializzare i valori del membro di stringa in maiuscolo.  Il metodo `toJSON` viene chiamato quando viene chiamato `JSON.stringify`.  
  
```javascript  
var contact = new Object();  
contact.firstname = "Jesper";  
contact.surname = "Aaberg";  
contact.phone = ["555-0100", "555-0120"];  
  
contact.toJSON = function(key)  
 {  
    var replacement = new Object();  
    for (var val in this)  
    {  
        if (typeof (this[val]) === 'string')  
            replacement[val] = this[val].toUpperCase();  
        else  
            replacement[val] = this[val]  
    }  
    return replacement;  
};  
  
var jsonText = JSON.stringify(contact);  
  
/* The value of jsonText is:  
'{"firstname":"JESPER","surname":"AABERG","phone":["555-0100","555-0120"]}'  
*/  
```  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare il metodo `toJSON` che è un membro incorporato dell'oggetto [Date](../../javascript/reference/date-object-javascript.md).  
  
```javascript  
var dt = new Date('8/24/2009');  
dt.setUTCHours(7, 30, 0);  
var jsonText = JSON.stringify(dt);  
  
/* The value of jsonText is:  
'"2009-08-24T07:30:00Z"'  
*/  
```  
  
## Requisiti  
 [!INCLUDE[jsv58](../../javascript/reference/includes/jsv58-md.md)] **Si applica a:** [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Oggetto JSON](../../javascript/reference/json-object-javascript.md)   
 [Funzione JSON.parse](../../javascript/reference/json-parse-function-javascript.md)   
 [Funzione JSON.stringify](../../javascript/reference/json-stringify-function-javascript.md)   
 [Metodi JavaScript](../../javascript/reference/javascript-methods.md)