---
title: "Funzione Array.from (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 1bf59a99-f860-4c4d-b4c6-d5f1f946a490
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Funzione Array.from (Array) (JavaScript)
Restituisce una matrice da un oggetto di tipo matrice o iterabile.  
  
## Sintassi  
  
```  
Array.from (arrayLike [ , mapfn [ , thisArg ] ] );  
```  
  
#### Parametri  
 `arrayLike`  
 Obbligatorio.  Oggetto di tipo matrice o un oggetto iterabile.  
  
 `mapfn`  
 Facoltativo.  Funzione di mapping da chiamare su ogni elemento in `arrayLike`.  
  
 `thisArg`  
 Facoltativo.  Specifica l'oggetto `this` nella funzione di mapping.  
  
## Note  
 Il parametro `arrayLike` deve essere un oggetto con elementi indicizzati e una proprietà `length` o un oggetto iterabile, ad esempio un oggetto `Set`.  
  
 La funzione di mapping facoltativa viene chiamata su ogni elemento nella matrice.  
  
## Esempio  
 L'esempio seguente restituisce una matrice da una raccolta di nodi elemento DOM.  
  
```javascript  
var elemArr = Array.from(document.querySelectorAll('*'));  
var elem = elemArr[0]; // elem contains a reference to the first DOM element  
  
```  
  
## Esempio  
 L'esempio seguente restituisce una matrice di caratteri.  
  
```javascript  
var charArr = Array.from("abc");  
// charArr[0] == "a";  
```  
  
## Esempio  
 L'esempio seguente restituisce una matrice di oggetti contenuti nella raccolta.  
  
```javascript  
var setObj = new Set("a", "b", "c");  
var objArr = Array.from(setObj);  
// objArr[1] == "b";  
  
```  
  
## Esempio  
 L'esempio seguente illustra l'uso della sintassi freccia e una funzione di mapping per modificare il valore degli elementi.  
  
```javascript  
var arr = Array.from([1, 2, 3], x => x * 10);  
// arr[0] == 10;  
// arr[1] == 20;  
// arr[2] == 30;  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]