---
title: "Propriet&#224; length (Array) (JavaScript) | Microsoft Docs"
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
  - "length Property"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Array (oggetto)"
  - "Length (proprietà)"
  - "length (proprietà) (array)"
ms.assetid: e1c6377c-2e84-440a-9660-f1f512e4a938
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Propriet&#224; length (Array) (JavaScript)
Ottiene o imposta la lunghezza della matrice.  Si tratta di un numero incrementato di uno rispetto all'elemento massimo definito in una matrice.  
  
## Sintassi  
  
```  
  
numVar = arrayObj.length   
```  
  
## Parametri  
 `numVar`  
 Obbligatorio.  Qualsiasi numero.  
  
 `arrayObj`  
 Obbligatorio.  Qualsiasi oggetto `Array`.  
  
## Note  
 In JavaScript le matrici sono sparse e gli elementi in una matrice non sono contigue.  La proprietà `length` non è necessariamente il numero di elementi nella matrice.  Ad esempio, nella definizione di matrice seguente `my_array.length` contiene 7, non 2:  
  
```javascript  
var my_array = new Array( );  
my_array[0] = "Test";  
my_array[6] = "Another Test";  
```  
  
 Se la proprietà `length` ha un valore inferiore al suo valore precedente, la matrice verrà troncata e qualsiasi elemento con indici di matrice uguali o maggiori del nuovo valore della proprietà `length` viene perso.  
  
 Se la proprietà della lunghezza è maggiore rispetto al suo valore precedente, la matrice viene espansa e gli eventuali nuovi elementi creati hanno il valore `undefined`.  
  
 Nell'esempio seguente viene illustrato l'uso della proprietà `length`:  
  
```javascript  
var a;  
a = new Array(0,1,2,3,4);  
document.write(a.length);  
  
// Output  
// 5  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
> [!NOTE]
>  A partire dalla modalità standard di Internet Explorer 9, le virgole finali incluse nell'inizializzazione di una matrice vengono gestite in modo diverso.