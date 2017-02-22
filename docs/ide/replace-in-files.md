---
title: "Sostituisci nei file | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.findreplace.replaceinfiles"
  - "vs.replaceinfiles"
helpviewer_keywords: 
  - "ricerche di testo, sostituzione testo"
  - "Finestra Trova e sostituisci, scheda Sostituisci nei file"
  - "Scheda Sostituisci nei file, finestra Trova e sostituisci"
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 29
caps.handback.revision: 29
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Sostituisci nei file
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **Sostituisci nei file** consente di ricercare una stringa o un'espressione nel codice di una determinata serie di file e di modificare alcune o tutte le corrispondenze trovate.  Le corrispondenze trovate e le azioni eseguite vengono elencate nella finestra **Risultati ricerca** selezionata in **Opzioni risultati**.  
  
> [!NOTE]
>  È possibile che le finestre di dialogo e i comandi di menu visualizzati siano diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma.  Per modificare le impostazioni, scegliere Importa\/Esporta impostazioni dal menu Strumenti.  Per ulteriori informazioni, vedere [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/it-it/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 È possibile utilizzare uno dei seguenti metodi per visualizzare l'opzione **Sostituisci nei file** nella finestra **Trova e sostituisci**.  
  
### Per visualizzare l'opzione Sostituisci nei file  
  
1.  Espandere **Trova e sostituisci** dal menu **Modifica**.  
  
2.  Scegliere **Sostituisci nei file**.  
  
     —oppure—  
  
     Se il  **Trova e Sostituisci** finestra è già aperta, sulla barra degli strumenti, scegliere  **Sostituisci nei file**.  
  
## Trova  
 Per cercare una nuova stringa di testo o un'espressione, è necessario specificarlo nella casella.  Per cercare una delle 20 stringhe cercato in più di recente, aprire l'elenco e scegliere la stringa da cercare.  Scegliere casella adiacente  **Generatore di espressioni** pulsante se si desidera utilizzare uno o più espressioni regolari nella stringa di ricerca.  Per ulteriori informazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## Sostituisci con  
 Per sostituire istanze della stringa nel  **Trova** casella con un'altra stringa, immettere la stringa sostitutiva nel  **Sostituisci con** casella.  Per eliminare istanze della stringa nel  **Trova** casella, lasciare vuoto questo campo.  Aprire l'elenco per visualizzare le 20 stringhe trovata più di recente.  Scegliere casella adiacente  **Generatore di espressioni** pulsante se si desidera utilizzare uno o più espressioni regolari nella stringa di sostituzione.  Per ulteriori informazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## Cerca in  
 A seconda dell'opzione scelta dall'elenco a discesa **Cerca in**, **Sostituisci nei file** consentirà di eseguire ricerche solo nei file attivi o in tutti i file archiviati in determinate cartelle.  Selezionare un ambito di ricerca dall'elenco, digitare un percorso o fare clic sui  **Sfoglia \(...\)** pulsante per visualizzare il  **Seleziona cartelle di ricerca** finestra di dialogo e scegliere un set di cartelle per la ricerca.  È anche possibile digitare un percorso direttamente nella casella **Cerca in**.  
  
> [!NOTE]
>  Se l'opzione selezionata in **Cerca in** include un file che è stato estratto dal controllo del codice sorgente, la ricerca verrà eseguita solo nella versione del file scaricata nel computer locale.  
  
## Opzioni di ricerca  
 È possibile espandere o comprimere la sezione **Opzioni di ricerca**.  Le seguenti opzioni possono essere selezionate o deselezionate:  
  
 Maiuscole\/minuscole  
 Quando questa opzione è selezionata, nelle finestre **Risultati ricerca** verranno visualizzate solo le istanze della stringa specificata in **Trova** corrispondenti per contenuto e combinazione di maiuscole\/minuscole.  Ad esempio, se si ricerca la stringa "MyObject" selezionando l'opzione **Maiuscole\/minuscole**, verrà restituito "MyObject" ma non "myobject" o "MYOBJECT".  
  
 Parola intera  
 Quando questa opzione è selezionata, nelle finestre **Risultati ricerca** verranno visualizzate solo le istanze della stringa specificata in **Trova** con l'esatta corrispondenza di parole.  Ad esempio, se si ricerca la stringa "MyObject", verrà restituito "MyObject" ma non "CMyObject" o "MyObjectC".  
  
 Utilizzare le espressioni regolari  
 Quando questa casella di controllo è selezionata, è possibile utilizzare le notazioni speciali per definire modelli di testo nel  **Trova** o  **sostituire con** le caselle di testo.  Per un elenco di queste notazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Cerca i seguenti tipi di file  
 Questo elenco indica i tipi di file delle directory specificate in **Cerca in** in cui eseguire la ricerca.  Se questo campo è vuoto, la ricerca verrà eseguita in tutti i file delle directory specificate in **Cerca in**.  
  
 Selezionare una voce dall'elenco per immettere una stringa di ricerca preconfigurata che consentirà di ricercare file dei tipi indicati.  
  
## Opzioni risultati  
 È possibile espandere o comprimere la sezione **Opzioni risultati**.  Le seguenti opzioni possono essere selezionate o deselezionate:  
  
 Finestra Risultati ricerca 1  
 Quando questa opzione è selezionata, i risultati della ricerca corrente sostituiranno il contenuto della finestra **Risultati ricerca 1**.  Questa finestra viene aperta automaticamente per visualizzare i risultati della ricerca.  Per aprire la finestra manualmente, scegliere **Altre finestre** dal menu **Visualizza** e selezionare **Risultati ricerca 1**.  
  
 Finestra Risultati ricerca 2  
 Quando questa opzione è selezionata, i risultati della ricerca corrente sostituiranno il contenuto della finestra **Risultati ricerca 2**.  Questa finestra viene aperta automaticamente per visualizzare i risultati della ricerca.  Per aprire la finestra manualmente, scegliere **Altre finestre** dal menu **Visualizza** e selezionare **Risultati ricerca 2**.  
  
 Mostra solo nomi file  
 Quando questa casella di controllo è selezionata, nelle finestre Risultati ricerca elencare i percorsi per tutti i file che contengono la stringa di ricerca e i nomi completi.  Tuttavia, i risultati non includono la riga di codice in cui viene visualizzata la stringa.  Questa casella di controllo è solo disponibile per la ricerca nei file.  
  
 Non chiudere i file modificati con Sostituisci tutto  
 Quando questa opzione è selezionata, tutti i file in cui sono state eseguite delle sostituzioni restano aperti, in modo da poter annullare o salvare le modifiche.  I vincoli di memoria potrebbero limitare il numero di file che possono rimanere aperti dopo un'operazione di sostituzione.  
  
> [!CAUTION]
>  È possibile utilizzare **Annulla** solo sui file che restano aperti per la modifica.  Se questa opzione non è selezionata, i file che non erano già aperti per la modifica resteranno chiusi e su di essi non sarà possibile eseguire alcuna operazione **Annulla**.  
  
## Vedere anche  
 [Ricerca e sostituzione di testo](../ide/finding-and-replacing-text.md)   
 [Cerca nei file](../ide/find-in-files.md)   
 [Comandi di Visual Studio](../ide/reference/visual-studio-commands.md)