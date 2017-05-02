---
title: "Errori di sintassi JavaScript | Microsoft Docs"
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
  - "JavaScript"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "errori [JavaScript]"
  - "errori di sintassi, JavaScript"
ms.assetid: 0343dc19-5f5e-4a4c-83da-630b4fbcb3b6
caps.latest.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 10
---
# Errori di sintassi JavaScript
Gli errori di sintassi [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] si verificano quando la struttura di una delle istruzioni [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] viola una o più regole sintattiche.  
  
## Errori  
  
|Numero di errore|Descrizione|  
|----------------------|-----------------|  
|1019|[Impossibile utilizzare 'break' all'esterno di un ciclo](../../javascript/misc/can-t-have-break-outside-of-loop.md)|  
|1020|[Impossibile utilizzare 'continue' all'esterno di un ciclo](../../javascript/misc/can-t-have-continue-outside-of-loop.md)|  
|1030|[Compilazione condizionale disattivata](../../javascript/misc/conditional-compilation-is-turned-off.md)|  
|1027|['default' può essere utilizzato una sola volta in un'istruzione 'switch'](../../javascript/misc/default-can-only-appear-once-in-a-switch-statement.md)|  
|1005|[Previsto '\('](../../javascript/misc/expected-left-parenthesis-javascript.md)|  
|1006|[Previsto '\)'](../../javascript/misc/expected-right-parenthesis-javascript.md)|  
|1012|[Previsto '\/'](../../javascript/misc/expected-minus.md)|  
|1003|[Previsto ':'](../../javascript/misc/expected-colon.md)|  
|1004|[Previsto ';'](../../javascript/misc/expected-semicolon.md)|  
|1032|[Previsto '@'](../../javascript/misc/expected-at.md)|  
|1029|[Previsto '@end'](../../javascript/misc/expected-at-end.md)|  
|1007|[Previsto '&#93;'](../../javascript/misc/expected-right-square-bracket.md)|  
|1008|[Previsto '{'](../../javascript/misc/expected-left-curly-brace.md)|  
|1009|[Previsto '}'](../../javascript/misc/expected-right-curly-brace.md)|  
|1011|[Previsto '\='](../../javascript/misc/expected-equal-javascript.md)|  
|1033|[Previsto 'catch'](../../javascript/misc/expected-catch.md)|  
|1031|[Prevista costante](../../javascript/misc/expected-constant.md)|  
|1023|[Prevista cifra esadecimale](../../javascript/misc/expected-hexadecimal-digit.md)|  
|1010|[Previsto identificatore](../../javascript/misc/expected-identifier-javascript.md)|  
|1028|[Previsto identificatore, stringa o numero](../../javascript/misc/expected-identifier-string-or-number.md)|  
|1024|[Previsto 'while'](../../javascript/misc/expected-while.md)|  
|1014|[Carattere non valido](../../javascript/misc/invalid-character-javascript.md)|  
|1026|[Impossibile trovare l'etichetta](../../javascript/misc/label-not-found.md)|  
|1025|[Etichetta ridefinita](../../javascript/misc/label-redefined.md)|  
|1018|[Istruzione 'return' esterna alla funzione](../../javascript/misc/return-statement-outside-of-function.md)|  
|1002|[Errore di sintassi](../../javascript/misc/syntax-error-javascript.md)|  
|1035|[La parola chiave 'throw' deve essere seguita da un'espressione nella stessa riga di codice sorgente](../../javascript/misc/throw-must-be-followed-by-an-expression-on-the-same-source-line.md)|  
|1016|[Commento senza terminazione](../../javascript/misc/unterminated-comment.md)|  
|1015|[Costante stringa senza terminazione](../../javascript/misc/unterminated-string-constant-javascript.md)|  
  
### Errori dell'host di script  
 I seguenti errori sono in particolare errori relativi all'host di script, ma è possibile che vengano visualizzati occasionalmente.  
  
|Errore|HRESULT|Descrizione|  
|------------|-------------|-----------------|  
|SCRIPT\_E\_RECORDED|0x86664004|Un errore è stato registrato per essere passato tra il motore di script e l'host.  L'host deve passare il codice di errore al chiamante.|  
|SCRIPT\_E\_REPORTED|0x80020101|Il motore di script ha segnalato un'eccezione non gestita all'host tramite IActiveScriptSite::OnScriptError.  L'host può ignorare questo errore.|  
|SCRIPT\_E\_PROPAGATE|0x8002010|È in corso la propagazione di un errore di script al chiamante che potrebbe trovarsi in un thread diverso.  L'host deve passare il codice di errore al chiamante.|  
  
## Vedere anche  
 [Errori di runtime JavaScript](../../javascript/reference/javascript-run-time-errors.md)