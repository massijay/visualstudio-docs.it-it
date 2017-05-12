---
title: "Oggetto Symbol (JavaScript) | Microsoft Docs"
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
ms.assetid: 2ad059f1-4b7f-4758-882a-c74ce1283ab0
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Oggetto Symbol (JavaScript)
Consente di creare un identificatore univoco.  
  
## Sintassi  
  
```  
obj = Symbol(desc)  
```  
  
#### Parametri  
 `desc`  
 Facoltativo.  Descrizione del simbolo.  
  
## Note  
 Gli oggetti Symbol consentono di aggiungere proprietà agli oggetti esistenti senza possibili interferenze con le proprietà degli oggetti esistenti, senza alcuna visibilità imprevista e senza altre aggiunte non coordinate da parte di altro codice.  
  
 Symbol è un tipo di dati primitivi.  Non è possibile creare oggetti Symbol con l'operatore `new`.  
  
 Per aggiungere oggetti Symbol al registro di simboli globali, usare le funzioni `Symbol.for` e `Symbol.keyFor`.  Se si serializzano i simboli sotto forma di stringhe, usare il registro dei simboli globali per assicurare il mapping di una particolare stringa al simbolo corretto per tutte le ricerche.  
  
 JavaScript include i valori predefiniti di Symbol seguenti che sono disponibili nell'ambito globale.  
  
|Simbolo|Descrizione|  
|-------------|-----------------|  
|`Symbol.hasInstance`|Questo metodo determina se un oggetto costruttore riconosce un oggetto come una delle istanze del costruttore.  Viene usato internamente dall'operatore `instanceof`.|  
|`Symbol.isConcatSpreadable`|Questa proprietà restituisce un valore booleano che indica se un oggetto deve essere semplificato nei relativi elementi matrice da `Array.concat`.|  
|`Symbol.iterator`|Questo metodo restituisce l'iteratore predefinito per un oggetto.  Viene usato internamente dall'istruzione `for…of`.|  
|`Symbol.toPrimitive`|Questo metodo converte un oggetto in un valore primitivo corrispondente.  Viene usato internamente dall'operazione astratta `ToPrimitive`.|  
|`Symbol.toStringTag`|Questa proprietà restituisce un valore stringa che viene usato per creare la descrizione predefinita della stringa di un oggetto.  Viene usata internamente dal metodo `Object.toString` del metodo predefinito.|  
|`Symbol.unscopables`|Questa proprietà restituisce un oggetto le cui proprietà sono escluse dai binding di ambiente `with` dell'oggetto associato.|  
  
## Funzioni  
 Nella tabella seguente sono elencate le funzioni dell'oggetto `Symbol`.  
  
|||  
|-|-|  
|Proprietà|Descrizione|  
|[Symbol.for](../../javascript/reference/symbol-for-function-javascript.md)|Restituisce il simbolo relativo a una chiave specificata o, se la chiave non è presente, crea un nuovo oggetto simbolo con la nuova chiave.|  
|[Symbol.keyFor](../../javascript/reference/symbol-keyfor-function-javascript.md)|Restituisce la chiave per un simbolo specificato.|  
|||  
  
## Esempio  
  
```javascript  
(function() {  
  
    // module-scoped symbol  
    var key = Symbol("description");  
  
    function MyClass(privateData) {  
      this[key] = privateData;  
    }  
  
    MyClass.prototype = {  
      someFunc: function() {  
        return "data: " + this[key];  
      }  
    };  
  
    var c = new MyClass("private data")  
    console.log(key);  
    console.log(c["key"]);  
    console.log(c.someFunc());  
  
})();  
  
// Output:  
// undefined  
// undefined  
// data: private data  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]