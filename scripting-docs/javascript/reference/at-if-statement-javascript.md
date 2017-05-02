---
title: "Istruzione @if (JavaScript) | Microsoft Docs"
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
  - "@if_JavaScriptKeyword"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "@if (istruzione)"
  - "condizionali (istruzioni), if"
  - "elif (istruzione)"
  - "else (istruzione)"
  - "if (istruzione), @if"
ms.assetid: ff11b29d-c06a-4276-b11d-db73e2da98ac
caps.latest.revision: 18
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 18
---
# Istruzione @if (JavaScript)
Esegue un gruppo di istruzioni in base a determinate condizioni, a seconda del valore di un'espressione.  
  
> [!WARNING]
>  La compilazione condizionale non è supportata nella modalità standard di Internet Explorer 11 e nelle applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  La compilazione condizionale è supportata nella modalità standard di Internet Explorer 10 e in tutte le versioni precedenti.  
  
## Sintassi  
  
```  
  
      @if (  
   condition1  
)  
   text1  
[@elif (  
   condition2  
)  
   text2]  
[@else  
   text3]  
@end   
```  
  
## Parametri  
 *condition1, condition2*  
 Facoltativa.  Espressione che può essere impostata come espressione booleana.  
  
 `text1`  
 Facoltativa.  Testo da analizzare se `condition1` è **true**.  
  
 `text2`  
 Facoltativa.  Testo da analizzare se `condition1` è **false** e `condition2` è **true**.  
  
 `text3`  
 Facoltativa.  Testo da analizzare se sia `condition1` che `condition2` sono **false**.  
  
## Note  
 Quando si scrive un'istruzione `@if`, non è necessario inserire ciascuna clausola in una riga distinta.  È possibile utilizzare più clausole **@elif**.  Tutte le clausole **@elif**, tuttavia, devono precedere una clausola **@else**.  
  
 L'istruzione `@if` viene in genere utilizzata per determinare quale testo deve essere utilizzato tra le possibili opzioni disponibili.  
  
 L'utilizzo di variabili di compilazione condizionale in script scritti per pagine ASP o ASP.NET o per programmi per la riga di comando non è un comportamento comune,  in quanto le funzionalità dei compilatori possono essere determinate utilizzando altri metodi.  
  
 Quando si scrive uno script per una pagina Web, aggiungere sempre il codice di compilazione condizionale nei commenti.  In questo modo gli host che non supportano la compilazione condizionale potranno ignorarlo.  
  
## Esempio  
 Nel seguente esempio viene illustrato l'utilizzo dell'istruzione **@if...@elif…@else...@end**.  
  
```javascript  
/*@cc_on @*/  
/*@  
    document.write("JavaScript version: " + @_jscript_version + ".");  
    document.write("<br />");  
    @if (@_win32)  
        document.write("Running on a 32-bit version of Windows.");  
    @elif (@_win16)  
        document.write("Running on a 16-bit version of Windows.");  
    @else  
        document.write("Running on a different operating system.");  
    @end  
@*/  
```  
  
## Requisiti  
 Supportato in tutte le versioni di Internet Explorer, ma non nelle applicazioni [!INCLUDE[win8_appname_long](../../javascript/includes/win8-appname-long-md.md)].  
  
## Vedere anche  
 [Compilazione condizionale](../../javascript/advanced/conditional-compilation-javascript.md)   
 [Variabili di compilazione condizionale](../../javascript/advanced/conditional-compilation-variables-javascript.md)   
 [Istruzione @cc\_on](../../javascript/reference/at-cc-on-statement-javascript.md)   
 [Istruzione @set](../../javascript/reference/at-set-statement-javascript.md)