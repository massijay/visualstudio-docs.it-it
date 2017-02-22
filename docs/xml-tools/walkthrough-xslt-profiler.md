---
title: "Procedura dettagliata: XSLT Profiler | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 87387c9a-2e89-4801-ad51-83740cd6ea25
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura dettagliata: XSLT Profiler
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il Profiler XSLT crea rapporti di prestazioni XSLT dettagliati utili per misurare, valutare e trattare problemi correlati alle prestazioni nel codice XSLT.Il Profiler XSLT include suggerimenti utili per le ottimizzazioni dei fogli di stile XSL e XSLT.Per applicazioni XSLT che richiedono massime prestazioni, questo strumento potrebbe essere essenziale.  
  
## Prerequisiti  
 Le operazioni descritte nella seguente procedura dettagliata richiedono Visual Studio 2010 e .NET Framework versione 4.Il Profiler XSLT è disponibile solo con Microsoft Visual Studio Team System con gli strumenti di analisi installati.  
  
### Creare il rapporto di prestazioni  
  
1.  Aprire un documento XSLT in Visual Studio.  
  
2.  Fare clic sull'opzione **Profila XSLT** disponibile nel menu XML.  
  
3.  Fornire un documento XML di input.Se non è già aperto un documento XML, verrà richiesto il file.  
  
4.  L'analisi viene avviata e un indicatore di stato visualizza lo stato di avanzamento all'interno dell'editor.  
  
5.  L'output XSLT è visibile nel riquadro di output.  
  
6.  Al termine di una sessione di prestazioni, controllare il rapporto di prestazioni.I dati salvati in un rapporto di prestazioni consentono di visualizzare e analizzare le prestazioni di XSLT.  
  
### Ottenere tutte le visualizzazioni disponibili  
  
1.  Fare clic sull'elenco a discesa **Visualizzazione corrente** per ottenere tutte le visualizzazioni disponibili.  
  
2.  Selezionare l'opzione di visualizzazione **Riepilogo** nell'elenco a discesa **Visualizzazione corrente**.Per impostazione predefinita, un rapporto di prestazioni viene visualizzato nella visualizzazione **Riepilogo**.Questa visualizzazione costituisce un punto iniziale per determinare problemi di prestazioni con i documenti XSLT.Nella visualizzazione **Riepilogo** vengono elencati i seguenti punti dati:  
  
    -   Funzioni più chiamate  
  
    -   Funzioni con più lavoro individuale  
  
    -   Funzioni la cui esecuzione richiede più tempo  
  
3.  Per impostazione predefinita, esistono tre colonne per ogni punto dati: il nome della funzione, il numero di chiamate in valore assoluto e un valore percentuale della funzione denominata per sommare le chiamate di funzione.Da ogni punto dati della visualizzazione **Riepilogo** è possibile andare a visualizzazioni più dettagliate facendo clic con il pulsante destro del mouse sui punti dati della funzione.  
  
4.  Selezionare l'opzione di visualizzazione **Funzione** nell'elenco a discesa **Visualizzazione corrente**.Nella visualizzazione **Funzione** vengono presentate le funzioni chiamate durante la profilatura.Per ordinare i dati è possibile fare clic sul nome di una colonna.Le colonne visualizzate per impostazione predefinita sono:  
  
    -   **Nome funzione**  
  
    -   **Tempo inclusivo trascorso**  
  
    -   **Tempo esclusivo trascorso**  
  
    -   **Tempo inclusivo applicazione**  
  
    -   **Tempo esclusivo applicazione**  
  
    -   **Numero di chiamate**  
  
5.  Tutte le colonne dell'ora vengono visualizzate sia in valori assoluti che in percentuali.Il termine **esclusivo** si riferisce al tempo totale impiegato da una funzione per l'esecuzione, escluso il tempo impiegato da altre funzioni chiamate durante l'esecuzione di questa funzione.  
  
6.  Il termine **inclusivo** si riferisce al tempo totale impiegato da una funzione per l'esecuzione, incluso il tempo di esecuzione di tutte le funzioni chiamate e se una di queste funzioni chiamate ha chiamato altre funzioni.  
  
### Selezionare la visualizzazione Chiamante\/chiamato  
  
1.  Selezionare la visualizzazione **Chiamante\/chiamato** nell'elenco a discesa **Visualizzazione corrente**.  
  
