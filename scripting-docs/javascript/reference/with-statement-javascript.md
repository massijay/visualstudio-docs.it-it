---
title: "Istruzione with (JavaScript) | Microsoft Docs"
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
  - "with_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "With (istruzione)"
ms.assetid: 892c7621-ae9e-4c10-8adb-05532274b1ca
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Istruzione with (JavaScript)
Imposta l'oggetto predefinito per un'istruzione.  
  
## Sintassi  
  
```  
with (object) {  
    statements  
}   
```  
  
## Parametri  
 `object`  
 Oggetto predefinito.  
  
 `statements`  
 Una o più istruzioni per le quali `object` è l'oggetto predefinito.  
  
## Note  
 L'istruzione `with` viene in genere utilizzata per ridurre la quantità di codice necessario in determinate situazioni.  
  
> [!WARNING]
>  L'utilizzo di `with` non è consentito in modalità strict.  L'utilizzo di `with` può rendere più difficili la lettura e il debug del codice e deve essere generalmente evitato.  
  
## Esempio  
 Nell'esempio seguente un oggetto `Math` viene utilizzato ripetutamente.  
  
```javascript  
x = Math.cos(3 * Math.PI) + Math.sin(Math.LN10)   
y = Math.tan(14 * Math.E)  
```  
  
## Esempio  
 Se si riscrive l'esempio per utilizzare l'istruzione `with`, il codice risulterà più conciso:  
  
```javascript  
with (Math){  
   x = cos(3 * PI) + sin (LN10)    
   y = tan(14 * E)  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Istruzione this](../../javascript/reference/this-statement-javascript.md)