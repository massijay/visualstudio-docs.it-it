---
title: "Cerca nei file | Microsoft Docs"
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
  - "vs.findreplace.findinfiles"
  - "vs.findinfiles"
helpviewer_keywords: 
  - "oggetti [Visual Studio], ricerca"
  - "ricerche di testo, sostituzione testo"
  - "oggetti [Visual Studio], ricerca"
  - "Finestra Trova e sostituisci, scheda Cerca nei file"
  - "ricerche di testo, finestra Trova e sostituisci"
  - "documenti, ricerca"
  - "file, ricerca"
  - "Scheda Cerca nei file, finestra Trova e sostituisci"
ms.assetid: 989e0737-46d7-4474-8453-fad52a74669d
caps.latest.revision: 41
caps.handback.revision: 41
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Cerca nei file
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

**Cerca nei file** permette di cercare un set specificato di file.  Le corrispondenze trovate e le azioni adottate sono elencate nella finestra **Risultati ricerca** selezionata in **Opzioni risultati**.  
  
 È possibile usare uno qualsiasi dei metodi seguenti per visualizzare **Cerca nei file** nella finestra **Trova e sostituisci**.  
  
### Per visualizzare Cerca nei file  
  
1.  Sulla barra dei menu fare clic su **Modifica** e quindi su **Trova e sostituisci**.  
  
2.  Scegliere **Cerca nei file**.  
  
 Per annullare un'operazione di ricerca, premere CTRL\+INTERR.  
  
> [!NOTE]
>  Lo strumento Trova e sostituisci non esegue la ricerca nelle directory per cui è impostato l'attributo `Hidden` o `System`.  
  
## Trova  
 Per cercare una nuova stringa di testo o espressione, specificarla nella casella.  Per cercare una delle 20 stringhe cercate più di recente, aprire l'elenco e scegliere la stringa che si vuole cercare.  Scegliere il pulsante **Generatore di espressioni** adiacente se si vuole usare una o più espressioni regolari nella stringa di ricerca.  Per altre informazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## Cerca in  
 L'opzione selezionata nell'elenco a discesa **Cerca in** determina se la funzionalità **Cerca nei file** deve cercare solo nei file attualmente attivi o in tutti i file archiviati all'interno di determinate cartelle.  Selezionare un ambito di ricerca nell'elenco o fare clic sul pulsante **Sfoglia \(...\)** per visualizzare la finestra di dialogo **Seleziona cartelle di ricerca** e immettere il set di directory desiderato.  È anche possibile digitare un percorso direttamente nella casella **Cerca in**.  
  
> [!WARNING]
>  Con le opzioni **Intera soluzione** o **Progetto corrente**, i file di progetto e di soluzione non vengono cercati.  Se si vuole cercare in file di progetto, scegliere una cartella di ricerca.  
  
> [!NOTE]
>  Se l'opzione selezionata in **Cerca in** fa sì che venga cercato un file estratto dal controllo del codice sorgente, verrà cercata solo la versione di questo file scaricata nel computer locale.  
  
## Includi sottocartelle  
 Specifica che la ricerca verrà eseguita nelle sottocartelle della cartella **Cerca in**.  
  
## Opzioni ricerca  
 È possibile espandere o comprimere la sezione **Trova opzioni**.  È possibile selezionare o deselezionare le opzioni seguenti:  
  
 Maiuscole\/minuscole  
 Se questa opzione è selezionata, una ricerca impostata su **Risultati ricerca** farà distinzione tra maiuscole e minuscole.  
  
 Parola intera  
 Se questa opzione è selezionata, la finestra **Risultati ricerca** restituirà solo corrispondenze di parole intere.  
  
 Utilizza espressioni regolari  
 Se questa casella di controllo è selezionata, è possibile usare notazioni speciali per definire modelli di testo che devono corrispondere nella casella di testo **Trova** o **Sostituisci con**.  Per un elenco di queste notazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Cerca i seguenti tipi di file  
 L'elenco indica i tipi di file da cercare nelle directory **Cerca in**.  Se questo campo è vuoto, verranno cercati tutti i file nelle directory **Cerca in**.  
  
 Selezionare qualsiasi voce dell'elenco per immettere una stringa di ricerca preconfigurata che troverà i file dei tipi specificati.  
  
## Opzioni risultati  
 È possibile espandere o comprimere la sezione **Opzioni risultati**.  È possibile selezionare o deselezionare le opzioni seguenti:  
  
 Finestra Risultati ricerca 1  
 Quando questa opzione è selezionata, i risultati della ricerca corrente sostituiranno il contenuto della finestra **Risultati ricerca 1**.  Questa finestra viene visualizzata automaticamente per mostrare i risultati della ricerca.  Per aprire la finestra manualmente, scegliere **Altre finestre** dal menu **Visualizza** e quindi **Risultati ricerca 1**.  
  
 Finestra Risultati ricerca 2  
 Quando questa opzione è selezionata, i risultati della ricerca corrente sostituiranno il contenuto della finestra **Risultati ricerca 2**.  Questa finestra viene visualizzata automaticamente per mostrare i risultati della ricerca.  Per aprire questa finestra manualmente, scegliere **Altre finestre** dal menu **Visualizza** e quindi **Risultati ricerca 2**.  
  
 Mostra solo nomi file  
 Mostra un elenco di file che contengono le corrispondenze invece di visualizzare le corrispondenze stesse.  
  
 Accoda risultati  
 Aggiunge i risultati della ricerca a quelli della ricerca precedente.  
  
## Vedere anche  
 [Ricerca e sostituzione di testo](../ide/finding-and-replacing-text.md)   
 [Sostituisci nei file](../ide/replace-in-files.md)   
 [Comandi di Visual Studio](../ide/reference/visual-studio-commands.md)