---
title: "Procedura dettagliata: creazione di un elenco esterno in SharePoint tramite il servizio di integrazione applicativa dei dati"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], dati business in una Web part"
  - "integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], elenco esterno"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], dati business in un elenco SharePoint"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], dati business in un elenco SharePoint"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], dati business in una Web part"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], elenco supportato da entità"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], elenco supportato da entità"
  - "servizio di integrazione applicativa dei dati [sviluppo per SharePoint in Visual Studio], elenco esterno"
ms.assetid: 046cf234-705a-4a6f-91f8-c5c569ae0dd0
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Procedura dettagliata: creazione di un elenco esterno in SharePoint tramite il servizio di integrazione applicativa dei dati
  Il servizio di integrazione applicativa dei dati consente a SharePoint di visualizzare dati business da applicazioni server back\-end, servizi Web e database.  
  
 In questa procedura dettagliata viene illustrato come creare un modello per il servizio di integrazione applicativa dei dati che restituisce informazioni sui contatti in un database di esempio.  Verrà quindi creato un elenco esterno in SharePoint tramite questo modello.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   Creazione di un progetto.  
  
-   Aggiunta di un'entità al modello.  
  
-   Aggiunta di un metodo Finder.  
  
-   Aggiunta di un metodo Finder specifico.  
  
-   Test del progetto.  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Windows e SharePoint.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vsPro](../sharepoint/includes/vspro-md.md)], [!INCLUDE[vsUltLong](../sharepoint/includes/vsultlong-md.md)] o [!INCLUDE[vsPreLong](../sharepoint/includes/vsprelong-md.md)].  
  
