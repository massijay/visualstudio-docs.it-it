---
title: "Metodo join (Array) (JavaScript) | Microsoft Docs"
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
  - "join"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Join (metodo)"
  - "concatenazione di stringhe, metodo join"
  - "matrici [Visual Studio], join"
ms.assetid: 20f8fde1-014b-488e-9008-464a86e6b21f
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Metodo join (Array) (JavaScript)
Aggiunge tutti gli elementi di una matrice separati dalla stringa di separazione specificata.  
  
## Sintassi  
  
```  
  
arrayObj.join([separator])   
```  
  
## Parametri  
 `arrayObj`  
 Obbligatorio.  Oggetto `Array`.  
  
 `separator`  
 Facoltativo.  Stringa utilizzata per separare un elemento di una matrice dall'elemento successivo nell'oggetto `String` risultante.  Se omesso, gli elementi della matrice verranno separati da una virgola.  
  
## Note  
 Qualsiasi elemento **undefined** o `null` della matrice è considerato come una stringa vuota.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo **join**.  
  
```javascript  
var a, b;  
a = new Array(0,1,2,3,4);  
b = a.join("-");  
document.write(b);  
  
// Output:  
// 0-1-2-3-4  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv2](../../javascript/reference/includes/jsv2-md.md)]  
  
## Vedere anche  
 [Oggetto String](../../javascript/reference/string-object-javascript.md)