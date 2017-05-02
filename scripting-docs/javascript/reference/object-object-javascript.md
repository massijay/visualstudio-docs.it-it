---
title: "Oggetto Object (JavaScript) | Microsoft Docs"
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
  - "object"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Object (oggetto)"
ms.assetid: d24ef8fc-217b-4828-94e1-19f72780bae0
caps.latest.revision: 25
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 25
---
# Oggetto Object (JavaScript)
Fornisce funzionalità comuni a tutti gli oggetti [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Sintassi  
  
```  
  
obj  
 = new Object([value])   
```  
  
## Parametri  
 `obj`  
 Obbligatorio.  Nome della variabile a cui l'oggetto `Object` è assegnato.  
  
 *value*  
 Facoltativo.  Uno dei tipi di dati primitivi [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] \(numero, valore booleano o stringa\).  Se il valore è un oggetto, l'oggetto viene restituito invariato.  Se *value* è `null`, **undefined** o non è specificato, viene creato un oggetto senza contenuto.  
  
## Note  
 L' oggetto `Object` è contenuto in tutti gli altri oggetti [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]; tutti i relativi metodi e le proprietà sono disponibili in tutti gli altri oggetti.  I metodi possono essere ridefiniti in oggetti definiti dall'utente e vengono chiamati da [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] al momento opportuno.  Il metodo **toString** è un esempio di metodo `Object` ridefinito frequentemente.  
  
 In questa Guida di riferimento per il linguaggio, la descrizione di ogni metodo `Object` include informazioni di implementazione predefinite e specifiche dell'oggetto per oggetti [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] intrinseci.  
  
## Requisiti  
 `Object Object` è stato introdotto in [!INCLUDE[jsv3text](../../javascript/reference/includes/jsv3text-md.md)].  Alcuni membri dell'elenco seguente sono stati introdotti nelle versioni successive.  
  
## Proprietà  
 La tabella seguente elenca le proprietà dell'oggetto `Object Object`.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|[Proprietà \_\_proto\_\_](../../javascript/reference/proto-property-object-javascript.md)|Specifica il prototipo per un oggetto.|  
|[Proprietà constructor](../../javascript/reference/constructor-property-object-javascript.md)|Specifica la funzione che crea un oggetto.|  
|[Proprietà prototype](../../javascript/reference/prototype-property-object-javascript.md)|Restituisce un riferimento al prototipo per una classe di oggetti.|  
  
## Funzioni  
 La tabella seguente elenca le funzioni dell'oggetto `Object Object`.  
  
|Funzione|Descrizione|  
|--------------|-----------------|  
|[Funzione Object.assign](../../javascript/reference/object-assign-function-object-javascript.md)|Copia i valori da uno o più oggetti di origine in un oggetto di destinazione.|  
|[Funzione Object.create](../../javascript/reference/object-create-function-javascript.md)|Crea un oggetto che ha un prototipo specificato e che contiene facoltativamente le proprietà specificate.|  
|[Funzione Object.defineProperties](../../javascript/reference/object-defineproperties-function-javascript.md)|Aggiunge una o più proprietà a un oggetto e\/o modifica gli attributi di una proprietà esistente.|  
|[Funzione Object.defineProperty](../../javascript/reference/object-defineproperty-function-javascript.md)|Aggiunge una proprietà a un oggetto o modifica gli attributi di una proprietà esistente.|  
|[Funzione Object.freeze](../../javascript/reference/object-freeze-function-javascript.md)|Impedisce la modifica degli attributi e dei valori di proprietà esistenti, e impedisce l'aggiunta di nuove proprietà.|  
|[Funzione Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md)|Restituisce la definizione di una proprietà di dati o di una proprietà di accesso.|  
|[Funzione Object.getOwnPropertyNames](../../javascript/reference/object-getownpropertynames-function-javascript.md)|Restituisce i nomi delle proprietà e dei metodi di un oggetto.|  
|[Funzione Object.getOwnPropertySymbols](../../javascript/reference/object-getownpropertysymbols-function-javascript.md)|Restituisce le proprietà dei simboli di un oggetto.|  
|[Funzione Object.getPrototypeOf](../../javascript/reference/object-getprototypeof-function-javascript.md)|Restituisce il prototipo di un oggetto.|  
|[Funzione Object.is](../../javascript/reference/object-is-function-javascript.md)|Restituisce un valore che indica se due valori sono uguali.|  
|[Funzione Object.isExtensible](../../javascript/reference/object-isextensible-function-javascript.md)|Restituisce un valore che indica se possono essere aggiunte nuove proprietà a un oggetto.|  
|[Funzione Object.isFrozen](../../javascript/reference/object-isfrozen-function-javascript.md)|Restituisce `true` se gli attributi e i valori della proprietà esistenti non possono essere modificati in un oggetto e se non è possibile aggiungere nuove proprietà all'oggetto.|  
|[Funzione Object.isSealed](../../javascript/reference/object-issealed-function-javascript.md)|Restituisce `true` se gli attributi della proprietà esistenti non possono essere modificati in un oggetto e se non è possibile aggiungere nuove proprietà all'oggetto.|  
|[Funzione Object.keys](../../javascript/reference/object-keys-function-javascript.md)|Restituisce i nomi delle proprietà e dei metodi enumerabili di un oggetto.|  
|[Funzione Object.preventExtensions](../../javascript/reference/object-preventextensions-function-javascript.md)|Impedisce l'aggiunta di nuove proprietà a un oggetto.|  
|[Funzione Object.seal](../../javascript/reference/object-seal-function-javascript.md)|Impedisce la modifica degli attributi di proprietà esistenti, e impedisce l'aggiunta di nuove proprietà.|  
|[Funzione Object.setPrototypeOf](../../javascript/reference/object-setprototypeof-function-javascript.md)|Imposta il prototipo di un oggetto.|  
  
## Metodi  
 La tabella seguente elenca i metodi dell'oggetto `Object Object`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Metodo hasOwnProperty](../../javascript/reference/hasownproperty-method-object-javascript.md)|Restituisce un valore booleano che indica se per un oggetto è disponibile una proprietà con il nome specificato.|  
|[Metodo isPrototypeOf](../../javascript/reference/isprototypeof-method-object-javascript.md)|Restituisce un valore booleano che indica se un oggetto esiste nella gerarchia di prototipi di un altro oggetto.|  
|[Metodo propertyIsEnumerable](../../javascript/reference/propertyisenumerable-method-object-javascript.md)|Restituisce un valore booleano che indica se una proprietà specificata è parte di un oggetto e se è enumerabile.|  
|[Metodo toLocaleString](../../javascript/reference/tolocalestring-method-object-javascript.md)|Restituisce un oggetto convertito in una stringa in base alle impostazioni locali correnti.|  
|[Metodo toString](../../javascript/reference/tostring-method-object-javascript.md)|Restituisce la rappresentazione in formato stringa di un oggetto.|  
|[Metodo valueOf](../../javascript/reference/valueof-method-object-javascript.md)|Restituisce il valore primitivo dell'opzione specificata.|  
  
## Vedere anche  
 [Oggetti JavaScript](../../javascript/reference/javascript-objects.md)