---
title: "Risoluzione dei problemi negli script (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "conversione di tipo automatica"
  - "risoluzione dei problemi degli script"
ms.assetid: 0e0545d9-44e5-4179-befc-99a882c5c672
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Risoluzione dei problemi negli script (JavaScript)
In qualsiasi linguaggio di programmazione esistono situazioni critiche.  Il valore `null` in [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] non si comporta, ad esempio, come il valore `Null` nei linguaggi C o C\+\+.  
  
 Di seguito sono riportate alcune delle aree in cui possono insorgere problemi durante la scrittura di script di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Errori di sintassi  
 È importante prestare attenzione ai dettagli durante la scrittura di script.  Le stringhe, ad esempio, devono essere racchiuse tra virgolette.  
  
## Ordine di interpretazione degli script  
 L'interpretazione di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] fa parte del processo di analisi del codice HTML del browser Web.  Uno script inserito nel tag \<HEAD\> di un documento viene interpretato prima di qualsiasi parte del tag \<BODY\>.  Gli eventuali oggetti creati nel tag \<BODY\> non esistono al momento dell'analisi di \<HEAD\> e non possono essere modificati mediante lo script.  
  
> [!NOTE]
>  Questo comportamento è specifico di Internet Explorer.  Le pagine ASP e WSH e altri host dispongono di modelli di esecuzione differenti.  
  
## Coercizione automatica dei tipi di dati  
 [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] è un linguaggio non fortemente tipizzato dotato di coercizione automatica dei tipi.  Sebbene i valori con tipi di dati diversi non siano uguali, le espressioni dell'esempio seguente restituiscono **true**.  
  
```javascript  
"100" == 100;  
false == 0;  
```  
  
 Per verificare che coincidano sia il tipo che il valore, utilizzare l'operatore di identità \(\=\=\=\).  Entrambe le espressioni seguenti restituiscono false:  
  
```javascript  
"100" === 100;  
false === 0;  
```  
  
## Precedenza tra gli operatori  
 Il concetto di [Precedenza tra gli operatori](../../javascript/operator-subtractprecedence-javascript.md) determina quando viene eseguita un'operazione durante la valutazione di un'espressione.  Nell'esempio seguente la moltiplicazione viene eseguita prima della sottrazione, anche se nell'espressione la sottrazione viene visualizzata per prima.  
  
```javascript  
theRadius = aPerimeterPoint - theCenterpoint * theCorrectionFactor;  
```  
  
## Utilizzo di cicli for...in con gli oggetti  
 Quando si scorrono le proprietà di un oggetto tramite un ciclo [for…in](../../javascript/reference/for-dot-dot-dot-in-statement-javascript.md), non è possibile prevedere o controllare l'ordine di assegnazione dei campi dell'oggetto alla variabile contatore del ciclo.  Inoltre, l'ordine può essere diverso a seconda del tipo di implementazione del linguaggio.  
  
## Parola chiave with  
 L'istruzione [with](../../javascript/reference/with-statement-javascript.md) risulta utile per accedere a proprietà già esistenti in un oggetto specificato, ma non può essere utilizzata per aggiungervi proprietà.  Per creare nuove proprietà in un oggetto, è necessario fare specificamente riferimento all'oggetto.  
  
## Parola chiave this  
 Sebbene la parola chiave `this` venga utilizzata nella definizione di un oggetto per farvi riferimento, non è possibile utilizzare `this` o parole chiave simili per fare riferimento alla funzione attualmente in esecuzione, se tale funzione non è la definizione di un oggetto.  Se la funzione deve essere assegnata a un oggetto come metodo, si può utilizzare la parola chiave `this` nella funzione per fare riferimento all'oggetto.  
  
## Creazione di uno script che scrive uno script in Internet Explorer  
 Se l'interprete rileva un tag \<\/SCRIPT\>, lo script corrente viene terminato.  Per visualizzare il termine "\<\/SCRIPT\>", riscriverlo suddividendolo in almeno due stringhe, ad esempio "\<\/SCR" e "IPT\>", che possono essere concatenate nell'istruzione che le scrive.  
  
## Riferimenti a finestra impliciti in Internet Explorer  
 Dato che più finestre possono essere aperte contemporaneamente, un riferimento a una finestra implicito punta alla finestra corrente.  Per altre finestre, è necessario utilizzare un riferimento esplicito.