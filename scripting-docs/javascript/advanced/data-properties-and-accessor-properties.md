---
title: "Propriet&#224; dei dati e propriet&#224; di accesso | Microsoft Docs"
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
ms.assetid: 7e132831-375d-4728-9a57-5c6f91075b1c
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Propriet&#224; dei dati e propriet&#224; di accesso
In questa sezione sono disponibili tutte le informazioni che possono essere necessarie sulle proprietà dei dati e sulle proprietà di accesso.  
  
### Proprietà dei dati  
 Una *proprietà dei dati* è una proprietà che può ottenere e impostare un valore.  Le proprietà dei dati contengono le proprietà `writable` e `value` nei relativi descrittori.  
  
 Nella tabella seguente sono elencati gli attributi per un descrittore di proprietà dei dati.  
  
|Attributo del descrittore di dati|Descrizione|Predefinito|  
|---------------------------------------|-----------------|-----------------|  
|`value`|Valore corrente della proprietà.|`undefined`|  
|`writable`|`true` o `false`.  Se `writable` è impostato su `true`, il valore della proprietà può essere modificato.|`false`|  
|`enumerable`|`true` o `false`.  Se `enumerable` è impostato su `true`, la proprietà può essere enumerata da un'istruzione `for…in`.|`false`|  
|`configurable`|`true` o `false`.  Se `configurable` è impostato su `true`, gli attributi della proprietà possono essere modificati e la proprietà può essere eliminata.|`false`|  
  
 Se il descrittore non contiene un attributo `value`, `writable`, `get` o `set` e il nome della proprietà specificata non esiste, viene aggiunta una proprietà dei dati.  
  
 Quando l'attributo `configurable` è `false` e `writable` è `true`, gli attributi `writable` e `value` possono essere modificati.  
  
#### Proprietà dei dati aggiunte senza l'utilizzo di defineProperty  
 Se si aggiunge una proprietà dei dati senza utilizzare le funzioni `Object.defineProperty`, `Object.defineProperties` o `Object.create`, tutti gli attributi `writable`, `enumerable` e `configurable` vengono impostati su `true`.  Dopo l'aggiunta, la proprietà può essere modificata utilizzando la funzione `Object.defineProperty`.  
  
 È possibile utilizzare i seguenti metodi per aggiungere una proprietà dei dati:  
  
-   Operatore di assegnazione \(\=\), come in `obj.color = "white";`  
  
-   Valore letterale di un oggetto, come in `obj = { color: "white", height: 5 };`  
  
-   Funzione di costruzione, come descritta in [Utilizzo di costruttori per la definizione di tipi](../../javascript/advanced/using-constructors-to-define-types.md)  
  
### Proprietà di accesso  
 Una *proprietà di accesso* chiama una funzione fornita dall'utente ogni volta che il valore della proprietà viene impostato o recuperato.  Il descrittore di una proprietà di accesso contiene un attributo `get`, un attributo `set` o entrambi.  
  
 Nella tabella seguente sono elencati gli attributi per un descrittore di proprietà di accesso.  
  
|Attributo del descrittore della funzione di accesso|Descrizione|Predefinito|  
|---------------------------------------------------------|-----------------|-----------------|  
|`get`|Funzione che restituisce il valore della proprietà.  La funzione non ha parametri.|`undefined`|  
|`set`|Funzione che imposta il valore della proprietà.  Include un parametro contenente il valore da assegnare.|`undefined`|  
|`enumerable`|`true` o `false`.  Se `enumerable` è impostato su `true`, la proprietà può essere enumerata da un'istruzione `for…in`.|`false`|  
|`configurable`|`true` o `false`.  Se `configurable` è impostato su `true`, gli attributi della proprietà possono essere modificati e la proprietà può essere eliminata.|`false`|  
  
 Quando una funzione di accesso `get` non è definita e viene effettuato un tentativo di accesso al valore della proprietà, viene restituito il valore `undefined`.  Quando una funzione di accesso `set` non è definita e viene effettuato un tentativo di assegnazione di un valore alla proprietà di accesso, non viene eseguita alcuna operazione.  
  
### Modifiche delle proprietà  
 Se l'oggetto dispone già di una proprietà con il nome specificato, gli attributi della proprietà vengono modificati.  Quando si modifica la proprietà, gli attributi non specificati nel descrittore rimangono invariati.  
  
 Se l'attributo `configurable` di una proprietà esistente è `false`, l'unica modifica consentita cambia l'attributo `writable` da `true` a `false`.  
  
 È possibile modificare una proprietà dei dati in una proprietà di accesso e viceversa.  In questo caso, gli attributi `configurable` e `enumerable` non specificati nel descrittore vengono mantenuti nella proprietà.  Altri attributi non specificati nel descrittore sono impostati sui valori predefiniti.  
  
 È possibile definire in modo incrementale le proprietà di accesso configurabili utilizzando più chiamate alla funzione `Object.defineProperty`.  Una chiamata `Object.defineProperty` può, ad esempio, definire solo una funzione di accesso `get`.  Una chiamata successiva sullo stesso nome della proprietà può definire una funzione di accesso `set`.  La proprietà disporrà quindi sia di una funzione di accesso `get` sia di una funzione di accesso `set`.  
  
 Per ottenere un oggetto descrittore che si applica a una proprietà esistente, è possibile utilizzare [Funzione Object.getOwnPropertyDescriptor](../../javascript/reference/object-getownpropertydescriptor-function-javascript.md).  
  
 Per impedire la modifica degli attributi della proprietà, è possibile utilizzare [Funzione Object.seal](../../javascript/reference/object-seal-function-javascript.md) e [Funzione Object.freeze](../../javascript/reference/object-freeze-function-javascript.md).