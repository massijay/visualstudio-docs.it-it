---
title: "Oggetto Debug (JavaScript) | Microsoft Docs"
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
  - "debug"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "Debug (oggetto)"
  - "oggetto Debug, informazioni sull'oggetto Debug"
ms.assetid: 42a367ec-beb1-4e59-8342-34c326eca042
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Oggetto Debug (JavaScript)
Oggetto globale intrinseco che invia l'output a un debugger.  
  
## Sintassi  
  
```  
Debug.function  
```  
  
## Note  
 Non creare l'istanza l'oggetto Debug. È possibile accedere a tutte le proprietà e metodi chiamando `function`.  
  
 Esistono diversi modi per eseguire il debug di Internet Explorer e delle app di [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)]. Nelle app di [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)] le funzioni `write` e `writeln` dell'oggetto `Debug` visualizzano le stringhe nella finestra di dialogo **Output** di Visual Studio in fase di esecuzione. Per altre informazioni sul debug delle app di [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)], vedere [Eseguire il debug di app in Visual Studio](~/debugger/debug-store-apps-in-visual-studio.md).  
  
 Per eseguire il debug degli script di Internet Explorer, è necessario che sia installato un debugger di script e che lo script sia eseguito in modalità debug. Internet Explorer 8 e le versioni successive includono il debugger [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)]. Se si usa una versione precedente di Internet Explorer, vedere [Procedura: Attivare e avviare il debug di script da Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
 Se non viene eseguito il debug dello script, le funzioni non hanno alcun effetto.  
  
## Esempio  
 Questo esempio usa la funzione `write` per visualizzare il valore della variabile.  
  
```javascript  
var counter = 42; Debug.write("The value of counter is " + counter);  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
## Costanti  
 [Costanti DEBUG](../../javascript/reference/debug-constants.md)  
  
## Proprietà  
 [Proprietà Debug.debuggerEnabled](../../javascript/reference/debug-debuggerenabled-property.md) &#124; [Proprietà Debug.setNonUserCodeExceptions](../../javascript/reference/debug-setnonusercodeexceptions-property.md)  
  
## Funzioni  
 [Funzione Debug.msTraceAsyncCallbackStarting](../../javascript/reference/debug-mstraceasynccallbackstarting-function.md) &#124; [Funzione Debug.msTraceAsyncCallbackCompleted](../../javascript/reference/debug-mstraceasynccallbackcompleted-function.md) &#124; [Funzione Debug.msTraceAsyncOperationCompleted](../../javascript/reference/debug-mstraceasyncoperationcompleted-function.md) &#124; [Funzione Debug.msTraceAsyncOperationStarting](../../javascript/reference/debug-mstraceasyncoperationstarting-function.md) &#124; [Funzione Debug.msUpdateAsyncCallbackRelation](../../javascript/reference/debug-msupdateasynccallbackrelation-function.md) &#124; [Funzione Debug.write](../../javascript/reference/debug-write-function-javascript.md) &#124; [Funzione Debug.writeln](../../javascript/reference/debug-writeln-function-javascript.md)  
  
## Vedere anche  
 [Istruzione debugger](../../javascript/reference/debugger-statement-javascript.md)