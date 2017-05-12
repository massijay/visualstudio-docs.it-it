---
title: "Metodo findIndex (Array) (JavaScript) | Microsoft Docs"
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
ms.assetid: 3a200cf0-db67-4c7b-89f8-5e9f5dc1a926
caps.latest.revision: 3
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 3
---
# Metodo findIndex (Array) (JavaScript)
Restituisce un valore di indice per il primo elemento della matrice che soddisfa i criteri di test specificati in una funzione di callback.  
  
## Sintassi  
  
```  
arrayObj.findIndex(callbackfn [, thisArg]);  
```  
  
#### Parametri  
 `arrayObj`  
 Obbligatorio.  Oggetto array.  
  
 `callbackfn`  
 Obbligatorio.  La funzione di callback per testare ogni elemento nella matrice.  
  
 `thisArg`  
 Facoltativo.  Specifica l'oggetto `this` nella funzione di callback.  Se non è specificato, l'oggetto `this` è non definito.  
  
## Note  
 Il metodo `findIndex` chiama la funzione di callback una volta per ogni elemento nella matrice, in ordine crescente, finché non viene restituito `true`.  Non appena un elemento restituisce true, `findIndex` restituisce il valore di indice dell'elemento che restituisce true.  Se nessun elemento nella matrice restituisce true, `findIndex` restituisce \-1.  
  
 `findIndex` non modifica l'oggetto array.  
  
## Sintassi della funzione di callback  
 La sintassi della funzione di callback è la seguente:  
  
 `function callbackfn(value, index, thisArg)`  
  
 È possibile dichiarare la funzione di callback usando un massimo di tre parametri.  
  
 I parametri della funzione di callback sono i seguenti.  
  
|Argomento di callback|Definizione|  
|---------------------------|-----------------|  
|`value`|Valore dell'elemento di matrice.|  
|`index`|Indice numerico dell'elemento di matrice.|  
|`arrayObj`|Oggetto array da attraversare.|  
  
## Esempio  
 Nell'esempio seguente la funzione di callback verifica se ogni elemento della matrice è uguale a 2.  
  
```javascript  
[1,2,3].findIndex(function(x) { x == 2; });  
// Returns an index value of 1.  
  
```  
  
## Esempio  
 L'esempio seguente usa la sintassi freccia per testare ogni elemento.  In questo esempio, nessun elemento restituisce `true`, e `findIndex` restituisce \-1.  
  
```  
[1,2,3].findIndex(x => x == 4);  
// Returns an index value of -1.  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]