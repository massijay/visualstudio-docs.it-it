---
title: "Funzione Debug.writeln (JavaScript) | Microsoft Docs"
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
  - "writeln"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "writeIn (metodo)"
ms.assetid: c3aad0cd-0486-4161-9ba6-31d672da72af
caps.latest.revision: 17
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 17
---
# Funzione Debug.writeln (JavaScript)
Invia le stringhe al debugger di script, seguito da un carattere di nuova riga.  
  
## Sintassi  
  
```  
  
Debug.writeln([str1 [, str2 [, ... [, strN]]]])  
```  
  
## Parametri  
 *str1, str2, ... , strN*  
 Facoltativo.  Stringhe da inviare al debugger di script.  
  
## Note  
 La funzione `Debug.writeln` invia le stringhe, seguite da un carattere di nuova riga, alla finestra di controllo immediato di Microsoft Script Debugger in fase di esecuzione.  Se lo script non è in fase di debug, la funzione `Debug.writeln` non è attiva.  
  
 La funzione `Debug.writeln` è quasi identica alla funzione `Debug.write`.  L'unica differenza è che la funzione `Debug.write` non invia un carattere di nuova riga dopo l'invio delle stringhe.  
  
## Esempio  
 In questo esempio viene utilizzata la funzione `Debug.writeln` per visualizzare il valore della variabile nella finestra di controllo immediato di Microsoft Script Debugger.  
  
> [!NOTE]
>  Per eseguire l'esempio, è necessario che sia installato un debugger di script e lo script deve essere eseguito in modalità debug.  
>   
>  Internet Explorer 8 include il debugger [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  Se si utilizza una versione precedente di Internet Explorer, vedere [Procedura: attivare e avviare il debug di script da Internet Explorer](http://go.microsoft.com/fwlink/?LinkId=133801).  
  
```javascript  
var counter = 42;  
Debug.writeln("The value of counter is " + counter);  
```  
  
## Requisiti  
 [!INCLUDE[jsv3](../../javascript/reference/includes/jsv3-md.md)]  
  
 **Si applica a**: [Oggetto Debug](../../javascript/reference/debug-object-javascript.md)  
  
## Vedere anche  
 [Funzione Debug.write](../../javascript/reference/debug-write-function-javascript.md)