---
title: "Metodo substring (String) (JavaScript) | Microsoft Docs"
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
  - "substring"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "sottostringhe"
  - "substring (metodo)"
ms.assetid: 9cf9a005-cbe3-42fd-828b-57a39f54224c
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Metodo substring (String) (JavaScript)
Restituisce la sottostringa in corrispondenza della posizione specificata in un oggetto `String`.  
  
## Sintassi  
  
```  
  
      strVariable. substring(start [, end])  
"String Literal".substring(start [, end])   
```  
  
## Parametri  
 `start`  
 Obbligatorio.  Integer dell'indice a base zero che specifica il punto iniziale della sottostringa.  
  
 `end`  
 Facoltativo.  Integer dell'indice a base zero che specifica il punto finale della sottostringa.  La sottostringa include i caratteri fino al carattere indicato da `end` escluso.  
  
 Se `end` viene omesso, vengono restituiti i caratteri da `start` alla fine della stringa originale.  
  
## Note  
 Il metodo `substring` restituisce una stringa contenente la sottostringa a partire da `start` fino a `end` escluso.  
  
 Il metodo **sottostringa** utilizza il valore minore fra `start` e `end` come punto iniziale della sottostringa.  Ad esempio, strvar.substring\(0, 3**\)** e strvar.substring\(3, 0\) restituiscono la stessa sottostringa.  
  
 Se `start` o `end` è `NaN` o negativo, viene sostituito con zero.  
  
 La lunghezza della sottostringa è uguale al valore assoluto della differenza tra `start` e `end`.  Ad esempio, la lunghezza della sottostringa restituita in strvar.substring\(0, 3\) e strvar.substring\(3, 0\) è 3.  
  
## Esempio  
 Nell'esempio seguente viene illustrato l'utilizzo del metodo **substring**.  
  
```javascript  
var s = "The quick brown fox jumps over the lazy dog.";  
var ss = s.substring(10, 15);  
document.write(ss);  
  
// Output:  
// brown  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
## Vedere anche  
 [Metodo substr \(String\)](../../javascript/reference/substr-method-string-javascript.md)