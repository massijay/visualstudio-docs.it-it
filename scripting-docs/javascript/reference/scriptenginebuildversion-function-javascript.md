---
title: "Funzione ScriptEngineBuildVersion (JavaScript) | Microsoft Docs"
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
  - "ScriptEngineBuildVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineBuildVersion (funzione)"
ms.assetid: 7e255030-b0a3-420b-9c96-bb3e93c9333f
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Funzione ScriptEngineBuildVersion (JavaScript)
Ottiene il numero di versione build del motore di scripting in uso.  
  
## Sintassi  
  
```  
ScriptEngineBuildVersion()  
```  
  
## Note  
 Il valore restituito corrisponde direttamente alle informazioni sulla versione contenute nella libreria di collegamento dinamico \(DLL\) per il linguaggio di scripting in uso.  
  
## Esempio  
 L'esempio seguente illustra l'uso della funzione `ScriptEngineBuildVersion`:  
  
```javascript  
if(window.ScriptEngineBuildVersion) {  
    console.log(window.ScriptEngineBuildVersion());  
}  
  
// Output: <current build version>  
```  
  
## Requisiti  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Vedere anche  
 [Funzione ScriptEngine](../../javascript/reference/scriptengine-function-javascript.md)   
 [Funzione ScriptEngineMajorVersion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)   
 [Funzione ScriptEngineMinorVersion](../../javascript/reference/scriptengineminorversion-function-javascript.md)