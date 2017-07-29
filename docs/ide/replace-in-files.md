---
title: Sostituisci nei file | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- Find and Replace window, Replace in Files tab
- Replace in Files tab, Find and Replace window
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 29
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: 79206d09446dcd76654c3c24976fab3fe65e4f83
ms.contentlocale: it-it
ms.lasthandoff: 05/24/2017

---
# <a name="replace-in-files"></a>Sostituisci nei file
**Sostituisci nei file** consente di cercare una stringa o un'espressione nel codice di un determinato set di file e di modificare alcune o tutte le corrispondenze trovate. Le corrispondenze trovate e le azioni eseguite sono elencate nella finestra **Risultati ricerca** selezionata in **Opzioni risultati**.  
  
> [!NOTE]
>  Le finestre di dialogo e i comandi di menu visualizzati potrebbero essere diversi da quelli descritti nella Guida a seconda delle impostazioni attive o dell'edizione del programma. Per modificare le impostazioni, scegliere Importa/esporta impostazioni dal menu Strumenti. Per altre informazioni, vedere [Personalizzare l'IDE di Visual Studio](../ide/personalizing-the-visual-studio-ide.md).  
  
 È possibile usare uno dei metodi seguenti per visualizzare l'opzione **Sostituisci nei file** nella finestra **Trova e sostituisci**.  
  
### <a name="to-display-replace-in-files"></a>Per visualizzare l'opzione Sostituisci nei file  
  
1.  Nel menu **Modifica** espandere **Trova e sostituisci**.  
  
2.  Scegliere **Sostituisci nei file**.  
  
     oppure  
  
     Se la finestra **Trova e sostituisci** è già visualizzata, scegliere **Sostituisci nei file** nella barra degli strumenti.  
  
## <a name="find-what"></a>Trova  
 Per cercare una nuova stringa di testo o espressione, specificarla nella casella. Per cercare una delle 20 stringhe cercate più di recente, aprire l'elenco e scegliere la stringa che si vuole cercare. Scegliere il pulsante **Generatore di espressioni** adiacente se si vuole usare una o più espressioni regolari nella stringa di ricerca. Per altre informazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## <a name="replace-with"></a>Sostituisci con  
 Per sostituire istanze della stringa nella casella **Trova** con un'altra stringa, immettere la stringa di sostituzione nella casella **Sostituisci con**. Per eliminare le istanze della stringa nella casella **Trova**, lasciare vuoto questo campo. Aprire l'elenco per visualizzare le ultime 20 stringhe cercate. Scegliere il pulsante **Generatore di espressioni** adiacente se si vuole usare una o più espressioni regolari nella stringa di sostituzione. Per altre informazioni, vedere [Utilizzo delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## <a name="look-in"></a>Cerca in  
 L'opzione selezionata nell'elenco a discesa **Cerca in** determina se la funzionalità **Sostituisci nei file** deve cercare solo nei file attualmente attivi o in tutti i file archiviati all'interno di determinate cartelle. Selezionare un ambito di ricerca dall'elenco, digitare il percorso di una cartella o fare clic sul pulsante **Sfoglia (...)** per visualizzare la finestra di dialogo **Seleziona cartelle di ricerca** e immettere il set di cartelle per la ricerca. È anche possibile digitare un percorso direttamente nella casella **Cerca in**.  
  
> [!NOTE]
>  Se l'opzione **Cerca in** selezionata fa sì che venga cercato un file estratto dal controllo del codice sorgente, la ricerca verrà eseguita solo nella versione del file scaricata nel computer locale.  
  
## <a name="find-options"></a>Opzioni ricerca  
 È possibile espandere o comprimere la sezione **Opzioni di ricerca**. È possibile selezionare o deselezionare le opzioni seguenti:  
  
 Maiuscole/minuscole  
 Quando questa opzione è selezionata, le finestre **Risultati ricerca** visualizzano solo le istanze della stringa specificata in **Trova** corrispondenti per contenuto e combinazione di maiuscole/minuscole. Ad esempio, la ricerca di "MyObject" con l'opzione **Maiuscole/minuscole** selezionata restituisce "MyObject" ma non "myobject" o "MYOBJECT".  
  
 Parola intera  
 Quando questa opzione è selezionata, le finestre **Risultati ricerca** visualizzano solo le istanze della stringa specificata in **Trova** con l'esatta corrispondenza di parole. Ad esempio, la ricerca di "MyObject" restituisce "MyObject" ma non "CMyObject" o "MyObjectC".  
  
 Utilizza espressioni regolari  
 Se questa casella di controllo è selezionata, è possibile usare le notazioni speciali per definire modelli di testo nelle caselle di testo **Trova** o **Sostituisci con**. Per un elenco di queste notazioni, vedere [Uso delle espressioni regolari in Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Cerca i seguenti tipi di file  
 L'elenco indica i tipi di file da cercare nelle directory **Cerca in**. Se questo campo è vuoto, la ricerca verrà eseguita in tutti i file nelle directory **Cerca in**.  
  
 Selezionare qualsiasi voce dell'elenco per immettere una stringa di ricerca preconfigurata che troverà i file dei tipi specificati.  
  
## <a name="result-options"></a>Opzioni risultati  
 È possibile espandere o comprimere la sezione **Opzioni risultati**. È possibile selezionare o deselezionare le opzioni seguenti:  
  
 Finestra Risultati ricerca 1  
 Quando questa opzione è selezionata, i risultati della ricerca corrente sostituiranno il contenuto della finestra **Risultati ricerca 1**. Questa finestra viene visualizzata automaticamente per mostrare i risultati della ricerca. Per aprire questa finestra manualmente, scegliere **Altre finestre** dal menu **Visualizza** e quindi **Risultati ricerca 1**.  
  
 Finestra Risultati ricerca 2  
 Quando questa opzione è selezionata, i risultati della ricerca corrente sostituiranno il contenuto della finestra **Risultati ricerca 2**. Questa finestra viene visualizzata automaticamente per mostrare i risultati della ricerca. Per aprire questa finestra manualmente, scegliere **Altre finestre** dal menu **Visualizza** e quindi **Risultati ricerca 2**.  
  
 Mostra solo nomi file  
 Quando questa casella di controllo è selezionata, le finestre Risultati ricerca visualizzano i nomi completi e i percorsi di tutti i file che contengono la stringa di ricerca. Tuttavia, i risultati non includono la riga di codice in cui viene visualizzata la stringa. Questa casella di controllo è disponibile solo per la ricerca nei file.  
  
 Non chiudere i file modificati con Sostituisci tutto  
 Quando questa opzione è selezionata, tutti i file in cui sono state eseguite delle sostituzioni restano aperti in modo da poter annullare o salvare le modifiche. I vincoli di memoria potrebbero limitare il numero di file che possono rimanere aperti dopo un'operazione di sostituzione.  
  
> [!CAUTION]
>  È possibile usare **Annulla** solo nei file che restano aperti per la modifica. Se questa opzione non è selezionata, i file che non sono già aperti per la modifica restano chiusi e l'opzione **Annulla** non è disponibile per i file.  
  
## <a name="see-also"></a>Vedere anche  
 [Ricerca e sostituzione di testo](../ide/finding-and-replacing-text.md)   
 [Cerca nei file](../ide/find-in-files.md)   
 [Comandi di Visual Studio](../ide/reference/visual-studio-commands.md)
