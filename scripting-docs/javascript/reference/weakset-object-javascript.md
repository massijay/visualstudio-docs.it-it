---
title: "Oggetto WeakSet (JavaScript) | Microsoft Docs"
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
ms.assetid: f97e6e7c-d678-4e32-978e-d949a7cafa3a
caps.latest.revision: 5
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 5
---
# Oggetto WeakSet (JavaScript)
Raccolta di oggetti univoci che possono essere di qualsiasi tipo.  
  
## Sintassi  
  
```  
setObj = new WeakSet()  
```  
  
## Note  
 Se si tenta di aggiungere un elemento non univoco a un oggetto `WeakSet`, il nuovo oggetto non verrà aggiunto alla raccolta.  
  
 Diversamente da `Set`, è possibile aggiungere solo oggetti alla raccolta.  Non è possibile aggiungere valori arbitrari alla raccolta.  
  
 In un oggetto `WeakSet` i riferimenti agli oggetti nel set vengono mantenuti in modo "debole".  Questo significa che `WeakSet` non impedirà il verificarsi di un'operazione di Garbage Collection sugli oggetti.  Quando non sono presenti riferimenti \(diversi da `WeakSet`\) agli oggetti, Garbage Collector potrebbe raccogliere gli oggetti.  
  
 `WeakSet` \(o `WeakMap`\) può essere utile in alcuni scenari che comportano la memorizzazione nella cache di oggetti o metadati di oggetti.  Ad esempio, i metadati per oggetti non estendibili possono essere archiviati in un oggetto `WeakSet` oppure è possibile creare una cache di immagini utente usando `WeakSet`.  
  
## Proprietà  
 Nella tabella seguente sono elencate le proprietà dell'oggetto `WeakSet`.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|constructor|Specifica la funzione che crea un set.|  
|prototype|Restituisce un riferimento al prototipo per un set.|  
  
## Metodi  
 Nella tabella seguente sono elencati i metodi dell'oggetto `WeakSet`:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|add|Aggiunge un elemento a un set.|  
|delete|Rimuove un elemento specificato da un set.|  
|has|Restituisce `true` se il set contiene un elemento specificato.|  
  
## Esempio  
 L'esempio seguente mostra come aggiungere membri a un set e quindi verificare che siano stati aggiunti.  
  
```javascript  
var ws = new WeakSet();  
  
var str = new String("Thomas Jefferson");  
var num = new Number(1776);  
  
ws.add(str);  
ws.add(num);  
  
console.log(ws.has(str));  
console.log(ws.has(num));  
  
ws.delete(str);  
console.log(ws.has(str));  
  
// Output:  
// true  
// true  
// false  
```  
  
## Requisiti  
 [!INCLUDE[jsv12](../../javascript/reference/includes/jsv12-md.md)]