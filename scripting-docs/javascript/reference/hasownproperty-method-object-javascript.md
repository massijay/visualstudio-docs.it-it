---
title: "Metodo hasOwnProperty (Object) (JavaScript) | Microsoft Docs"
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
  - "hasOwnProperty"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Metodo hasOwnProperty"
ms.assetid: 3eb69d69-486f-4792-9518-4452aef369ca
caps.latest.revision: 15
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 15
---
# Metodo hasOwnProperty (Object) (JavaScript)
Determina se un oggetto contiene una proprietà con il nome specificato.  
  
## Sintassi  
  
```  
  
object.hasOwnProperty(proName)  
```  
  
## Parametri  
 `object`  
 Necessario.  Istanza di un oggetto.  
  
 `proName`  
 Necessario.  Valore stringa di un nome di proprietà.  
  
## Note  
 Il metodo `hasOwnProperty` restituisce `true` se `object` include una proprietà del nome specificato e, in caso contrario, `false`.  Questo metodo non consente di verificare le proprietà nella catena di prototipi dell'oggetto. La proprietà deve essere un membro dell'oggetto stesso.  
  
 Questa proprietà non è supportata negli oggetti host per Internet Explorer 8 e versione precedente.  
  
## Esempio  
 Nell'esempio riportato di seguito tutti gli oggetti `String` condividono un metodo split comune.  Nel codice seguente verranno visualizzati **false** e **true**.  
  
```javascript  
var s = new String("Sample");  
document.write(s.hasOwnProperty("split"));  
document.write("<br/>");  
document.write(String.prototype.hasOwnProperty("split"));  
  
// Output:  
// false  
// true  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv55](../../javascript/reference/includes/jsv55-md.md)]  
  
## Vedere anche  
 [Operatore in](../../javascript/reference/in-operator-decrementjavascript.md)