---
title: "Procedura: definire e utilizzare delegati di attivit&#224; in Progettazione del flusso di lavoro | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
ms.assetid: c68e42ad-3ec0-4c2d-b104-fe36c6d83b5e
caps.latest.revision: 3
ms.author: "sdanie"
manager: "erikre"
caps.handback.revision: 3
---
# Procedura: definire e utilizzare delegati di attivit&#224; in Progettazione del flusso di lavoro
In [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)] è inclusa una nuova finestra di progettazione predefinita dell'attività di <xref:System.Activities.Statements.InvokeDelegate>.Questa finestra di progettazione può essere utilizzata per assegnare i delegati all'attività che derivano da <xref:System.Activities.ActivityDelegate>, come <xref:System.Activities.ActivityAction> o <xref:System.Activities.ActivityFunc%601>.  
  
### Definire un delegato dell'attività  
  
1.  In [!INCLUDE[vs_current_short](../code-quality/includes/vs_current_short_md.md)] selezionare **File**, **Nuovo**, **Progetto**.Selezionare il nodo **Flusso di lavoro** a sinistra e il modello **Applicazione console flusso di lavoro** a destra.Assegnare al progetto il nome \(se lo si desidera\), quindi fare clic su **OK**.  
  
2.  Fare clic con il pulsante destro del mouse in **Esplora soluzioni**, quindi selezionare **Aggiungi**, **Nuovo elemento**.Selezionare il nodo **Flusso di lavoro** a sinistra e il modello **Attività** a destra.Assegnare un nome alla nuova attività **MyForEach.xaml**, quindi fare clic su **OK**.L'attività verrà visualizzata nella Progettazione flussi di lavoro.  
  
3.  In Progettazione flussi di lavoro fare clic sulla scheda **Argomenti**.  
  
4.  Fare clic su **Crea argomento**.Assegnare al nuovo argomento il nome **Elementi**.  
  
5.  Nella colonna **Tipo di argomento** selezionare **Matrice di T \[\]**.  
  
6.  Nel browser tipi, selezionare **Oggetto**.Scegliere **Ok**.  
  
7.  Fare nuovamente clic su **Crea argomento**.Assegnare al nuovo argomento il nome **Corpo**.Nella colonna **Direzione** per il nuovo argomento, selezionare **Proprietà**.  
  
8.  Nella colonna tipo di argomento, selezionare **Cerca tipi…**  
  
9. Nel browser tipi, immettere **ActivityAction** nel campo **Nome tipo**.Selezionare **ActivityAction\<T\>** nella visualizzazione ad albero.Selezionare **Oggetto** nell'elenco a discesa che viene visualizzato per assegnare il tipo **ActivityAction\<Object\>** all'argomento.  
  
10. Trascinare un'attività <xref:System.Activities.Statements.While> dalla sezione **Flusso di controllo** della casella degli strumenti all'area di progettazione.  
  
11. Selezionare l'attività <xref:System.Activities.Statements.While> e selezionare la scheda **Variabili**.  
  
12. Selezionare **Crea variabile**.Assegnare alla nuova variabile il nome **Indice**.  
  
13. Nella colonna **Tipo variabile** selezionare **Int32**.Lasciare **Ambito** su **While** e lasciare vuota la colonna **Predefinito**.  
  
14. Impostare la proprietà **Condizione** dell'attività <xref:System.Activities.Statements.While> su **index \< Items.Length;**.  
  
15. Trascinare un'attività <xref:System.Activities.Statements.InvokeDelegate> dalla sezione **Primitive** della casella degli strumenti al **Corpo** dell'attività <xref:System.Activities.Statements.While>.  
  
16. Selezionare **Corpo** nell'elenco a discesa del delegato.  
  
17. Nella griglia **Proprietà** per l'attività <xref:System.Activities.Statements.InvokeDelegate> fare clic sul pulsante **...** all'interno della proprietà **Argomenti del delegato**.  
  
18. Nella colonna **Valore** dell'argomento denominato **Argomento**, immettere **Items\[Index\]**.Fare clic su **OK** per chiudere la finestra di dialogo **DelegateArguments**.  
  
19. Trascinare un'attività di <xref:System.Activities.Statements.Assign> sulla riga orizzontale al di sotto dell'attività di <xref:System.Activities.Statements.InvokeDelegate>.Verrà creata l'attività di <xref:System.Activities.Statements.Assign> e un'attività <xref:System.Activities.Statements.Sequence> verrà creata automaticamente per contenere le due attività nella sezione **Corpo** dell'attività **MyForEach**.La sequenza è necessaria poiché la sezione **Corpo** può contenere solo una singola attività.La creazione automatica di una nuova attività <xref:System.Activities.Statements.Sequence> è una nuova funzionalità di [!INCLUDE[net_v45](../ide/includes/net_v45_md.md)].  
  
20. Impostare la proprietà **A** dell'attività <xref:System.Activities.Statements.Assign> su **indice**.Impostare la proprietà **Valore** dell'attività **Assegna** su **Index\+1**.  
  
 L'attività personalizzata di **MyForEach** richiamerà un'attività arbitraria una volta per ogni valore passato tramite la raccolta **Items**, con i valori della raccolta come input per l'attività.  
  
### Utilizzare l'attività personalizzata in un flusso di lavoro  
  
1.  Premere **CTRL\+MAIUSC\+B** per compilare il progetto.  
  
2.  In **Esplora soluzioni** aprire **Workflow1.xaml** nella finestra di progettazione.  
  
3.  Trascinare un'attività **MyForEach** dalla casella degli strumenti all'area di progettazione.L'attività si troverà in una sezione della casella degli strumenti con lo stesso nome del progetto.  
  
4.  Impostare la proprietà **Elementi** dell'attività **MyForEach** su **new Object\[\] {1, "abc"}**.  
  
5.  Trascinare un'attività <xref:System.Activities.Statements.WriteLine> dalla sezione **Primitive** della casella degli strumenti al alla sezione **Delegate:Body** dell'attività **MyForEach**.  
  
6.  Impostare la proprietà **Testo** dell'attività <xref:System.Activities.Statements.WriteLine> su **Argument.ToString\(\)**.  
  
 Quando il flusso di lavoro viene eseguito, nella console verrà visualizzato quanto segue:  
  
 **1**   
**abc**