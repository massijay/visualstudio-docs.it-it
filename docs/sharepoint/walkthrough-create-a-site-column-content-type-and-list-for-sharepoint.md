---
title: "Procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.ListDesigner.GeneralMessageHelp"
  - "Microsoft.VisualStudio.SharePoint.Designers.ListDesigner.ViewModels.ListViewModel.SortingAndGrouping"
  - "VS.SharePointTools.ListDesigner.SortingGrouping"
dev_langs: 
  - "VB"
  - "CSharp"
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "sviluppo per SharePoint in Visual Studio, tipi di contenuto"
  - "sviluppo per SharePoint in Visual Studio, campi"
  - "sviluppo per SharePoint in Visual Studio, definizioni di elenco"
  - "sviluppo per SharePoint in Visual Studio, istanze di elenco"
ms.assetid: caebacc2-616c-4373-8e21-edc7979338e7
caps.latest.revision: 54
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 53
---
# Procedura dettagliata: creare una colonna del sito, un tipo di contenuto e un elenco per SharePoint
  Nelle procedure seguenti viene illustrato come creare un sito di SharePoint personalizzato—o *campi*—nonché come utilizzare il tipo di contenuto per l'utilizzo delle colonne del sito.  Viene inoltre illustrato come creare un elenco che contiene il nuovo tipo di contenuto.  
  
 In questa procedura dettagliata sono incluse le attività seguenti:  
  
