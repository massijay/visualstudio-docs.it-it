---
title: "Procedura: aggiungere la convalida a classi di entit&#224; | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 61107da9-7fa3-4dba-b101-ae46536f52c4
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: aggiungere la convalida a classi di entit&#224;
La *convalida* delle classi di entità rappresenta il processo mediante cui si conferma che i valori immessi negli oggetti dati sono conformi ai vincoli presenti nello schema di un oggetto e alle regole stabilite per l'applicazione.Per ridurre gli errori, è opportuno convalidare i dati prima di inviare aggiornamenti al database sottostante.La convalida consente anche di ridurre il numero potenziale di round trip tra un'applicazione e il database.  
  
 In [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md) sono disponibili metodi parziali che consentono agli utenti di estendere il codice generato nella finestra di progettazione, che viene eseguito durante i comandi di inserimento, aggiornamento ed eliminazione di entità complete nonché durante e dopo le modifiche di singole colonne.  
  
> [!NOTE]
>  In questo argomento vengono forniti i passaggi di base per aggiungere la convalida a classi di entità utilizzando [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].Poiché potrebbe essere difficile seguire questi passaggi generici senza fare riferimento a una specifica classe di entità, è stata fornita una procedura dettagliata in cui vengono utilizzati dati effettivi.Per istruzioni dettagliate per la configurazione della convalida mediante [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], vedere [Procedura dettagliata: aggiunta della convalida a classi di entità](../Topic/Walkthrough:%20Adding%20Validation%20to%20Entity%20Classes.md).  
  
## Aggiunta della convalida per le modifiche al valore di una specifica colonna  
 In questa procedura viene mostrato come convalidare i dati quando viene modificato il valore in una colonna.Poiché la convalida viene eseguita nella definizione di classe anziché nell'interfaccia utente, se il valore causa l'esito negativo della convalida, viene generata un'eccezione.Implementare la gestione degli errori per il codice nell'applicazione che tenta di modificare i valori della colonna.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
#### Per convalidare i dati durante la modifica del valore di una colonna  
  
1.  Aprire o creare un nuovo file di classi LINQ to SQL \(file **.dbml**\) in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\(fare doppio clic sul file **.dbml** in **Esplora soluzioni**\).  
  
2.  In Progettazione relazionale oggetti fare clic con il pulsante destro del mouse sulla classe per cui si desidera aggiungere la convalida, quindi scegliere **Visualizza codice**.  
  
     Viene aperto l'editor del codice con una classe parziale per la classe di entità selezionata.  
  
3.  Posizionare il cursore nella classe parziale.  
  
4.  Per i progetti di Visual Basic:  
  
    1.  Espandere l'elenco **Nome metodo**.  
  
    2.  Individuare il metodo **On***COLUMNNAME***Changing** per la colonna a cui si desidera aggiungere la convalida.  
  
    3.  Viene aggiunto un metodo `On`*COLUMNNAME*`Changing` alla classe parziale.  
  
    4.  Aggiungere il codice riportato di seguito per verificare innanzitutto che sia stato immesso un valore e quindi per assicurarsi che il valore immesso per la colonna sia accettabile per l'applicazione.Poiché l'argomento `value` contiene il valore proposto, aggiungere logica per confermare che si tratta di un valore valido:  
  
        ```vb#  
        If value.HasValue Then  
            ' Add code to ensure that the value is acceptable.  
            ' If value < 1 Then  
            '    Throw New Exception("Invalid data!")  
            ' End If  
        End If  
        ```  
  
     Per i progetti C\#:  
  
    1.  Poiché i progetti C\# non generano automaticamente i gestori eventi, è possibile utilizzare IntelliSense per creare i metodi parziali di modifica delle colonne.  
  
         Digitare `partial` e uno spazio per accedere all'elenco dei metodi parziali disponibili.Fare clic sul metodo di modifica delle colonne relativo alla colonna per cui si desidera aggiungere la convalida.Il codice riportato di seguito è simile al codice generato quando si seleziona un metodo parziale di modifica delle colonne:  
  
        ```c#  
        partial void OnCOLUMNNAMEChanging(COLUMNDATATYPE value)  
            {  
               throw new System.NotImplementedException();  
            }  
  
        ```  
  
## Aggiunta della convalida per gli aggiornamenti a una classe di entità  
 Oltre a controllare i valori durante le modifiche, è anche possibile convalidare i dati quando si tenta di aggiornare una classe di entità completa.La convalida durante un tentativo di aggiornamento consente di confrontare i valori di più colonne, se richiesto dalle regole business.Nella procedura riportata di seguito viene mostrato come eseguire la convalida quando si tenta di aggiornare una classe di entità completa.  
  
> [!NOTE]
>  Il codice di convalida per gli aggiornamenti alle classi di entità complete viene eseguito nella classe <xref:System.Data.Linq.DataContext> parziale, anziché nella classe parziale di una classe di entità specifica.  
  
#### Per convalidare i dati durante un aggiornamento a una classe di entità  
  
1.  Aprire o creare un nuovo file di classi LINQ to SQL \(file **.dbml**\) in [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\(fare doppio clic sul file **.dbml** in **Esplora soluzioni**\).  
  
2.  Fare clic con il pulsante destro del mouse su un'area vuota in Progettazione relazionale oggetti, quindi scegliere **Visualizza codice**.  
  
     Viene aperto l'editor del codice con una classe parziale per `DataContext`.  
  
3.  Posizionare il cursore nella classe parziale per `DataContext`.  
  
4.  Per i progetti di Visual Basic:  
  
    1.  Espandere l'elenco **Nome metodo**.  
  
    2.  Fare clic su **Aggiorna***ENTITYCLASSNAME*.  
  
    3.  Viene aggiunto un metodo `Update`*ENTITYCLASSNAME* alla classe parziale.  
  
    4.  Accedere ai valori delle singole colonne utilizzando l'argomento `instance`, come mostrato nel codice seguente:  
  
        ```vb#  
        If (instance.COLUMNNAME = x) And (instance.COLUMNNAME = y) Then  
            Dim ErrorMessage As String = "Invalid data!"  
            Throw New Exception(ErrorMessage)  
        End If  
        ```  
  
     Per i progetti C\#:  
  
    1.  Poiché i progetti C\# non generano automaticamente i gestori eventi, è possibile utilizzare IntelliSense per creare il metodo `Update`*CLASSNAME* parziale.  
  
    2.  Digitare `partial` e uno spazio per accedere all'elenco dei metodi parziali disponibili.Fare clic sul metodo di aggiornamento relativo alla classe per cui si desidera aggiungere la convalida.Il codice riportato di seguito è simile al codice generato quando si seleziona un metodo parziale `Update`*CLASSNAME*:  
  
        ```c#  
        partial void UpdateCLASSNAME(CLASSNAME instance)  
        {  
            if ((instance.COLUMNNAME == x) && (instance.COLUMNNAME = y))  
            {  
                string ErrorMessage = "Invalid data!";  
                throw new System.Exception(ErrorMessage);  
            }  
        }  
        ```  
  
## Vedere anche  
 [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)