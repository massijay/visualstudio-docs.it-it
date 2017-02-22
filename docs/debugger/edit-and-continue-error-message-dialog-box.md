---
title: "Finestra di dialogo di errore di Modifica e continuazione | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.debug.ENC.SupportedButNotAvaiable"
  - "vs.debug.ENC.CannotEditWhileException"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Modifica e continuazione (finestra di dialogo di errore)"
ms.assetid: f98c91c0-447a-4533-85b6-87170a0dc4c3
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Finestra di dialogo di errore di Modifica e continuazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa finestra di dialogo viene visualizzata quando si esegue il debug in un linguaggio in cui è supportata la funzionalità **Modifica e continuazione**, ma questa non è disponibile per il tipo di modifiche apportate al codice.  Nel messaggio di errore sono riportate informazioni più dettagliate.  Questa finestra di dialogo può essere visualizzata per uno dei seguenti motivi:  
  
-   Si è tentato di modificare il codice gestito mentre era abilitato il debug di codice non gestito.  La funzionalità Modifica e continuazione non è compatibile con il debug in modalità mista.  
  
-   Si è tentato di modificare il codice di SQL Server.  
  
-   Si è tentato di modificare il codice durante il debug di un dump di  Dr. Watson.  
  
-   Si è tentato di modificare il codice dopo un'eccezione non gestita e l'opzione **Rimuovi stack di chiamate su eccezioni non gestite** non era selezionata.  
  
-   Si è tentato di modificare il codice durante il debug di un'applicazione di runtime incorporata.  
  
-   Si è tentato di modificare il codice in un programma a cui si era connessi anziché avviandolo dal menu **Debug**.  
  
-   Si è tentato di modificare il codice ottimizzato.  
  
-   Si è tentato di modificare il codice gestito quando la destinazione è un'applicazione a 64 bit.  Se si desidera utilizzare Modifica e continuazione, è necessario impostare la destinazione su x86 \(**Proprietà di *Project***, scheda **Compilazione**, **Impostazioni del compilatore avanzate**\).  
  
-   Si è tentato di modificare il codice in un assembly modificato durante il debug e ricaricato.  
  
-   Si è tentato di modificare il codice in un assembly che non è stato caricato.  
  
-   Si è avviato il debug di una versione precedente dell'applicazione, poiché la nuova versione presenta errori di compilazione.  
  
-   Si è tentato di modificare il codice durante l'esecuzione.  
  
## Elenco UIElement  
 **OK**  
 Chiudere la finestra di dialogo e annullare il tentativo di modifica immediatamente precedente.  
  
## Vedere anche  
 [Modifiche e limitazioni del codice supportato \(C\+\+\)](../debugger/supported-code-changes-cpp.md)