---
title: 'Procedura dettagliata: Analisi del codice C/C++ per i difetti | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- C/C++, code analysis
- code analysis, walkthroughs
- code, analyzing C/C++
- code analysis tool, walkthroughs
ms.assetid: eaee55b8-85fe-47c7-a489-9be0c46ae8af
caps.latest.revision: "35"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: f3c3be4f5a2cebda5b7fd0f705eefc0077b36f29
ms.sourcegitcommit: fb751e41929f031d1a9247bc7c8727312539ad35
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/15/2017
---
# <a name="walkthrough-analyzing-cc-code-for-defects"></a>Procedura guidata: analisi del codice C/C++ per l'identificazione degli errori
Questa procedura dettagliata viene illustrato come analizzare il codice C/C++ per potenziali difetti del codice utilizzando lo strumento di analisi codice per il codice C/C++.  
  
 In questa procedura dettagliata, si esamina il processo di analisi del codice di utilizzo per analizzare il codice C/C++ per potenziali difetti del codice.  
  
 Si completeranno le seguenti operazioni:  
  
-   Eseguire l'analisi del codice nel codice nativo.  
  
-   Analizzare gli avvisi degli errori di codice.  
  
-   Considera avviso come errore.  
  
-   Annotare il codice sorgente per migliorare l'analisi degli errori del codice.  
  
## <a name="prerequisites"></a>Prerequisiti  
  
-   [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)] o [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)].  
  
-   Una copia del [esempio dimostrativo](../code-quality/demo-sample.md).  
  
-   Nozioni di base di C/C++.  
  
### <a name="to-run-code-defect-analysis-on-native-code"></a>Per eseguire l'analisi degli errori del codice nel codice nativo  
  
1.  Aprire la soluzione Demo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
     La soluzione Demo popola ora **Esplora**.  
  
2.  Nel **compilare** menu, fare clic su **Ricompila soluzione**.  
  
     La soluzione venga compilata senza errori o avvisi.  
  
3.  In **Esplora**, selezionare il progetto CodeDefects.  
  
4.  Scegliere **Proprietà** dal menu **Progetto**.  
  
     Il **pagine delle proprietà CodeDefects** viene visualizzata la finestra di dialogo.  
  
5.  Fare clic su **l'analisi del codice**.  
  
6.  Fare clic su di **Attiva analisi codice per C/C++ in fase di compilazione** casella di controllo.  
  
7.  Ricompilare il progetto CodeDefects.  
  
     Avvisi dell'analisi del codice vengono visualizzati di **elenco errori**.  
  
### <a name="to-analyze-code-defect-warnings"></a>Per analizzare gli avvisi degli errori di codice  
  
1.  Nel **vista** menu, fare clic su **elenco errori**.  
  
     In base al profilo di sviluppo scelto nel [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], potrebbe essere necessario scegliere **altre finestre** sul **vista** menu e quindi fare clic su **elenco errori**.  
  
2.  Nel **elenco errori**, fare doppio clic sull'avviso seguente:  
  
     avviso C6230: cast implicito tra tipi integer semanticamente diversi: utilizzo di HRESULT in un contesto booleano.  
  
     L'editor di codice viene visualizzata la riga che ha provocato l'avviso nella funzione `bool``ProcessDomain()`. Questo avviso indica che un valore HRESULT è in uso in un'istruzione 'if' è previsto un risultato booleano.  
  
3.  Risolvere il problema utilizzando la macro SUCCEEDED. Il codice sarà simile al codice seguente:  
  
    ```  
    if (SUCCEEDED (ReadUserAccount()) )  
    ```  
  
4.  Nel **elenco errori**, fare doppio clic sull'avviso seguente:  
  
     avviso C6282: operatore errato: assegnazione di costante in contesto di test. È stato = = previsto?  
  