2.  La visualizzazione **Chiamante\/chiamato** è costituita da tre parti distinte:  
  
    -   **Funzioni che hanno chiamato**: tutte le funzioni che hanno chiamato una particolare funzione vengono elencate nella parte superiore della visualizzazione.  
  
    -   **Funzione corrente**: la funzione chiamata viene riportata nella parte centrale della visualizzazione.  
  
    -   **Funzioni che sono state chiamate da**: tutte le funzioni chiamate dalla particolare funzione vengono elencate nella parte inferiore della visualizzazione.  
  
3.  Se una funzione denominata `SyncToNavigator` viene riportata nella parte centrale della visualizzazione, tutte le funzioni che hanno chiamato la funzione `SyncToNavigator` vengono visualizzate nella parte superiore della visualizzazione e tutte le funzioni che sono state chiamate da `SyncToNavigator` vengono elencate nella parte inferiore della visualizzazione.  
  
4.  È possibile modificare la funzione nella parte centrale della visualizzazione facendo doppio clic su una delle funzioni elencate nelle altre due parti della visualizzazione.La visualizzazione verrà quindi automaticamente aggiornata in base alle modifiche.  
  
5.  Per ordinare i dati, è anche possibile fare clic sui nomi delle colonne.  
  
### Selezionare la visualizzazione struttura ad albero delle chiamate  
  
1.  Selezionare la visualizzazione **Struttura ad albero delle chiamate** nell'elenco a discesa **Visualizzazione corrente**.Questa visualizzazione è una struttura ad albero dell'esecuzione del programma.  
  
2.  Nella visualizzazione **Struttura ad albero delle chiamate** viene mostrata la radice della struttura ad albero come nome del processo.Le funzioni sono i nodi della struttura ad albero.Questa visualizzazione consente di esaminare determinate tracce di chiamata e di analizzare quali tracce hanno il maggiore impatto sulle prestazioni.La visualizzazione è simile alla visualizzazione **Stack di chiamate** disponibile durante l'esecuzione del debug.Oltre alle colonne in visualizzazione **Funzione**, nella visualizzazione **Struttura ad albero delle chiamate** viene riportata una colonna aggiuntiva che visualizza il **Nome modulo**.  
  
3.  Selezionare **Contrassegni** nell'elenco a discesa **Visualizzazione corrente**.  
  
4.  Con il Profiler SLT, vengono visualizzati contrassegni nel flusso di raccolta dati con un commento associato.I contrassegni sono parti del codice che dispongono di contatori.Indicando al Profiler XSLT di raccogliere contatori delle prestazioni XSLT, i contatori vengono raccolti ogni volta che viene eseguito uno di questi contrassegni.I dati vengono visualizzati in una tabella che contiene **ID contrassegno**, **Nome contrassegno** \(**Avvia programma**, **Termina programma**\) e **Time Stamp**.I contrassegni non sono aggregati e non vengono visualizzati in ordine cronologico nella visualizzazione **Contrassegni** del rapporto delle prestazioni.  
  
### Selezionare i moduli nella visualizzazione corrente  
  
1.  Selezionare **Moduli** nell'elenco a discesa **Visualizzazione corrente**.  
  
2.  La visualizzazione dei moduli è un elenco completo di tutte le funzioni aggregate a livello di modulo.Espandere o comprimere il nome del modulo per visualizzare o chiudere la visualizzazione dei dati relativi alle prestazioni del modulo.Per ordinare i dati è possibile fare clic sul nome di una colonna.Per impostazione predefinita, esistono sia valori assoluti che numeri in percentuale per **Tempo inclusivo trascorso**, **Tempo esclusivo trascorso**, **Tempo inclusivo applicazione**, **Tempo esclusivo applicazione** e **Numero di chiamate**.  
  
3.  Selezionare **Processo** nell'elenco a discesa **Visualizzazione corrente**.  
  
4.  Nella visualizzazione dei processi viene mostrata una tabella che include **ID processo**, **Nome processo**, **Ora di inizio** e **Ora di fine**.Per ordinare i dati, è possibile fare clic sui nomi delle colonne.  
  
## Vedere anche  
 [Procedura dettagliata: utilizzo della gerarchia XSLT](../xml-tools/walkthrough-using-xslt-hierarchy.md)