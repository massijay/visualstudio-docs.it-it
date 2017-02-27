---
title: "Procedura: Creare un set di regole personalizzato | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.codeanalysis.addremoverulesets"
helpviewer_keywords: 
  - "Development Edition, set di regole"
ms.assetid: bcc42508-9592-4802-9f66-a50111641d73
caps.latest.revision: 24
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 24
---
# Procedura: Creare un set di regole personalizzato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In [!INCLUDE[vsUltShort](../code-quality/includes/vsultshort_md.md)], [!INCLUDE[vsPreShort](../code-quality/includes/vspreshort_md.md)] e [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)], è possibile creare e modificare un *set di regole* personalizzate per soddisfare specifiche esigenze del progetto in relazione all'analisi del codice.  Per creare un set di regole personalizzato, aprire uno o più set di regole standard nell'Editor set di regole.  È quindi possibile aggiungere quindi o rimuovere determinate regole nonché modificare l'azione che si verifica quando l'analisi codice determina che una regola è stata violata.  
  
 Per creare un nuovo set di regole personalizzate, è necessario salvarlo con un nuovo nome file.  Il set di regole personalizzato viene assegnato automaticamente al progetto.  
  
## Apertura dell'Editor set di regole  
  
#### Per aprire un file del set di regole vuoto nell'editor del set di regole  
  
1.  Scegliere **Nuovo** dal menu **File** di [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)], quindi fare clic su **File**.  
  
2.  Nella finestra di dialogo **Nuovo file** fare clic su **Generale** nell'elenco **Modelli installati**, quindi selezionare **Set di regole di analisi codice**.  
  
3.  Verrà aperto l'editor del set di regole.  Nell'elenco dell'editor non è selezionata alcuna regola.  
  
#### Per creare una regola personalizzata da un singolo set di regole esistente  
  
1.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**.  
  
2.  Nella scheda **Proprietà** fare clic su **Analisi codice**.  
  
3.  Nell'elenco a discesa **Set di regole** eseguire una delle operazioni seguenti:  
  
    -   Selezionare il set di regole che si desidera personalizzare.  
  
     \- oppure \-  
  
    -   Selezionare **\<Sfoglia...\>** per specificare un set di regole esistente non incluso nell'elenco.  
  
4.  Fare clic su **Apri** per visualizzare le regole nell'Editor set di regole.  
  
#### Per creare un set di regole personalizzato a partire da più set di regole esistenti  
  
1.  In Esplora soluzioni fare clic con il pulsante destro del mouse sul progetto, quindi scegliere **Proprietà**.  
  
2.  Nella scheda **Proprietà** fare clic su **Analisi codice**.  
  
3.  Selezionare **\<Scegli più set di regole\>** da **Esegui il set di regole**.  
  
4.  Nella finestra di dialogo **Aggiungi o rimuovi set di regole** selezionare i set di regole su cui si desidera basare il nuovo set e quindi scegliere **OK**.  
  
5.  Salvare il nuovo set di regole.  
  
     Il nome del nuovo set di regole viene selezionato nell'elenco **Esegui il set di regole**.  Nel passaggio successivo è possibile modificare il nome visualizzato del set di regole.  
  
6.  \(Facoltativo\) Per modificare il nome visualizzato del set di regole, scegliere **Finestra Proprietà** dal menu **Visualizza**.  Digitare il nome visualizzato nella casella **Nome**.  
  
7.  Per aggiungere, rimuovere o modificare regole di analisi del codice specifiche nel nuovo set di regole, fare clic su **Apri**.  
  
## Modifica di un set di regole  
  
#### Per modificare un set di regole nell'Editor set di regole  
  
-   Per modificare il nome visualizzato del set di regole, scegliere **Finestra Proprietà** dal menu **Visualizza**.  Immettere il nome visualizzato nella casella **Nome**.  Si noti che il nome visualizzato può differire dal nome file.  
  
-   Per aggiungere tutte le regole del gruppo a un set di regole personalizzato, selezionare la casella di controllo del gruppo.  Per rimuovere tutte le regole del gruppo, deselezionare la casella di controllo.  
  
-   Per aggiungere una regola specifica al set di regole personalizzato, selezionare la casella di controllo della regola.  Per rimuovere la regola dal set di regole, deselezionare la casella di controllo.  
  
-   Per modificare l'azione eseguita in caso di violazione di una regola nell'analisi del codice, fare clic nel campo **Azione** corrispondente alla regola, quindi selezionare uno dei valori seguenti:  
  
     **Warn**: genera un avviso.  
  
     **Error**: genera un errore.  
  
     **None**: disabilita la regola.  Questa azione corrisponde alla rimozione della regola dal set di regole.  
  
## Modifica della visualizzazione dell'Editor set di regole  
  
#### Per raggruppare, filtrare o modificare i campi nell'Editor set di regole tramite la relativa barra degli strumenti  
  
-   Per espandere le regole in tutti i gruppi, fare clic su **Espandi tutto**.  
  
-   Per comprimere le regole in tutti i gruppi, fare clic su **Comprimi tutto**.  
  
-   Per modificare il campo in base al quale sono raggruppate le regole, selezionare il campo dall'elenco **Raggruppa per**.  Per visualizzare le regole separate, selezionare **\<Nessuno\>**.  
  
-   Per aggiungere o rimuovere campi nelle colonne della regola, fare clic su **Opzioni colonne**.  
  
-   Per nascondere regole che non si applicano alla soluzione corrente, selezionare **Nascondi le regole che non si applicano alla soluzione corrente**.  
  
-   Per visualizzare e nascondere regole assegnate all'azione in caso di errore, fare clic su **Mostra regole che possono generare errori di analisi codice**.  
  
-   Per visualizzare e nascondere regole assegnate all'azione in caso di avviso, fare clic su **Mostra regole che possono generare avvisi di analisi codice**.  
  
-   Per visualizzare e nascondere regole assegnate all'azione **Nessuna**, fare clic su **Mostra regole non abilitate**.  
  
-   Per aggiungere o rimuovere set di regole Microsoft predefiniti al set di regole corrente, fare clic su **Aggiungi o rimuovi set di regole figlio**.  
  
## Vedere anche  
 [Procedura: Configurare l'analisi codice per un progetto di codice gestito](../code-quality/how-to-configure-code-analysis-for-a-managed-code-project.md)   
 [Tabella di riferimento del set di regole di analisi del codice](../code-quality/code-analysis-rule-set-reference.md)