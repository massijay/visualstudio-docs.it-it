---
title: "Istruzione debugger (JavaScript) | Microsoft Docs"
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
  - "debugger_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "debugger (istruzione)"
ms.assetid: c6d2e193-c1f7-4fb3-8a4e-cc9823174ae4
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Istruzione debugger (JavaScript)
Sospende l'esecuzione.  
  
## Sintassi  
  
```  
debugger  
```  
  
## Note  
 Le istruzioni `debugger` possono essere inserite in qualsiasi punto delle procedure di sospensione dell'esecuzione.  L'utilizzo dell'istruzione `debugger` è analogo all'impostazione di un punto di interruzione nel codice.  
  
 L'istruzione `debugger` sospende l'esecuzione, ma non chiude i file o cancella le variabili.  
  
> [!NOTE]
>  L'istruzione `debugger` non ha alcun effetto a meno che lo script non sia in fase di debug.  
  
## Esempio  
 Nell'esempio seguente viene utilizzata l'istruzione `debugger` per la sospensione dell'esecuzione di ogni iterazione del ciclo `for`.  
  
> [!NOTE]
>  Per eseguire l'esempio, è necessario che sia installato un debugger di script e lo script deve essere eseguito in modalità debug.  
>   
>  Internet Explorer 8 include il debugger [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Se si utilizza una versione precedente di Internet Explorer, vedere [Procedura: attivare e avviare il debug di script da Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```javascript  
for(i = 1; i<5; i++) {  
   // Print i to the Output window.  
   Debug.write("loop index is " + i);  
   // Wait for user to resume.  
   debugger  
}  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Vedere anche  
 [Istruzioni JavaScript](../../javascript/reference/javascript-statements.md)   
 [Compilazione condizionale](../../javascript/advanced/conditional-compilation-javascript.md)