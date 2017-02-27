---
title: "Ricerca e sostituzione di testo | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.find"
  - "vs.findreplacecontrol"
  - "vs.findreplace.findsymbol"
  - "vs.findreplace.symbol"
  - "findresultswindow"
  - "vs.findreplace.quickreplace"
  - "vs.findsymbol"
  - "vs.findinfiles"
  - "vs.findresults1"
  - "vs,findsymbolwindow"
  - "vs.findreplace.quickfind"
  - "vs.lookin"
  - "vs.replace"
helpviewer_keywords: 
  - "find"
  - "trova e sostituisci"
  - "Cerca nei file (finestra di dialogo)"
  - "trova testo"
  - "find, simbolo"
  - "find, testo"
  - "replace"
  - "Sostituisci (finestra di dialogo)"
  - "Sostituisci nei file (finestra di dialogo)"
  - "sostituzione di testo"
  - "ricerche di testo"
  - "ricerche di testo, ricerca e sostituzione di testo"
  - "testo, ricerca e sostituzione"
ms.assetid: a62545c3-1570-4d12-99fb-a82607eb35a1
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# Ricerca e sostituzione di testo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile cercare e sostituire testo nell'editor del codice di Visual Studio e determinate finestre di output basate su testo come le finestre **Risultati ricerca**, utilizzando il controllo **Trova e sostituisci** o **Trova\/Sostituisci nei file**.  È inoltre possibile trovare e sostituire in alcune finestre di progettazione, ad esempio la finestra di progettazione XAML e di Windows Form e le finestre degli strumenti  
  
 È possibile definire l'ambito di ricerca al documento corrente, alla soluzione corrente o a un set di cartelle personalizzato.  È inoltre possibile specificare un set di estensioni di file per ricerche a più file.  È possibile personalizzare la sintassi di ricerca tramite espressioni regolari di .NET.  
  
 Per trovare e sostituire le espressioni regolari, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)  
  
> [!TIP]
>  La casella **Trova\/Comando** è ancora disponibile come controllo toolbar, ma non è più visibile per impostazione predefinita.  È possibile visualizzare la casella **Trova\/Comando** scegliendo **Aggiungi o rimuovi pulsanti** sulla barra degli strumenti **Standard** e scegliendo **Trova**.  Per ulteriori informazioni, vedere [Casella Trova\/Comando](../ide/find-command-box.md).  
  
## Trovare e sostituire il controllo  
 Il controllo **Trova e sostituisci** visualizzato nell'angolo superiore destro della finestra dell'editor di codice.  Il controllo **Trova e sostituisci** evidenzia immediatamente tutte le occorrenze della stringa specificata nel documento corrente.  È possibile spostarsi da un'occorrenza a un'altra scegliendo il pulsante **Trova successivo** o il pulsante **Trova precedente** nel controllo di ricerca.  
  
 È possibile accedere alle opzioni di sostituzione scegliendo il pulsante accanto alla casella di testo **Trova**.  Per eseguire una sostituzione per volta, scegliere il pulsante **Sostituisci successivo** accanto alla casella di testo **Sostituisci**.  Per sostituire tutte le corrispondenze, scegliere il pulsante **Sostituisci tutto**.  
  
 Per modificare il colore di evidenziazione per le corrispondenze, scegliere il menu **Strumenti**, selezionare **Opzioni**, quindi scegliere **Ambiente** e selezionare **Tipi di carattere e colori**.  Nell'elenco **Mostra impostazioni per** selezionare **Editor di testo**, quindi nell'elenco **Elementi visualizzati** selezionare **Trova evidenziato \(estensione\)**.  
  
### Finestre dello strumento di ricerca.  
 È possibile utilizzare il controllo **Trova** nelle finestre del codice o del testo, quali le finestre **Output** e le finestre **Risultati ricerca**, scegliendo **Trova e sostituisci** dal menu **Modifica** o \(CTRL\+F\).  
  
 Una versione del controllo di ricerca è disponibile anche in alcune finestre degli strumenti.  Ad esempio, è ora possibile filtrare l'elenco di controlli nella finestra **Casella degli strumenti** immettendo il testo nella casella di ricerca.  Tra le altre finestre degli strumenti che ora consentono di cercare il relativo contenuto sono incluse **Esplora soluzioni**, **Proprietà** e **Team Explorer**.  
  
## Individua\/Sostituisci nei file  
 **Trova\/Sostituisci nei file** funziona come il controllo **Trova e sostituisci**, ma è possibile definire un ambito per la ricerca.  Non solo è possibile cercare il file aperto corrente nell'editor, ma anche tutti i documenti aperti, l'intera soluzione, il progetto corrente e gli insiemi di cartelle selezionati.  È inoltre possibile cercare per estensione del file.  Per accedere alla finestra di dialogo **Trova\/Sostituisci nei file**, scegliere **Trova e sostituisci** dal menu **Modifica** \(o CTRL\+MAIUSC\+F\).  
  
 Quando si sceglie **Trova tutti**, una finestra **Risultati ricerca** viene aperta ed elenca le corrispondenze della ricerca.  Selezionando un risultato nell'elenco viene visualizzato il file associato ed evidenziata la corrispondenza.  Se il file non è già aperto per la modifica, viene aperto in una scheda di anteprima a destra della finestra scheda.  È possibile utilizzare il controllo **Trova** per cercare nell'elenco **Risultati ricerca**.  
  
### Creazione di set personalizzati di cartelle di ricerca  
 È possibile definire un ambito di ricerca scegliendo il pulsante **Seleziona cartelle di ricerca** \(simile a **…**\) accanto alla casella **Cerca in**.  Nella finestra di dialogo **Seleziona cartelle di ricerca** è possibile specificare un set di cartelle in cui cercare ed è possibile salvare la specifica in modo da poterla riutilizzare successivamente.  È possibile specificare le cartelle in un computer remoto solo se è stato eseguito il mapping della relativa unità nel computer locale.  
  
### Creazione di set di componenti personalizzati  
 È possibile definire set di componenti nell'ambito di ricerca scegliendo il pulsante **Modifica insieme di componenti personalizzato** accanto alla casella **Cerca in**.  È possibile specificare i componenti .NET o COM installati, i progetti Visual Studio che sono inclusi nella soluzione, o qualsiasi assembly o libreria dei tipi \(.dll, .tlb, .olb, .exe o .ocx\).  Per individuare i riferimenti, selezionare la casella **Cerca in riferimenti**.  
  
## Vedere anche  
 [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md)