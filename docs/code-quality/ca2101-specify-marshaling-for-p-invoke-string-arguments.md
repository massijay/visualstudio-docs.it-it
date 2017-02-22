---
title: "CA2101: Specificare il marshalling per gli argomenti di stringa P/Invoke | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyMarshalingForPInvokeStringArguments"
  - "CA2101"
helpviewer_keywords: 
  - "CA2101"
  - "SpecifyMarshalingForPInvokeStringArguments"
ms.assetid: 9d1abfc3-d320-41e0-9f6e-60cefe6ffe1b
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2101: Specificare il marshalling per gli argomenti di stringa P/Invoke
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyMarshalingForPInvokeStringArguments|  
|CheckId|CA2101|  
|Category|Microsoft.Globalization|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un membro di platform invoke consente i chiamanti parzialmente attendibili, presenta un parametro di stringa e non esegue il marshalling della stringa.  
  
## Descrizione della regola  
 Quando si esegue la conversione da Unicode ad ANSI, è possibile che non tutti i caratteri Unicode possano essere rappresentati in una tabella codici ANSI specifica.  Tramite il *mapping più appropriato* si tenta di risolvere il problema sostituendo un carattere con il carattere che non può essere rappresentato.  L'utilizzo di questa funzionalità può causare una potenziale vulnerabilità della sicurezza poiché non è possibile controllare il carattere scelto.  Ad esempio, è possibile che tramite codice dannoso venga creata intenzionalmente una stringa Unicode contenente caratteri non trovati in una determinata tabella codici che vengono convertiti in caratteri speciali del file system come ".." o "\/".  Si noti inoltre che i controlli di sicurezza per caratteri speciali vengono frequentemente eseguiti prima che la stringa sia convertita in ANSI.  
  
 Il mapping più appropriato rappresenta l'impostazione predefinita per la conversione non gestita da WChar a MByte.  A meno che il mapping più appropriato non venga disabilitato in modo esplicito, il codice potrebbe contenere una vulnerabilità della sicurezza causata da questo problema.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, eseguire esplicitamente il marshalling dei dati di tipo stringa.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un metodo che viola questa regola e viene spiegato come correggere la violazione.  
  
 [!code-cs[FxCop.Security.PinvokeAnsiUnicode#1](../code-quality/codesnippet/CSharp/ca2101-specify-marshaling-for-p-invoke-string-arguments_1.cs)]