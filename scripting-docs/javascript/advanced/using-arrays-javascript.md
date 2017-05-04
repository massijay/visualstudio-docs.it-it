---
title: "Utilizzo di matrici (JavaScript) | Microsoft Docs"
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
helpviewer_keywords: 
  - "matrici [JavaScript]"
  - "matrici [JavaScript], oggetti"
ms.assetid: 785c5acd-b8b3-4152-af9a-dd42ecdd75ba
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Utilizzo di matrici (JavaScript)
Le matrici in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] sono *sparse*,  ovvero se è disponibile una matrice con tre elementi numerati 0, 1 e 2, è possibile creare l'elemento 50 senza preoccuparsi degli elementi da 3 a 49.  Se la matrice contiene una variabile di lunghezza automatica \(vedere [Oggetti intrinseci](../../javascript/intrinsic-objects-javascript.md) per una spiegazione del monitoraggio automatico della lunghezza della matrice\), la variabile di lunghezza viene impostata su 51 e non su 4.  È possibile creare matrici in cui non sono presenti gap nella numerazione di elementi. Questa operazione non è, tuttavia, necessaria.  
  
 In [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] gli oggetti e le matrici sono reciprocamente quasi identici.  Le due principali differenze consistono nel fatto che gli oggetti diversi dalle matrici non dispongono di una proprietà di lunghezza automatica e che le matrici non dispongono delle proprietà e dei metodi di un oggetto.  
  
## Risoluzione di matrici  
 Le matrici vengono risolte utilizzando parentesi quadre \(\[\]\), come illustrato nell'esempio seguente.  Le parentesi racchiudono un valore numerico o un'espressione che restituisce un numero intero.  
  
```javascript  
var entryNum = 5;  
  
sample = new Array();  
  
sample[1] = "Maple Street";  
sample[entryNum] = 25;  
  
document.write (sample[1]);  
document.write (" ");  
document.write (sample[entryNum]);  
  
// Output: Maple Street 25  
  
```  
  
## Oggetti come matrici associative  
 In genere si utilizza l'operatore punto "." per accedere alle proprietà di un oggetto.  Di seguito è riportato un esempio:  
  
```javascript  
myObject.aProperty  
```  
  
 In questo caso il nome della proprietà è un identificatore.  È possibile accedere alle proprietà di un oggetto anche utilizzando l'operatore di indice \(\[\]\).  In questo caso l'oggetto viene considerato *matrice associativa* in cui i valori dei dati vengono associati alle stringhe.  Di seguito è riportato un esempio:  
  
```javascript  
myObject["aProperty"] // Same as above.  
```  
  
 L'operatore di indice è in genere associato all'accesso agli elementi della matrice.  Quando utilizzato con gli oggetti, l'indice è un valore letterale stringa che rappresenta il nome della proprietà.  
  
 Notare le differenze importanti esistenti tra le due modalità di accesso alle proprietà degli oggetti.  
  
1.  Un nome della proprietà considerato come identificatore \(la sintassi del punto \(.\)\) non può essere modificato come dati.  
  
2.  Un nome della proprietà considerato come indice \(la sintassi delle parentesi quadre \(\[\]\)\) può essere modificato come dati.  
  
 Questa differenza risulta utile quando non si conoscono i nomi delle proprietà fino al momento dell'esecuzione, ad esempio in caso di costruzione di oggetti in base all'input dell'utente.  Per estrarre tutte le proprietà da una matrice associativa, è necessario utilizzare il ciclo `for…in`.