---
title: "Funzione ScriptEngineMinorVersion (JavaScript) | Microsoft Docs"
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
  - "ScriptEngineMinorVersion"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "ScriptEngineMinorVersion (funzione)"
ms.assetid: caa506a5-e61d-4b2a-8b83-83d56a2f26cd
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Funzione ScriptEngineMinorVersion (JavaScript)
Ottiene il numero di versione secondaria del motore di scripting in uso.  
  
## Sintassi  
  
```  
ScriptEngineMinorVersion()  
```  
  
## Note  
 Il valore restituito corrisponde direttamente alle informazioni sulla versione contenute nella libreria di collegamento dinamico \(DLL\) per il linguaggio di scripting in uso.  
  
## Esempio  
 L'esempio seguente illustra l'uso della funzione `ScriptEngineMinorVersion`.  
  
```javascript  
if (window.ScriptEngineMinorVersion) {  
    console.log(window.ScriptEngineMinorVersion());  
}  
  
//Output: <current minor version>  
  
```  
  
## Requisiti  
 [!INCLUDE[jsv5](../../javascript/reference/includes/jsv5-md.md)]  
  
## Vedere anche  
 [Funzione ScriptEngine](../../javascript/reference/scriptengine-function-javascript.md)   
 [Funzione ScriptEngineBuildVersion](../../javascript/reference/scriptenginebuildversion-function-javascript.md)   
 [Funzione ScriptEngineMajorVersion](../../javascript/reference/scriptenginemajorversion-function-javascript.md)