-   [Creare le colonne personalizzate del sito](#BKMK_CreatingCustSiteCols).  
  
-   [Creazione di un tipo di contenuto personalizzato](#BKMK_CreateCustContType).  
  
-   [Creare un elenco](#BKMK_CreateList).  
  
-   [Creare un elenco](#BKMK_CreateList).  
  
-   [Verifica dell'applicazione](#BKMK_TestApp).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Windows e SharePoint.  Per ulteriori informazioni, vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio.  
  
##  <a name="BKMK_CreatingCustSiteCols"></a> Creare le colonne personalizzate del sito  
 In questo esempio viene creato un elenco per gestire i pazienti di un ospedale.  Innanzitutto, è necessario creare un progetto SharePoint in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] e aggiungere le colonne del sito, come l'esempio seguente.  
  
#### Per creare il progetto  
  
1.  Nel menu [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] **File**, scegliere **Nuovo**, **Progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto**, sotto **Visual Basic** o **Visual C\#**, espandere il nodo **SharePoint**, quindi selezionare **2010**.  
  
3.  Nel pannello **Modello**, selezionare **Progetto SharePoint 2010**, modificare il nome del progetto in Clinic, quindi selezionare il pulsante **OK**.  
  
     Il modello di progetto di SharePoint 2010 è un progetto vuoto che viene utilizzato in questo esempio per contenere colonne del sito e altri elementi di progetto che sono aggiunti successivamente.  
  
4.  Nella pagina **Specificare il sito e il livello di sicurezza per il debug** immettere l'URL per il sito locale SharePoint a cui si desidera aggiungere il nuovo elemento del campo personalizzato oppure utilizzare il percorso predefinito \(`http://<`*SystemName*`>/)`.  
  
5.  Nella sezione **Selezionare il livello di attendibilità per la soluzione SharePoint** utilizzare il valore predefinito **Distribuisci come soluzione creata mediante sandbox**.  
  
     Per ulteriori informazioni sulle soluzioni create mediante sandbox e quelle della farm, vedere [Considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
6.  Fare clic sul pulsante **Fine**.  Il progetto dovrebbe ora essere elencato in **Esplora soluzioni**.  
  
#### Per aggiungere colonne del sito  
  
1.  Aggiungere una nuova colonna del sito.  Per fare questo, In **Esplora soluzioni** aprire il menu di scelta rapida per la cartella **Clinic**, quindi scegliere **Aggiungi**, **Nuovo elemento**.  
  
2.  Nella finestra di dialogo **Aggiungi nuovo elemento**, scegliere il campo **Site Column**, modificare il Nome del paziente e quindi selezionare il pulsante **Aggiungi**.  
  
3.  Nella colonna del sito del file Elements.xml , lasciare il **Tipo** impostato come **Testo** e modificare il **Gruppo** per impostare le colonne del sito della clinica.  Al termine, le colonne del sito del file Elements.xml devono essere analoghe alle seguenti.  
  
    ```  
    <Field  
         ID="{f9ba60d1-5631-41fb-b016-a38cf48eef63}"  
         Name="Clinic - Patient Name"  
         DisplayName="Patient Name"  
         Type="Text"  
         Required="FALSE"  
         Group="Clinic Site Columns">  
    </Field>  
    ```  
  
4.  Utilizzando la stessa procedura, aggiungere altre due colonne del sito del progetto: Paziente ID \(tipo \= "integer"\) e il Nome dottore \(tipo \= "text"\).  Impostare il valore del gruppo sulle colonne del sito della clinica.  
  
##  <a name="BKMK_CreateCustContType"></a> Creazione di un tipo di contenuto personalizzato  
 Successivamente, creare un tipo di contenuto—basato sul tipo di contenuto dei Contatti—che include le colonne del sito creato nella procedura precedente.  Basare un tipo di contenuto su un tipo di contenuto esistente, consente di risparmiare tempo perché il tipo di contenuto di base fornisce diverse colonne del sito che possono essere utilizzate nel nuovo tipo di contenuto.  
  
#### Per creare un tipo di contenuto personalizzato  
  
1.  Aggiungere un tipo di contenuto al progetto.  Per fare questo, in **Esplora soluzioni** selezionare il nodo del progetto.  
  
2.  Sulla barra dei menu scegliere **Progetto**, **Aggiungi nuovo elemento**.  
  
3.  Sotto **Visual C\#** o **Visual Basic**, espandere il nodo **SharePoint**, quindi scegliere il nodo **2010**.  
  
4.  Nel riquadro **Modelli**, scegliere il modello **Tipo contenuto**, modificare il nome in Informazioni paziente e quindi selezionare il pulsante **Aggiungi**.  
  
     Si aprirà la **Personalizzazione guidata SharePoint**.  
  
5.  Nell'elenco **Selezionare il tipo di contenuti di base che il tipo di contenuti dovrebbe ereditare da**, scegliere **Contatto** come tipo di contenuto sul quale basare il nuovo tipo di contenuto e quindi selezionare il pulsante **Fine**.  
  
     Questa operazione consente l'accesso ad altre colonne del sito potenzialmente utili nel tipo di contenuto del Contatto, oltre alle colonne del sito che sono state definite in precedenza.  
  
6.  Dopo che la finestra di progettazione del tipo di contenuto viene visualizzata, nella scheda **Colonne**, aggiungere le tre colonne del sito definito in precedenza: **Nome paziente**, **ID paziente** e **Nome dottore**.  Per aggiungere queste colonne, selezionare la prima casella di riepilogo nelle colonne del sito elencate sotto **Nome visualizzato** quindi selezionare una alla volta ogni colonna del sito nell'elenco.  
  
    > [!TIP]  
    >  Per selezionare più rapidamente le colonne del sito, filtrare l'elenco immettendo le prime lettere del nome della colonna.  
  
7.  Oltre alle tre colonne personalizzate del sito, aggiungere la colonna del sito **Commenti** dall'elenco delle colonne del sito.  
  
8.  Selezionare la casella di controllo **Obbligatorio** per le colonne del sito **ID paziente** e **Nome paziente** rendendo tali campi obbligatori.  
  
9. Nella scheda **Tipo contenuto**, assicurarsi che il nome del tipo di contenuto sia **Info paziente**, quindi modificare la descrizione nella scheda informazioni paziente.  
  
10. Modificare il **Nome gruppo** in tipo di contenuto clinica e lasciando le altre impostazioni invariate sui valori predefiniti.  
  
11. Sulla barra dei menu, scegliere **File**, **Salva tutto** quindi chiudere la finestra di progettazione del tipo di contenuto.  
  
##  <a name="BKMK_CreateList"></a> Creare un elenco  
 A questo punto, creare un elenco che utilizza le nuove colonne del sito e del tipo di contenuto.  
  
#### Per creare un elenco  
  
1.  Aggiungere un elenco al progetto.  Per fare questo, in **Esplora soluzioni** selezionare il nodo del progetto.  
  
2.  Sulla barra dei menu scegliere **Progetto**, **Aggiungi nuovo elemento**.  
  
3.  Sotto **Visual C\#** o **Visual Basic**, espandere il nodo **SharePoint**, quindi scegliere il nodo **2010**.  
  
4.  Nel riquadro **Modelli**, scegliere il modello **Elenco**, modificare il nome in Pazienti e quindi selezionare il pulsante **Aggiungi**.  
  
5.  Lasciare **Personalizza l'elenco basato su** impostato su **Predefinito \(vuoto\)**quindi selezionare il pulsante **Fine**.  
  
6.  Nella finestra di progettazione dell'elenco, scegliere il pulsante **Tipi di contenuto** per visualizzare la finestra di dialogo **Impostazioni tipo di contenuto**.  
  
7.  Scegliere la nuova riga, selezionare il tipo di contenuto **Informazioni paziente** nei tipi di elenco contenuti e quindi selezionare il pulsante **OK**.  
  
     Questa operazione consente di aggiungere tutte le colonne del sito dal tipo di contenuto **Informazioni paziente** all'elenco.  
  
8.  Eliminare tutte le colonne del sito nell'elenco tranne le seguenti:  
  
    -   Paziente ID  
  
    -   Nome paziente  
  
    -   Telefono abitazione  
  
    -   Posta elettronica  
  
    -   Nome dottore  
  
    -   Commenti  
  
9. In **Nome visualizzato nella colonna**, scegliere una riga vuota, aggiungervi una colonna personalizzata dell'elenco e denominarla Ospedale.  Lasciare il tipo di dati come **Singola riga di testo**.  
  
     La colonna personalizzata dell'elenco viene applicata solo a questo elenco.  Quando si aggiunge una colonna personalizzata dell'elenco su un elenco, un nuovo tipo di contenuto elenco, incluse le eventuali colonne aggiunte dell'elenco, viene creato e impostato come illustrato nell'elenco predefinito.  
  
    > [!TIP]  
    >  Se si sceglie una colonna dall'elenco delle colonne del sito, viene utilizzata una colonna di sito esistente.  Tuttavia, se viene inserito il valore del nome nella colonna senza scegliere alcune colonne dell'elenco, viene creata una colonna personalizzata dell'elenco, anche se è già esistente una colonna con lo stesso nome.  
  
     Facoltativamente, anziché impostare il tipo di dati della colonna personalizzata dell'elenco su **Singola riga di testo**, è possibile invece impostare il tipo di dati per questa colonna di ricerca e i relativi valori vengono recuperati da una tabella oppure da un altro elenco.  Per informazioni sulle colonne di ricerca, vedere [Relazioni di elenco in SharePoint 2010](http://go.microsoft.com/fwlink/?LinkId=224994) ed [Ricerche e relazioni di elenco](http://go.microsoft.com/fwlink/?LinkID=224995).  
  
10. Accanto alle caselle **Nome paziente** e **ID paziente**, selezionare la casella di controllo **Obbligatorio**.  
  
11. Nella scheda **Viste**, scegliere una riga vuota per creare una visualizzazione.  Immettere i dettagli del paziente  
  
     Nella scheda **Viste**, è possibile specificare le colonne che si desidera visualizzare nell'elenco SharePoint.  
  
12. Scegliere nuova riga **Dettagli paziente** quindi scegliere il pulsante **Imposta come predefinito**.  
  
     La nuova visualizzazione ora rappresenta la visualizzazione predefinita dell'elenco.  
  
13. Aggiungere le seguenti colonne all'elenco **Colonne selezionate** nel seguente ordine:  
  
    -   Paziente ID  
  
    -   Nome paziente  
  
    -   Telefono abitazione  
  
    -   Posta elettronica  
  
    -   Nome dottore  
  
    -   Ospedale  
  
    -   Commenti  
  
14. Nell'elenco **Proprietà**, scegliere la proprietà **Ordinamento e raggruppamento** quindi scegliere il pulsante con i puntini di sospensione ![Icona con i puntini di sospensione](../sharepoint/media/ellipsisicon.png "Icona con i puntini di sospensione") per visualizzare la finestra di dialogo **Ordinamento e raggruppamento**.  
  
15. Nell'elenco **Nome colonna**, scegliere **Nome paziente**, assicurarsi che la colonna **Ordinamento** sia impostata su **Crescente** quindi selezionare il pulsante **OK**.  
  
##  <a name="BKMK_TestApp"></a> Verifica dell'applicazione  
 Ora che le colonne, il tipo di contenuto e l'elenco personalizzato del sito sono pronti, distribuirle su SharePoint ed eseguire l'applicazione verificando il funzionamento.  
  
#### Per eseguire il test dell'applicazione  
  
1.  Sulla barra dei menu scegliere **File**, **Salva tutto**.  
  
2.  Premere F5 per eseguire l'applicazione.  
  
     L'applicazione viene compilata quindi le relative funzionalità sono distribuite su SharePoint e sono attivate.  
  
3.  Sulla barra di navigazione rapida, scegliere il collegamento **Pazienti** per visualizzare l'elenco di **Pazienti**.  
  
     I nomi di colonna nell'elenco devono corrispondere a quelli immessi nella scheda **Viste** in [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)].  
  
4.  Scegliere il collegamento **Aggiungi nuovo elemento** per creare una scheda informazioni del paziente.  
  
5.  Immettere le informazioni nei campi e quindi selezionare il pulsante **Salva**.  
  
     Il nuovo record verrà visualizzato nell'elenco.  
  
## Vedere anche  
 [Creazione di colonne del sito, tipi di contenuto ed elenchi per SharePoint](../sharepoint/creating-site-columns-content-types-and-lists-for-sharepoint.md)   
 [Developing SharePoint Solutions](../sharepoint/developing-sharepoint-solutions.md)   
 [Procedura: Creare un tipo di campo personalizzato](http://go.microsoft.com/fwlink/?LinkId=192079)   
 [Tipi di contenuto](http://go.microsoft.com/fwlink/?LinkId=192080)   
 [Colonne](http://go.microsoft.com/fwlink/?LinkId=192081)  
  
  