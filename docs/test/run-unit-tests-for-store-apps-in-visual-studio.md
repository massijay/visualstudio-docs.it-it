---
title: Eseguire unit test per le app dello Store in Visual Studio | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a6f5b32-bfce-4a63-81e9-02d54c592539
caps.latest.revision: 12
ms.author: douge
manager: douge
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
translationtype: Human Translation
ms.sourcegitcommit: 5ab78b6b8eaa8156ed2c8a807b1d8a80e75afa84
ms.openlocfilehash: ab3b6e63d78148553c449032913b2e04a054ecf3
ms.lasthandoff: 04/04/2017

---
# <a name="run-unit-tests-for-store-apps-in-visual-studio"></a>Eseguire unit test per le app dello Store in Visual Studio
Questo argomento descrive come eseguire unit test tramite Esplora test in Microsoft Visual Studio  
  
> [!NOTE]
>  Gli argomenti di questa sezione descrivono la funzionalità di Visual Studio Express per Windows 8. Visual Studio Community, Enterprise e Professional offrono funzionalità aggiuntive per gli unit test.  
>   
>  -   È possibile usare un framework di unit test open source o di terze parti che abbia creato un adattatore di componente aggiuntivo per Esplora test Microsoft. È anche possibile analizzare e visualizzare le informazioni di code coverage per i test.  
> -   Eseguire i test dopo ogni compilazione. È anche possibile usare Microsoft Fakes, un framework di isolamento per il codice gestito che consente di concentrare i test sul codice sostituendo il codice di test per le funzionalità di sistema e di terze parti.  
>   
>  Per altre informazioni, vedere [Eseguire unit test del codice](../test/unit-test-your-code.md) in MSDN Library.  
  