-   Accesso al database di esempio AdventureWorks.  Per ulteriori informazioni su come installare i database AdventureWorks, vedere [Database di esempio di SQL Server](http://go.microsoft.com/fwlink/?LinkID=117483).  
  
## Creazione di un progetto contenente un modello BDC  
  
#### Per creare un progetto contenente un modello BDC  
  
1.  Sulla barra dei menu di Visual Studio, scegliere **File**, **Nuovo**, **Project**.  
  
     Verrà visualizzata la finestra di dialogo **Nuovo progetto**.  
  
2.  Sotto **Visual C\#** o **Visual Basic**, espandere il nodo **SharePoint**, quindi scegliere l'elemento **2010**.  
  
3.  Nel riquadro **Modelli**, scegliere la voce **Progetto SharePoint 2010**, denominare il progetto AdventureWorksTest e quindi fare clic sul pulsante **OK**.  
  
     Viene visualizzata la **Personalizzazione guidata SharePoint**.  In questa procedura guidata, è possibile specificare il sito che verrà utilizzato per eseguire il debug del progetto e impostare il livello di attendibilità della soluzione.  
  
4.  Scegliere il pulsante di opzione **Distribuisci come soluzione farm** per impostare il livello di attendibilità.  
  
5.  Selezionare il pulsante **Fine** per accettare il sito SharePoint locale predefinito.  
  
6.  Scegliere il nodo di progetto SharePoint in **Esplora soluzioni**.  
  
7.  Sulla barra dei menu scegliere **Progetto**,  **Aggiungi nuovo elemento**.  
  
     Viene aperta la finestra di dialogo **Aggiungi nuovo elemento**.  
  
8.  Nel riquadro **Modelli**, scegliere **Modello di integrazione applicativa dei dati \(solo soluzioni farm\)**, denominare il progetto AdventureWorksContacts quindi scegliere il pulsante **Aggiungi**.  
  
## Aggiunta al progetto di classi di accesso ai dati  
  
#### Per aggiungere al progetto classi di accesso ai dati  
  
1.  Nella barra dei menu, scegliere **Strumenti**, **Connetti al Database**.  
  
     Verrà visualizzata la finestra di dialogo **Aggiungi connessione**.  
  
2.  Aggiungere una connessione al database di esempio AdventureWorks di SQL Server.  
  
     Per ulteriori informazioni, vedere [Add\/Modify Connection \(Microsoft SQL Server\)](http://msdn.microsoft.com/it-it/fa400910-26c3-4df7-b9d1-115e688b4ea3).  
  
3.  Scegliere il nodo di progetto in **Esplora soluzioni**.  
  
4.  Sulla barra dei menu scegliere **Progetto**,  **Aggiungi nuovo elemento**.  
  
5.  Nel riquadro **Modelli installati** selezionare il nodo **Dati**.  
  
6.  Nel riquadro **Modelli** selezionare **Classi LINQ to SQL**.  
  
7.  Nella casella **Nome**, specificare AdventureWorks, quindi scegliere il pulsante **Aggiungi**.  
  
     Verrà aggiunto al progetto un file con estensione dbml e verrà aperto Progettazione relazionale oggetti.  
  
8.  Nella barra dei menu, scegliere **Visualizza** dal menu **Esplora server**.  
  
9. In **Esplora server** espandere il nodo che rappresenta il database di esempio AdventureWorks, quindi espandere il nodo **Tables**.  
  
10. Aggiungere la tabella **Contact \(Person\)** in Progettazione relazionale oggetti.  
  
     Viene creata una classe di entità, che verrà visualizzata nell'area di progettazione.  La classe di entità include proprietà che eseguono il mapping alle colonne nella tabella Contact \(Person\).  
  
## Rimozione dell'entità predefinita dal modello di integrazione applicativa dei dati  
 Il progetto **Modello di integrazione applicativa dei dati** aggiunge al modello un'entità predefinita denominata Entity1.  Rimuovere questa entità.  In un secondo momento, si aggiungerà una nuova entità.  L'avvio con un modello vuoto riduce il numero di passaggi richiesto per completare la procedura dettagliata.  
  
#### Per rimuovere l'entità predefinita dal modello  
  
1.  In **Esplora soluzioni** espandere il nodo **BdcModel1**, quindi aprire il file BdcModel1.bdcm.  
  
2.  Il file del modello di integrazione applicativa dei dati verrà aperto nella finestra di progettazione dell'integrazione applicativa dei dati.  
  
3.  Nella finestra di progettazione aprire il menu di scelta rapida per il nodo **Entity1**, quindi scegliere **Elimina**.  
  
4.  In **Esplora soluzioni**, aprire il menu di scelta rapida per Entity1.vb \(in Visual Basic\) o su Entity1.cs \(in C\#\) e quindi scegliere **Elimina**.  
  
5.  Aprire il menu di scelta rapida per Entity1Service.vb \(in Visual Basic\) o per Entity1Service.cs \(in C\#\) e quindi scegliere **Elimina**.  
  
## Aggiunta di un'entità al modello  
 Aggiungere un'entità al modello.  È possibile aggiungere entità dalla **Casella degli strumenti** di Visual Studio nella finestra di progettazione dell'integrazione applicativa dei dati.  
  
#### Per aggiungere un'entità al modello  
  
1.  Nella barra dei menu, scegliere **Visualizza**, **Casella degli strumenti**.  
  
2.  Nella scheda **BusinessDataConnectivity** della **Casella degli strumenti** aggiungere un elemento da **Entità** nella finestra di progettazione dell'integrazione applicativa dei dati.  
  
     La nuova entità verrà visualizzata nella finestra di progettazione.  Visual Studio aggiunge un file al progetto denominato EntityService.vb \(in Visual Basic\) o EntityService.cs \(in C\#\).  
  
3.  Nella barra dei menu, scegliere **Visualizza**, **Proprietà**, **Finestra**.  
  
4.  Nella finestra **Proprietà** impostare la proprietà **Nome** a Contatto.  
  
5.  In progettazione, aprire il menu di scelta rapida per l'entità, scegliere **Aggiungi**, quindi scegliere **Identificatore**.  
  
     Il nuovo identificatore verrà visualizzato nell'entità.  
  
6.  Nella finestra **Proprietà** modificare il nome dell'identificatore in ContactID.  
  
7.  Nell'elenco **Nome tipo**, scegliere **System.Int32**.  
  
## Aggiunta di un metodo Finder specifico  
 Per consentire al servizio di integrazione applicativa dei dati di visualizzare un contatto specifico, è necessario aggiungere un metodo Finder specifico.  Il servizio di integrazione applicativa dei dati chiama il metodo Finder specifico quando un utente seleziona un elemento in un elenco e seleziona il pulsante **Visualizza elemento** sulla barra multifunzione.  
  
 Aggiungere un metodo Finder specifico all'entità Contact tramite la finestra **Dettagli metodo di integrazione applicativa dei dati**.  Per restituire un'entità specifica, aggiungere codice al metodo.  
  
#### Per aggiungere un metodo Finder specifico  
  
1.  Nella finestra di progettazione dell'integrazione applicativa dei dati selezionare l'entità **Contact**.  
  
2.  Sulla barra dei menu, scegliere **Visualizza**, **Altre finestre**, **Dettagli metodo di integrazione applicativa dei dati**.  
  
     Viene visualizzata la finestra Dettagli metodo di integrazione applicativa dei dati  
  
3.  Nell'elenco di **Aggiungi un metodo**, scegliere **Crea metodo Finder specifico**.  
  
     In Visual Studio vengono aggiunti gli elementi seguenti al modello.  Questi elementi vengono visualizzati nella finestra **Dettagli metodo di integrazione applicativa dei dati**.  
  
    -   Metodo denominato Readitem.  
  
    -   Parametro di input per il metodo.  
  
    -   Parametro restituito per il metodo.  
  
    -   Descrittore di tipo per ogni parametro.  
  
    -   Istanza di metodo per il metodo.  
  
4.  Nella finestra **Dettagli Metodo BDC**, aprire l'elenco visualizzato per il descrittore di tipo **Contact**, quindi scegliere **Modifica**.  
  
     In **Esplora integrazione applicativa dei dati** aprire e fornire una visualizzazione gerarchica del modello.  
  
5.  Nella finestra **Proprietà**, aprire l'elenco accanto alla proprietà **Typename**, scegliere la scheda **Progetto corrente** quindi scegliere la proprietà **Contatto**.  
  
6.  In **Esplora BDC**, aprire il menu di scelta rapida di **Contatto** e scegliere **Aggiungi descrittore di tipo**.  
  
     Un nuovo descrittore di tipo denominato **TypeDescriptor1** verrà visualizzato in **Esplora integrazione applicativa dei dati**.  
  
7.  Nella finestra **Proprietà** impostare la proprietà **Nome** su **ContactID**.  
  
8.  Aprire l'elenco accanto alla proprietà **Typename** quindi scegliere **Int32**.  
  
9. Aprire l'elenco accanto alla proprietà **Identificatore** quindi scegliere **ContactID**.  
  
10. Ripetere il passaggio 6 per creare un descrittore di tipo per ognuno dei campi riportati di seguito.  
  
    |Nome|Nome tipo|  
    |----------|---------------|  
    |FirstName|System.String|  
    |LastName|System.String|  
    |Phone|System.String|  
    |EmailAddress|System.String|  
    |EmailPromotion|System.Int32|  
    |NameStyle|System.Boolean|  
    |PasswordHash|System.String|  
    |PasswordSalt|System.String|  
  
11. Nella finestra di progettazione dell'integrazione applicativa dei dati aprire il metodo **ReadItem** nell'entità **Contact**.  
  
     Il file di codice servizio di Contact verrà aperto nell'editor di codice.  
  
12. Nella classe `ContactService` sostituire il metodo `ReadItem` con il codice riportato di seguito.  Mediante il codice vengono effettuate le seguenti attività:  
  
    -   Recupero di un record dalla tabella Contact del database AdventureWorks.  
  
    -   Restituzione di un'entità Contact al servizio di integrazione applicativa dei dati.  
  
    > [!NOTE]  
    >  Sostituire il valore del campo `ServerName` con il nome del server locale.  
  
     [!code-csharp[SP_BDC#3](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#3)]
     [!code-vb[SP_BDC#3](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#3)]  
  
## Aggiunta di un metodo Finder  
 Per consentire al servizio di integrazione applicativa dei dati di visualizzare i contatti in un elenco, è necessario aggiungere un metodo Finder.  Aggiungere un metodo Finder all'entità Contact tramite la finestra **Dettagli metodo di integrazione applicativa dei dati**.  Per restituire una raccolta di entità al servizio di integrazione applicativa dei dati, aggiungere codice al metodo.  
  
#### Per aggiungere un metodo Finder  
  
1.  Nella finestra di progettazione dell'integrazione applicativa dei dati selezionare l'entità **Contact**.  
  
2.  Nella finestra **Dettagli metodo di integrazione applicativa dei dati** comprimere il nodo **ReadItem**.  
  
3.  Nell'elenco **Aggiungi un metodo** sotto **ReadList**, scegliere **Crea metodo Finder**.  
  
     In Visual Studio verranno aggiunti automaticamente un metodo, un parametro restituito e un descrittore di tipo.  
  
4.  Nella finestra di progettazione dell'integrazione applicativa dei dati aprire il metodo **ReadList** nell'entità **Contact**.  
  
     Il file di codice per il servizio di Contact verrà aperto nell'editor di codice.  
  
5.  Nella classe `ContactService` sostituire il metodo `ReadList` con il codice riportato di seguito.  Mediante il codice vengono effettuate le seguenti attività:  
  
    -   Recupero dei dati dalla tabella Contacts del database AdventureWorks.  
  
    -   Restituzione di un elenco di entità Contact al servizio di integrazione applicativa dei dati.  
  
    > [!NOTE]  
    >  Sostituire il valore del campo `ServerName` con il nome del server locale.  
  
     [!code-csharp[SP_BDC#2](../snippets/csharp/VS_Snippets_OfficeSP/sp_bdc/CS/bdcmodel1/contactservice.cs#2)]
     [!code-vb[SP_BDC#2](../snippets/visualbasic/VS_Snippets_OfficeSP/sp_bdc/VB/bdcmodel1/contactservice.vb#2)]  
  
## Verifica del progetto  
 Quando si esegue il progetto, viene aperto il sito di SharePoint e in Visual Studio viene aggiunto il modello al servizio di integrazione applicativa dei dati.  Creare un elenco esterno in SharePoint che faccia riferimento all'entità Contact.  I dati per i contatti nel database AdventureWorks vengono visualizzati nell'elenco.  
  
> [!NOTE]  
>  Può essere necessario modificare le impostazioni di sicurezza in SharePoint prima di eseguire il debug della soluzione.  Per ulteriori informazioni, vedere [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md).  
  
#### Per verificare il progetto  
  
1.  Premere **F5**.  
  
     Verrà aperto il sito di SharePoint.  
  
2.  Dal menu **Azioni sito**, scegliere il comando **Altre opzioni**.  
  
3.  Nella pagina **Crea**, scegliere il modello **Elenco esterno** quindi scegliere il pulsante **Crea**.  
  
4.  Assegnare il nome Contatti all'elenco personalizzato.  
  
5.  Scegliere il pulsante sfoglia accanto al campo **Tipo di contenuto esterno**.  
  
6.  Nella finestra di dialogo **Selezione tipo di contenuto esterno** selezionare l'elemento **AdventureWorksContacts.BdcModel1.Contact**, quindi fare clic su **Crea**.  
  
     In SharePoint viene creato un elenco esterno che contiene i contatti del database di esempio AdventureWorks.  
  
7.  Per testare il metodo Finder specifico, scegliere un contatto nell'elenco.  
  
8.  Sulla barra multifunzione, scegliere la scheda **Elementi** quindi scegliere il comando **Visualizza elemento**.  
  
     I dettagli del contatto selezionato verranno visualizzati in un form.  
  
## Passaggi successivi  
 Per ulteriori informazioni sulla progettazione di modelli per il servizio di integrazione applicativa dei dati in SharePoint, vedere i seguenti argomenti:  
  
-   [Procedura: aggiungere un metodo Creator](../sharepoint/how-to-add-a-creator-method.md).  
  
-   [Procedura: aggiungere un metodo Updater](../sharepoint/how-to-add-an-updater-method.md).  
  
-   [Procedura: aggiungere un metodo Deleter](../sharepoint/how-to-add-a-deleter-method.md).  
  
## Vedere anche  
 [Progettazione di un modello di integrazione applicativa dei dati](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Creazione di un modello di integrazione applicativa dei dati](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Panoramica degli strumenti di progettazione del modello di integrazione applicativa dei dati](../sharepoint/bdc-model-design-tools-overview.md)   
 [Integrazione di dati business in SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)  
  
  