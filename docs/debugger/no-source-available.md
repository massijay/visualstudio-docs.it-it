---
title: "Nessuna origine disponibile | Microsoft Docs"
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
  - "vs.debug.nosource"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "Codice sorgente non disponibile per il percorso corrente (finestra di dialogo)"
ms.assetid: ed0732bc-4b8c-490f-adb1-af06869a2a6b
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Nessuna origine disponibile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il progetto non contiene codice sorgente per il codice che si tenta di visualizzare.  Questa condizione si verifica, di solito, quando si fa doppio clic su un modulo per il quale non è disponibile codice sorgente nella finestra **Stack di chiamate** o **Thread**.  È possibile continuare il debug, ma non è possibile utilizzare la finestra di origine per impostare i punti di interruzione ed eseguire altre operazioni in questa posizione.  Per impostare un punto di interruzione, utilizzare invece la finestra **Disassembly**.  
  
 Nelle pagine delle proprietà della soluzione è possibile modificare le directory in cui il debugger cerca i file di origine e indicare al debugger di ignorare determinati file di origine.  Vedere [Esegui debug dei file di origine, Proprietà comuni, finestra di dialogo Pagine delle proprietà di soluzione](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md).  
  
 **Sfoglia per trovare il codice sorgente**  
 Fare clic su questo collegamento per aprire una finestra di dialogo in cui è possibile cercare il codice sorgente.  
  
 **Mostra disassembly**  
 Apre la finestra **Disassembly**.  
  
 **Mostra sempre disassembly per i file del codice sorgente mancanti**  
 Selezionare questa opzione per visualizzare automaticamente la finestra **Disassembly** quando non è disponibile alcuna origine.  È anche possibile modificare questa impostazione nella finestra di dialogo **Opzioni**, categoria **Debug**, pagina **Generale**, selezionando o deselezionando **Mostra disassembly se l'origine non è disponibile**.  
  
## Vedere anche  
 [Esegui debug dei file di origine, Proprietà comuni, finestra di dialogo Pagine delle proprietà di soluzione](../debugger/debug-source-files-common-properties-solution-property-pages-dialog-box.md)   
 [Specifica di file di simboli \(con estensione pdb\) e di origine](../debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger.md)   
 [SOS.dll \(SOS Debugging Extension\)](../Topic/SOS.dll%20\(SOS%20Debugging%20Extension\).md)