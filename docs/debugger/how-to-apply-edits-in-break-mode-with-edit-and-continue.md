---
title: "Procedura: applicare modifiche in modalit&#224; di interruzione con Modifica e continuazione | Microsoft Docs"
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
  - "vs.debug.variables.failededit"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "VB"
helpviewer_keywords: 
  - "modalità di interruzione, applicazione di modifiche al codice"
  - "codice, modifica in modalità di interruzione"
  - "codifica, modifica in modalità di interruzione"
  - "Modifica e continuazione [Visual Basic], applicazione di modifiche in modalità di interruzione"
  - "Modifica e continuazione, applicazione di modifiche in modalità di interruzione"
  - "modifica, modalità di interruzione"
ms.assetid: 1eef7498-6a1f-4fba-8146-510adc6375c9
caps.latest.revision: 30
caps.handback.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: applicare modifiche in modalit&#224; di interruzione con Modifica e continuazione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile usare Modifica e continuazione per modificare il codice in modalità di interruzione e continuare senza interrompere e riavviare l'esecuzione.  
  
 Modifica e continuazione non è disponibile nei seguenti scenari di debug:  
  
-   Debug in modalità mista \(nativo\/gestito\).  
  
-   Debug SQL.  
  
-   Debug di un dump di  Dr. Watson.  
  
-   Modifica di codice dopo un'eccezione non gestita, quando l'opzione **Rimuovi stack di chiamate su eccezioni non gestite** non è selezionata.  
  
-   Debug di un'applicazione di runtime incorporata.  
  
-   Debug di un'applicazione con **Connetti a** anziché tramite l'esecuzione dell'applicazione con il comando **Avvia** del menu **Debug**.  
  
-   Debug di codice ottimizzato.  
  
-   Debug di codice gestito quando la destinazione è un'applicazione a 64 bit.  Se si desidera utilizzare Modifica e continuazione, è necessario impostare la destinazione su x86  \(**Proprietà** di *Progetto*, scheda **Compilazione**, **Impostazioni del compilatore avanzate**\).  
  
-   Debug di una versione precedente del codice dopo un tentativo non riuscito di compilazione di una nuova versione a causa della presenza di errori di compilazione.  
  
### Per modificare il codice in modalità di interruzione  
  
1.  Attivare la modalità di interruzione in uno dei seguenti modi:  
  
    -   Impostare un punto di interruzione nel codice, quindi scegliere **Avvia debug** dal menu **Debug** e attendere che l'applicazione raggiunga il punto di interruzione.  
  
         \- oppure \-  
  
    -   Avviare il debug, quindi scegliere **Interrompi tutto** dal menu **Debug**.  
  
         \- oppure \-  
  
    -   Quando si verifica un'eccezione, scegliere **Attiva modifica** in **Informazioni sulle eccezioni**.  
  
2.  Apportare tutte le modifiche desiderate al codice, purché siano valide.  
  
     Per altre informazioni, vedere [Modifiche non supportate in Modifica e continuazione di Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md).  
  
    > [!NOTE]
    >  Se si tenta di apportare una modifica non consentita da Modifica e continuazione, la modifica verrà contrassegnata con una riga ondulata di colore viola e nell'Elenco attività verrà indicata un'attività da eseguire.  Per poter proseguire l'esecuzione del codice, è necessario annullare la modifica non valida del codice.  
  
3.  Scegliere **Continua** dal menu **Debug** per riprendere l'esecuzione.  
  
     Il codice verrà eseguito con le modifiche incorporate nel progetto.  
  
## Vedere anche  
 [Modifiche non supportate in Modifica e continuazione di Visual Basic](../debugger/unsupported-edits-in-visual-basic-edit-and-continue.md)   
 [Modifica e continuazione \(Visual Basic\)](../debugger/edit-and-continue-visual-basic.md)