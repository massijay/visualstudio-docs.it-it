---
title: "Utilizzo di set di regole per specificare le regole C++ da eseguire | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ac3877e6-5349-4c03-9541-3d5be259f1e8
caps.latest.revision: 5
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Utilizzo di set di regole per specificare le regole C++ da eseguire
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] e [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)] è possibile creare e modificare un *set di regole* personalizzate per soddisfare specifiche esigenze del progetto in relazione all'analisi del codice.  Per creare un set di regole personalizzate C\+\+, il progetto C\/C\+\+ deve essere aperto nell'IDE di Visual Studio.  Aprire poi un set di regole standard nell' Editor set di regole e quindi si aggiungere o rimuove le regole specifiche e facoltativamente modificare l'azione che si verifica quando l'analisi codice determina che una regola è stata violata.  
  
 Per creare un nuovo set di regole personalizzate, è necessario salvarlo con un nuovo nome file.  Il set di regole personalizzato viene assegnato automaticamente al progetto.  
  
## Apertura dell'Editor set di regole  
  
#### Per creare una regola personalizzata da un singolo set di regole esistente  
  
1.  In Esplora soluzioni aprire il menu di scelta rapida per il progetto e scegliere **Proprietà**.  
  
2.  Nella scheda **Proprietà** scegliere **Analisi codice**.  
  
3.  Nell'elenco a discesa **Set di regole** eseguire una delle operazioni seguenti:  
  
    -   Selezionare il set di regole che si desidera personalizzare.  
  
     \-oppure\-  
  
    -   Selezionare **\<Sfoglia...\>** per specificare un set di regole esistente non incluso nell'elenco.  
  
4.  Fare clic su **Apri** per visualizzare le regole nell'Editor set di regole.  
  
#### Per modificare un set di regole nell'Editor set di regole  
  
-   Per modificare il nome visualizzato del set di regole, dal menu **Visualizza**, scegliere **Finestra Proprietà**.  Immettere il nome visualizzato nella casella **Nome**.  Si noti che il nome visualizzato può differire dal nome file.  
  
-   Per aggiungere tutte le regole del gruppo a un set di regole personalizzato, selezionare la casella di controllo del gruppo.  Per rimuovere tutte le regole del gruppo, deselezionare la casella di controllo.  
  
-   Per aggiungere una regola specifica al set di regole personalizzato, selezionare la casella di controllo della regola.  Per rimuovere la regola dal set di regole, deselezionare la casella di controllo.  
  
-   Per modificare l'azione eseguita in caso di violazione di una regola nell'analisi del codice, fare clic nel campo **Azione** corrispondente alla regola, quindi selezionare uno dei valori seguenti:  
  
     **Warn**: genera un avviso.  
  
     **Error**: genera un errore.  
  
     **None**: disabilita la regola.  Questa azione corrisponde alla rimozione della regola dal set di regole.  
  
#### Per raggruppare, filtrare o modificare i campi nell'Editor set di regole tramite la relativa barra degli strumenti  
  
-   Per espandere le regole in tutti i gruppi, scegliere **Espandi tutto**.  
  
-   Per comprimere le regole in tutti i gruppi, scegliere **Comprimi tutto**.  
  
-   Per modificare il campo in base al quale sono raggruppate le regole, selezionare il campo dall'elenco **Raggruppa per**.  Per visualizzare le regole separate, selezionare **\<Nessuno\>**.  
  
-   Per aggiungere o rimuovere campi nelle colonne della regola, scegliere **Opzioni colonne**.  
  
-   Per nascondere regole che non si applicano alla soluzione corrente, scegliere **Nascondi le regole che non si applicano alla soluzione corrente**.  
  
-   Per visualizzare e nascondere regole assegnate all'azione in caso di errore, fare clic su **Mostra regole che possono generare errori di analisi codice**.  
  
-   Per visualizzare e nascondere regole assegnate all'azione in caso di avviso, fare clic su **Mostra regole che possono generare avvisi di analisi codice**.  
  
-   Per visualizzare e nascondere regole assegnate all'azione **Nessuna**, fare clic su **Mostra regole non abilitate**.  
  
-   Per aggiungere o rimuovere set di regole Microsoft predefiniti al set di regole corrente, fare clic su **Aggiungi o rimuovi set di regole figlio**.