5.  Risolvere il problema eseguendo il test di uguaglianza. Il codice dovrebbe essere simile al codice seguente:  
  
    ```  
    if ((len == ACCOUNT_DOMAIN_LEN) || (g_userAccount[len] != '\\'))  
    ```  
  
### <a name="to-treat-warning-as-an-error"></a>Per considerare l'avviso come errore  
  
1.  Nel file bug, aggiungere le seguenti `#pragma` istruzione all'inizio del file da considerare l'avviso C6001 come un errore:  
  
    ```  
    #pragma warning (error: 6001)  
    ```  
  
2.  Ricompilare il progetto CodeDefects.  
  
     Nel **elenco errori**, C6001 viene visualizzato come un errore.  
  
3.  Correggere i due errori C6001 nel **elenco errori** inizializzando `i` e `j` su 0.  
  
4.  Ricompilare il progetto CodeDefects.  
  
     Il progetto venga compilato senza errori o avvisi.  
  
### <a name="to-correct-the-source-code-annotation-warnings-in-annotationc"></a>Per correggere gli avvisi di annotazione di codice sorgente nella Annotation  
  
1.  In Esplora soluzioni selezionare il progetto di annotazioni.  
  
2.  Scegliere **Proprietà** dal menu **Progetto**.  
  
     Il **pagine delle proprietà di annotazioni** viene visualizzata la finestra di dialogo.  
  
3.  Fare clic su **l'analisi del codice**.  
  
4.  Selezionare il **Attiva analisi codice per C/C++ in fase di compilazione** casella di controllo.  
  
5.  Ricompilare il progetto di annotazioni.  
  
6.  Nel **elenco errori**, fare doppio clic sull'avviso seguente:  
  
     avviso C6011: dereferenziazione del puntatore NULL 'newNode'.  
  
     Questo avviso indica un errore dal chiamante per controllare il valore restituito. In questo caso, una chiamata a **AllocateNode** potrebbe restituire un valore NULL (vedere il file di intestazione Annotations. h per la dichiarazione di funzione per AllocateNode).  
  
7.  Aprire il file Annotations.  
  
8.  Per risolvere il problema, utilizzare un'istruzione 'if' per verificare il valore restituito. Il codice sarà simile al codice seguente:  
  
     `if (NULL != newNode)`  
  
     `{`  
  
     `newNode->data = value;`  
  
     `newNode->next = 0;`  
  
     `node->next = newNode;`  
  
     `}`  
  
9. Ricompilare il progetto di annotazioni.  
  
     Il progetto venga compilato senza errori o avvisi.  
  
### <a name="to-use-source-code-annotation"></a>Per utilizzare l'annotazione del codice sorgente  
  
1.  Annotare i parametri formali e il valore della funzione restituito `AddTail` utilizzando le condizioni di Pre e Post, come illustrato in questo esempio:  
  
     `[returnvalue:SA_Post (Null=SA_Maybe)] LinkedList* AddTail`  
  
     `(`  
  
     `[SA_Pre(Null=SA_Maybe)] LinkedList* node,`  
  
     `int value`  
  
     `)`  
  
2.  Ricompilare il progetto di annotazioni.  
  
3.  Nel **elenco errori**, fare doppio clic sull'avviso seguente:  
  
     avviso C6011: dereferenziazione del puntatore NULL "nodo".  
  
     Questo avviso indica che il nodo passato alla funzione potrebbe essere null e indica il numero di riga in cui è stato generato l'avviso.  
  
4.  Per risolvere il problema, utilizzare un'istruzione 'if' per verificare il valore restituito. Il codice sarà simile al codice seguente:  
  
    ```  
    . . .  
    LinkedList *newNode = NULL;   
    if (NULL == node)  
    {  
         return NULL;  
        . . .  
    }  
    ```  
  
5.  Ricompilare il progetto di annotazioni.  
  
     Il progetto venga compilato senza errori o avvisi.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: analisi del codice gestito per l'identificazione di errori del codice](../code-quality/walkthrough-analyzing-managed-code-for-code-defects.md)