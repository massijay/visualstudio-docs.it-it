---
title: "Procedura: Limitare la strumentazione a specifiche funzioni | Microsoft Docs"
ms.custom: ""
ms.date: "12/08/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti per le prestazioni, limitazione della strumentazione alle funzioni"
ms.assetid: bd98d6bf-2560-4eba-b063-2facb09f87c4
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Procedura: Limitare la strumentazione a specifiche funzioni
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile limitare la strumentazione e la raccolta dei dati a uno o più funzioni impostando le opzioni nella pagina **Avanzate** di **Sessione prestazioni** o nelle pagine delle proprietà del binario di destinazione:  
  
-   Se nella pagina delle proprietà della sessione di prestazioni vengono specificate le funzioni, solo tali funzioni vengono instrumentate in tutti i binari instrumentati della sessione.  
  
-   Se nella pagina delle proprietà del binario di destinazione vengono specificate le funzioni, solo le funzioni presenti in quel determinato binario vengono instrumentate.  Le funzioni negli altri binari delle prestazioni vengono instrumentate come al solito.  
  
 Questo tipo di limitazione della raccolta de dati è supportata solo quando viene selezionato il metodo di profilatura tramite strumentazione.  
  
> [!NOTE]
>  È inoltre possibile utilizzare la pagina **Avanzate** delle pagine delle proprietà di **Sessione prestazioni** per impostare le altre opzioni disponibili nello strumento di strumentazione da riga di comando [VSInstr](../profiling/vsinstr.md) disponibile negli strumenti di profilatura.  
  
### Per limitare la strumentazione a funzioni specifiche in una sessione di prestazioni  
  
1.  In **Esplora prestazioni** fare clic con il pulsante destro del mouse sul nome della sessione e scegliere **Proprietà**.  
  
     Verrà visualizzata la finestra di dialogo **Pagine delle proprietà**.  
  
2.  Nella finestra di dialogo **Pagine delle proprietà** scegliere **Avanzate**.  
  
3.  Nella casella di testo **Opzioni di strumentazione aggiuntive** , digitare il nome delle funzioni che si desidera instrumentare utilizzando la seguente sintassi:  
  
     **\/include:** `FuncSpec` **\[;** `FuncSpec` **\]** `...`  
  
     `FuncSpec` è il nome dello spazio dei nomi e il nome della funzione.  Ha il formato `Namespace`**::**`FunctionName`.  Utilizzare un punto e virgola per separare più funzioni.  Utilizzare un asterisco \(\*\) per specificare un carattere jolly per uno o più caratteri.  Ad esempio, **\/include:MyNS::\*** specifica tutte le funzioni nello spazio dei nomi MyNS.  
  
    > [!NOTE]
    >  Per elencare le funzioni in un file binario, aprire una finestra del prompt dei comandi nella directory di installazione degli strumenti di profilatura \(in genere, la directory \\Team Tools\\Performance Tools nella directory di installazione di [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)] \), quindi digitare vsinstr \/DumpFuncs  
  
### Per limitare la strumentazione a specifiche funzioni in un binario  
  
1.  In **Esplora prestazioni** trovare il nome binario nel nodo **Destinazioni** della sessione di prestazioni.  
  
2.  Fare clic con il pulsante destro del mouse sul nome del binario, quindi scegliere **Proprietà**.  
  
     Verrà visualizzata la finestra di dialogo **Pagine delle proprietà**.  
  
3.  Nella finestra di dialogo **Pagine delle proprietà** scegliere **Avanzate**.  
  
4.  Nella casella di testo **Opzioni di strumentazione aggiuntive** , digitare il nome delle funzioni che si desidera instrumentare utilizzando la seguente sintassi:  
  
     **\/include:** `FuncSpec` **\[;** `FuncSpec` **\]** `...`  
  
     `FuncSpec` è il nome dello spazio dei nomi e il nome della funzione.  Ha il formato `Namespace`**::**`FunctionName`.  Utilizzare un punto e virgola per separare più funzioni.  Utilizzare un asterisco \(\*\) per specificare un carattere jolly per uno o più caratteri.  Ad esempio, **\/include:MyNS::\*** specifica tutte le funzioni nello spazio dei nomi MyNS.  
  
    > [!NOTE]
    >  Per elencare le funzioni in un file binario, aprire una finestra del prompt dei comandi nella directory di installazione degli strumenti di profilatura \(in genere, la directory \\Team Tools\\Performance Tools nella directory di installazione di [!INCLUDE[vsprvsts](../code-quality/includes/vsprvsts_md.md)] \), quindi digitare vsinstr \/DumpFuncs  
  
## Vedere anche  
 [Controllo della raccolta di dati](../profiling/controlling-data-collection.md)   
 [Procedura: Limitare la strumentazione a specifiche DLL](../profiling/how-to-limit-instrumentation-to-specific-dlls.md)   
 [Procedura: Specificare opzioni di strumentazione aggiuntive](../profiling/how-to-specify-additional-instrumentation-options.md)