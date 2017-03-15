---
title: "Procedura guidata: analisi del codice C/C++ per l&#39;identificazione degli errori | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "C/C++, analisi codice"
  - "strumento di analisi del codice, procedure dettagliate"
  - "analisi codice, procedure dettagliate"
  - "codice, analisi di codice C/C++"
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: 35
caps.handback.revision: 35
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Procedura guidata: analisi del codice C/C++ per l&#39;identificazione degli errori
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questa procedura dettagliata viene illustrato come analizzare il codice C\/C\+\+ per identificare errori potenziali del codice attraverso lo strumento di analisi del codice C\/C\+\+.  
  
 Verrà spiegato in modo dettagliato come utilizzare l'analisi del codice per esaminare il codice C\/C\+\+ con l'obiettivo di identificare errori potenziali.  
  
 Verranno completati i seguenti passaggi:  
  
-   Eseguire l'analisi del codice su codice nativo.  
  
-   Analizzare gli avvisi degli errori del codice.  
  
-   Considerare l'avviso come un errore.  
  
-   Annotare il codice sorgente per migliorare l'analisi degli errori del codice.  
  
## Prerequisiti  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] o [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)].  
  
-   Una copia di [Esempio dimostrativo](../code-quality/demo-sample.md).  
  
-   Concetti di base di C\/C\+\+.  
  
### Per eseguire l'analisi degli errori del codice su codice nativo  
  
1.  Aprire la soluzione Demo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     A questo punto la soluzione Demo verrà inserita in **Esplora soluzioni**.  
  
2.  Scegliere **Ricompila soluzione** dal menu **Compila**.  
  
     La soluzione verrà compilata senza alcun errore o avviso.  
  
3.  In **Esplora soluzioni** selezionare il progetto CodeDefects.  
  
4.  Scegliere **Proprietà** dal menu **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Pagine delle proprietà CodeDefects**.  
  
5.  Fare clic su **Analisi codice**.  
  
6.  Selezionare la casella di controllo **Abilita analisi del codice per C\/C\+\+ in fase di compilazione**.  
  
7.  Ricompilare il progetto CodeDefects.  
  
     Nell'**Elenco errori** vengono visualizzati gli avvisi dell'analisi del codice.  
  
### Per analizzare gli avvisi di errori del codice  
  
1.  Scegliere **Elenco errori** dal menu **Visualizza**.  
  
     In base al profilo dello sviluppatore scelto in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], potrebbe essere necessario scegliere **Altre finestre** dal menu **Visualizza**, quindi fare clic su **Elenco errori**.  
  
2.  Nella finestra **Elenco errori** fare doppio clic sul seguente avviso:  
  
     avviso C6230: Cast implicito tra tipi integer semanticamente diversi: utilizzo di HRESULT in un contesto Booleano.  
  
     Nell'editor di codice viene visualizzata la riga che ha causato la generazione dell'avviso nella funzione `bool` `ProcessDomain()`.  Questo avviso indica l'utilizzo di HRESULT in un'istruzione 'if' dove è previsto un risultato Booleano.  
  
3.  Risolvere il problema utilizzando la macro SUCCEEDED.  L'aspetto del codice dovrebbe essere simile al seguente:  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4.  Nella finestra **Elenco errori** fare doppio clic sul seguente avviso:  
  
     avviso C6282: Operatore errato: assegnazione di costante in contesto Booleano.  Si consiglia di utilizzare '\=\='  
  
5.  Risolvere il problema eseguendo un test dell'uguaglianza.  Il codice dovrebbe risultare simile al seguente:  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### Per considerare l'avviso come un errore  
  
1.  Nel file Bug.cpp aggiungere la seguente istruzione `#pragma` all'inizio del file per considerare l'avviso C6001 come un errore:  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2.  Ricompilare il progetto CodeDefects.  
  
     Nella finestra **Elenco errori** C6001 appare ora come un errore.  
  
3.  Correggere i due errori C6001 residui nella finestra **Elenco errori** inizializzando `i` e `j` su 0.  
  
4.  Ricompilare il progetto CodeDefects.  
  
     Il progetto verrà compilato senza alcun avviso o errore.  
  
### Per correggere gli avvisi di annotazione del codice sorgente in annotation.c  
  
1.  Selezionare il progetto Annotations in Esplora soluzioni.  
  
2.  Scegliere **Proprietà** dal menu **Progetto**.  
  
     Verrà visualizzata la finestra di dialogo **Pagine delle proprietà Annotations**.  
  
3.  Fare clic su **Analisi codice**.  
  
4.  Selezionare la casella di controllo **Abilita analisi del codice per C\/C\+\+ in fase di compilazione**.  
  
5.  Ricompilare il progetto Annotations.  
  
6.  Nella finestra **Elenco errori** fare doppio clic sul seguente avviso:  
  
     avviso C6011: Dereferenziazione del puntatore NULL 'newNode'.  
  
     Questo avviso indica che il chiamante non è riuscito a controllare il valore restituito.  In questo caso, una chiamata a **AllocateNode** potrebbe restituire un valore NULL \(vedere il file di intestazione annotations.h per la dichiarazione di funzione relativa ad AllocateNode\).  
  
7.  Aprire il file annotations.cpp.  
  
8.  Per risolvere il problema, utilizzare un'istruzione 'if' per verificare il valore restituito.  L'aspetto del codice dovrebbe essere simile al seguente:  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. Ricompilare il progetto Annotations.  
  
     Il progetto verrà compilato senza alcun avviso o errore.  
  
### Per utilizzare l'annotazione del codice sorgente  
  
1.  Annotare i parametri formali e il valore restituito della funzione `AddTail` utilizzando le condizioni Pre e Post, come illustrato nell'esempio seguente:  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2.  Ricompilare il progetto Annotations.  
  
3.  Nella finestra **Elenco errori** fare doppio clic sul seguente avviso:  
  
     avviso C6011: Dereferenziazione del puntatore NULL 'node'.  
  
     Questo avviso indica che il nodo passato alla funzione potrebbe essere null e indica il numero di riga dove è stato generato l'avviso.  
  
4.  Per risolvere il problema, utilizzare un'istruzione 'if' per verificare il valore restituito.  L'aspetto del codice dovrebbe essere simile al seguente:  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5.  Ricompilare il progetto Annotations.  
  
     Il progetto verrà compilato senza alcun avviso o errore.  
  
## Vedere anche  
 [Procedura dettagliata: Analisi del codice gestito per l'identificazione di errori del codice](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)