---
title: "Modifiche al codice supportate (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Modifica e continuazione [C#], modifiche supportate al codice"
ms.assetid: c7a48ea9-5a7f-4328-a9d7-f0e76fac399d
caps.latest.revision: 27
caps.handback.revision: 27
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Modifiche al codice supportate (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La funzionalità Modifica e continuazione è in grado di gestire la maggior parte dei tipi di modifiche al codice all'interno del corpo del metodo.  Tuttavia, non è possibile applicare durante il debug la maggior parte delle modifiche all'esterno del corpo del metodo nonché alcune modifiche all'interno del corpo del metodo.  Per applicare tali modifiche non supportate, interrompere il debug e riavviarlo utilizzando una versione aggiornata del codice.  
  
 Le seguenti modifiche non possono essere applicate al codice C\# durante una sessione di debug:  
  
-   Modifiche all'istruzione corrente o a qualsiasi altra istruzione attiva.  
  
     Le istruzioni attive includono qualsiasi istruzione, nelle funzioni presenti nello stack di chiamate, che è stata chiamata per ottenere l'istruzione corrente.  
  
     L'istruzione corrente è contrassegnata con uno sfondo giallo nella finestra del codice sorgente.  Le altre istruzioni attive sono contrassegnate con uno sfondo ombreggiato e sono di sola lettura.  È possibile cambiare i colori predefiniti nella finestra di dialogo **Opzioni**.  
  
-   Modifica della firma di un tipo.  
  
-   Aggiunta di un metodo anonimo che acquisisce una variabile che non è stata acquisita in precedenza.  
  
-   Aggiunta, rimozione o modifica di attributi.  
  
-   Aggiunta, rimozione o modifica delle direttive `using`.  
  
-   Aggiunta di `foreach`, `using` o `lock` intorno all'istruzione attiva.  
  
## Codice di tipo unsafe  
 Le modifiche a codice non sicuro hanno le stesse limitazioni delle modifiche a codice sicuro, con un'ulteriore restrizione: Modifica e continuazione non supporta modifiche a codice non sicuro all'interno di un metodo che contiene l'operatore `stackalloc`.  
  
## Eccezioni  
 Modifica e continuazione supporta modifiche ai blocchi `catch` e `finally`, tranne che l'aggiunta di un blocco `catch` o `finally` all'istruzione attiva non è consentita.  
  
## Scenari non supportati  
 Modifica e continuazione non è disponibile nei seguenti scenari di debug:  
  
-   Debug di codice LINQ in determinate circostanze.  Per altre informazioni, vedere [Debug di LINQ](../debugger/debugging-linq.md).  
  
    -   Cattura di una variabile che non è stata catturata in precedenza.  
  
    -   Modifica del tipo di espressione di query \(ad esempio, select a \=\> select new { A \= a };\)  
  
    -   Rimozione di un oggetto `where` che contiene un'istruzione attiva.  
  
    -   Rimozione di un oggetto `let` che contiene un'istruzione attiva.  
  
    -   Rimozione di un oggetto `join` che contiene un'istruzione attiva.  
  
    -   Rimozione di un oggetto `orderby` che contiene un'istruzione attiva.  
  
-   Debug in modalità mista \(nativo\/gestito\).  
  
-   Debug SQL.  
  
-   Debug di un dump di  Dr. Watson.  
  
-   Modifica di codice dopo un'eccezione non gestita, quando l'opzione "**Rimuovi stack di chiamate su eccezioni non gestite**" non è selezionata.  
  
-   Debug di un'applicazione di runtime incorporata.  
  
-   Debug di un'applicazione che dispone dell'opzione **Connetti a** invece dell'esecuzione dell'applicazione scegliendo **Avvia** dal menu **Debug**.  
  
-   Debug di codice ottimizzato.  
  
-   Debug di una versione precedente del codice dopo l'esito negativo della compilazione di una nuova versione a causa di errori di compilazione.  
  
## Vedere anche  
 [Modifica e continuazione \(Visual C\#\)](../debugger/edit-and-continue-visual-csharp.md)   
 [Procedura: utilizzare Modifica e continuazione \(C\#\)](../debugger/how-to-use-edit-and-continue-csharp.md)