---
title: "Funzione Debug.write (JavaScript) | Microsoft Docs"
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
  - "Write"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "write (metodo) [JavaScript]"
ms.assetid: fd1cfbb3-46cb-47cc-896c-a70d457dd413
caps.latest.revision: 22
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 22
---
# Funzione Debug.write (JavaScript)
Invia le stringhe al debugger di script.  
  
## Sintassi  
  
```  
  
Debug.write([str1 [, str2 [, ... [, strN]]]])  
```  
  
## Parametri  
 *str1, str2, ... , strN*  
 Facoltativo.  Stringhe da inviare al debugger di script.  
  
## Note  
 La funzione `Debug.write` invia le stringhe alla finestra di controllo immediato del debugger di script in fase di esecuzione.  Se lo script non è in fase di debug, la funzione `Debug.write` non è attiva.  
  
 La funzione `Debug.write` è quasi identica alla funzione `Debug.writeln`.  L'unica differenza è che la funzione `Debug.writeln` invia un carattere di nuova riga dopo aver inviato le stringhe.  
  
## Esempio  
 In questo esempio viene utilizzata la funzione `Debug.write` per visualizzare il valore della variabile nella finestra di controllo immediato del debugger dello script.  
  
> [!NOTE]
>  Per eseguire l'esempio, è necessario che sia installato un debugger di script e lo script deve essere eseguito in modalità debug.  
>   
>  Internet Explorer 8 include il debugger [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Se si utilizza una versione precedente di Internet Explorer, vedere [Procedura: attivare e avviare il debug di script da Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```javascript  
var counter = 42;  
Debug.write("The value of counter is " + counter);  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Debug](../../javascript/reference/debug-object-javascript.md)  
  
## Vedere anche  
 [Funzione Debug.writeln](../../javascript/reference/debug-writeln-function-javascript.md)