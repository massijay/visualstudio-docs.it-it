---
title: "Funzione ArrayBuffer.isView (ArrayBuffer) | Microsoft Docs"
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
ms.assetid: 1887324f-892b-4fcd-ad33-748ba9517a06
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Funzione ArrayBuffer.isView (ArrayBuffer)
Determina se un oggetto fornisce una visualizzazione del buffer.  
  
## Sintassi  
  
```javascript  
ArrayBuffer.isView(object)  
```  
  
#### Parametri  
 `object`  
 Obbligatorio.  Oggetto da testare.  
  
## Valore restituito  
 `true` se una delle seguenti condizioni è vera:  
  
-   `object` è un oggetto `DataView`.  
  
-   `object` è una matrice tipizzata.  
  
 In caso contrario, il metodo restituisce `false`.  
  
## Note  
  
## Esempio  
 L'esempio seguente illustra l'uso della funzione `isView` per testare una matrice tipizzata e un oggetto `DataView`.  
  
```javascript  
var uint = new UInt8ClampedArray(10);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(uint) ); // Outputs true  
{  
var dataView = new DataView(uint.buffer);  
  
if(console && console.log) {  
    console.log( ArrayBuffer.isView(dataView) ); // Outputs true.  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv11_winonly](../../javascript/reference/includes/jsv11-winonly-md.md)]  
  
## Vedere anche  
 [Oggetto Uint8ClampedArray](../../javascript/reference/uint8clampedarray-object-javascript.md)