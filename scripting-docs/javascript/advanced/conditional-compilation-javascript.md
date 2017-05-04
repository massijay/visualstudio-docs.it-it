---
title: "Compilazione condizionale (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ConditionalComp_JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "compilazione condizionale"
  - "compilazione condizionale, panoramica"
ms.assetid: a843de4e-3aae-43cd-ad64-477dd00814a2
caps.latest.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 16
---
# Compilazione condizionale (JavaScript)
La compilazione condizionale permette l'utilizzo delle nuove funzionalità del linguaggio [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] senza pregiudicare la compatibilità con versioni precedenti in cui non erano supportate.  
  
> [!WARNING]
>  La compilazione condizionale è supportata in tutte le versioni di Internet Explorer precedenti a Internet Explorer 11.  A partire dalla modalità standard di Internet Explorer 11 e nelle applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] la compilazione condizionale non è supportata.  
  
## Istruzioni  
 La compilazione condizionale è attivata tramite l'istruzione `@cc_on` o tramite un'istruzione `@set` o `@if`.  La compilazione condizionale implica in genere l'uso delle nuove funzionalità di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)], l'inserimento del supporto per il debug in uno script e la tracciatura dell'esecuzione del codice.  
  
 Inserire sempre il codice di compilazione condizionale come commento, in modo che gli host \(ad esempio Netscape Navigator\) che non supportano la compilazione condizionale lo ignoreranno.  Di seguito è riportato un esempio.  
  
```javascript  
/*@cc_on @*/  
/*@if (@_jscript_version >= 4)  
    alert("JavaScript version 4 or better");  
    @else @*/  
    alert("Conditional compilation not supported by this scripting engine.");  
/*@end @*/  
```  
  
 In questo esempio vengono utilizzati delimitatori di commento speciali applicati solo se la compilazione condizionale viene attivata dall'istruzione `@cc_on`.  I motori di script che non supportano la compilazione condizionale vedono solo il messaggio che indica che la compilazione condizionale non è supportata.