##  <a name="BKMK_In_this_topic"></a> Contenuto dell'argomento  
 [Framework di unit test e progetti di test](#BKMK_Unit_test_frameworks_and_test_projects)  
  
 [Esecuzione di test in Esplora test](#BKMK_Running_tests_in_Test_Explorer)  
  
-   [Esecuzione di test](#BKMK_Running_tests)  
  
 [Visualizzazione dei risultati dei test](#BKMK_Viewing_test_results)  
  
-   [Visualizzazione dei dettagli dei test](#BKMK_Viewing_test_details)  
  
-   [Visualizzazione del codice sorgente di un metodo di test](#BKMK_Viewing_the_source_code_of_a_test_method)  
  
 [Organizzazione dell'elenco dei test](#BKMK_Organizing_the_test_list)  
  
-   [Raggruppamento dei test](#BKMK_Grouping_tests)  
  
-   [Ricerca e filtro nell'elenco dei test](#BKMK_Searching_and_filtering_the_test_list)  
  
 [Debug di unit test](#BKMK_Debugging_unit_tests)  
  
##  <a name="BKMK_Unit_test_frameworks_and_test_projects"></a> Framework di unit test e progetti di test  
 Visual Studio Express per app di Windows Store include i framework di testing unità Microsoft per il codice C++ gestito e nativo. Esplora test può eseguire test da più progetti di test in una soluzione e da classi di test appartenenti a progetti di codice di produzione. I progetti di test possono essere costituiti da una combinazione qualsiasi di framework di unit test in Visual C++ o Visual C# e Visual Basic. Quando il codice sottoposto a test è scritto per .NET Framework, il progetto di test può essere scritto in qualsiasi linguaggio .NET Framework, indipendentemente dal linguaggio del codice di destinazione. I progetti in codice C/C++ nativo devono essere testati tramite un framework di unit test C++.  
  
##  <a name="BKMK_Running_tests_in_Test_Explorer"></a> Esecuzione di test in Esplora test  
 Quando si compila il progetto di test, i test vengono visualizzati in Esplora test. Se Esplora test non è visualizzato, scegliere **Test** dal menu di Visual Studio, quindi scegliere **Windows**e infine **Esplora test**.  
  
 ![Esplora unit test](~/ide/media/ute_failedpassednotrunsummary.png "UTE_FailedPassedNotRunSummary")  
  
 Quando si eseguono, si scrivono e si rieseguono i test, Esplora test mostra i risultati nei gruppi predefiniti **Test non superati**, **Test superati**, **Test ignorati** e **Test non eseguiti**. È possibile modificare la modalità con cui Esplora test raggruppa i test.  
  
 È possibile eseguire molte delle operazioni di ricerca, organizzazione ed esecuzione dei test dalla barra degli strumenti di Esplora test.  
  
 ![Eseguire test dalla barra degli strumenti di Esplora test](../test/media/ute_toolbar.png "UTE_ToolBar")  
  
###  <a name="BKMK_Running_tests"></a> Esecuzione di test  
 È possibile eseguire tutti i test nella soluzione, tutti i test in un gruppo o un set di test selezionati. Eseguire una delle operazioni seguenti:  
  
-   Per eseguire tutti i test in una soluzione, scegliere **Esegui tutto**.  
  
-   Per eseguire tutti i test in un gruppo predefinito, scegliere **Esegui...** e quindi scegliere il gruppo dal menu.  
  
-   Selezionare i singoli test da eseguire, aprire il menu di scelta rapida per un test selezionato e quindi scegliere **Esegui test selezionati**.  
  
 Mentre il test viene eseguito, la barra Superato/Non superato nella parte superiore della finestra Esplora test mostra un'animazione. Al termine dell'esecuzione del test, la barra Superato/Non superato diventa verde se tutti i test sono stati superati o rossa se un test non è stato superato.  
  
##  <a name="BKMK_Viewing_test_results"></a> Visualizzazione dei risultati dei test  
 Quando si eseguono, si scrivono e si rieseguono i test, Esplora test mostra i risultati nei gruppi **Test non superati**, **Test superati**, **Test ignorati** e **Test non eseguiti**. Il riquadro dei dettagli nella parte inferiore della finestra Esplora Test mostra un riepilogo dell'esecuzione dei test.  
  
###  <a name="BKMK_Viewing_test_details"></a> Visualizzazione dei dettagli dei test  
 Per visualizzare i dettagli di un singolo test, selezionare il test.  
  
 Il riquadro dei dettagli del test mostra le informazioni seguenti:  
  
-   Nome del file di origine e numero di riga del metodo di test.  
  
-   Stato del test.  
  
-   Tempo impiegato per l'esecuzione del metodo di test.  
  
 Se il test non viene superato, il riquadro dei dettagli mostra anche le informazioni seguenti:  
  
-   Messaggio restituito dal framework di unit test per il test.  
  
-   Analisi dello stack al momento del mancato superamento del test.  
  
###  <a name="BKMK_Viewing_the_source_code_of_a_test_method"></a> Visualizzazione del codice sorgente di un metodo di test  
 Per visualizzare il codice sorgente per un metodo di test nell'editor di Visual Studio, selezionare il test e quindi scegliere **Apri test** dal menu di scelta rapida (tastiera: F12).  
  
##  <a name="BKMK_Organizing_the_test_list"></a> Organizzazione dell'elenco dei test  
  
###  <a name="BKMK_Grouping_tests"></a> Raggruppamento dei test  
 Per impostazione predefinita, Esplora test mostra i test come nodi figlio di **Test non superati**, **Test superati**, **Test ignorati** e **Test non eseguiti**.  
  
|||  
|-|-|  
|![Pulsante di raggruppamento di Team Explorer](~/test/media/ute_groupby_btn.png "UTE_GroupBy_btn")|Per raggruppare i test in base al tempo impiegato per l'esecuzione, aprire l'elenco **Raggruppa** e scegliere **Durata**. Scegliere **Risultato test** per passare al raggruppamento originale.|  
  
###  <a name="BKMK_Searching_and_filtering_the_test_list"></a> Ricerca e filtro nell'elenco dei test  
 Quando è presente un numero elevato di test, è possibile digitare nella casella di ricerca di Esplora test per filtrare l'elenco in base alla stringa specificata. È possibile limitare il filtro a tipi specifici di stringhe scegliendo dall'elenco di filtri prima di immettere la stringa di ricerca.  
  
 ![Categorie di filtri di ricerca](../test/media/ute_searchfilter.png "UTE_SearchFilter")  
  
##  <a name="BKMK_Debugging_unit_tests"></a> Debug di unit test  
 È possibile usare Esplora test per avviare una sessione di debug per i test. Esaminando con facilità il codice grazie al debugger di Visual Studio è possibile spostarsi in avanti e indietro tra gli unit test e i progetti da testare. Per avviare il debug:  
  
1.  Nell'editor di Visual Studio impostare un punto di interruzione in uno o più metodi di test di cui si vuole eseguire il debug.  
  
    > [!NOTE]
    >  Poiché i metodi di test possono essere eseguiti in qualsiasi ordine, impostare punti di interruzione in tutti i metodi di test di cui si vuole eseguire il debug.  
  
2.  In Esplora test selezionare i metodi di test e quindi scegliere **Esegui debug test selezionati** dal menu di scelta rapida.  
  
 Per altre informazioni sul debugger, vedere [Debugging in Visual Studio](../debugger/debugging-in-visual-studio.md).

