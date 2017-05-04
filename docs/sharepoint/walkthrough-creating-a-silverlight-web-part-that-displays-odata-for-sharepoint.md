---
title: "Procedura dettagliata: creazione di una Web part Silverlight che visualizza il servizio OData per SharePoint | Microsoft Docs"
ms.custom: ""
ms.date: "02/22/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.SharePointTools.SPE.SilverlightWebPart"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 92d55e68-8f3f-4bf7-a21b-801c298b04c4
caps.latest.revision: 21
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 20
---
# Procedura dettagliata: creazione di una Web part Silverlight che visualizza il servizio OData per SharePoint
  SharePoint 2010 espone i dati dell'elenco mediante OData.  In SharePoint, il servizio di OData viene implementato dal servizio RESTful ListData.svc.  Questa procedura dettagliata mostra come creare un web part SharePoint che ospita un'applicazione Silverlight.  L'applicazione Silverlight mostra le informazioni riguardanti un elenco di annunci SharePoint utilizzando ListData.svc.  Per ulteriori informazioni, vedere [Interfaccia REST di SharePoint Foundation](http://go.microsoft.com/fwlink/?LinkId=225999) ed [Aprire il protocollo di dati](http://go.microsoft.com/fwlink/?LinkId=226000).  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   [Creare un'applicazione Silverlight e una Web part di Silverlight](#BKMK_creatingSLApp).  
  
-   [Personalizzazione dell'applicazione Silverlight](#BKMK_customizeSLApp).  
  
-   [Personalizzazione dell'applicazione Silverlight](#BKMK_customizeSLApp).  
  
-   [Personalizzazione dell'applicazione Silverlight](#BKMK_customizeSLApp).  
  
-   [Test delle web part di Silverlight](#BKMK_testSLApp).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Microsoft Windows e SharePoint.  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
##  <a name="BKMK_creatingSLApp"></a> Creare un'applicazione Silverlight e una Web part di Silverlight  
 Innanzitutto, creare un'applicazione Silverlight in Visual Studio.  L'applicazione Silverlight recupera i dati dall'elenco di annunci SharePoint utilizzando il servizio ListData.svc.  
  
> [!NOTE]  
>  Nessun versione di Silverlight 4.0 supporta le interfacce richieste per far riferimento ai dati di elenchi SharePoint.  
  
#### Per creare un'applicazione Silverlight e una web part di Silverlight.  
  
1.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto** per visualizzare la finestra di dialogo **Nuovo progetto**.  
  
2.  Espandere il nodo **SharePoint** sotto **Visual C\#** o **Visual Basic**, quindi scegliere il nodo **2010**.  
  
3.  Nel riquadro Modelli, selezionare il modello **SharePoint 2010 Silverlight Web Part**.  
  
4.  Nella casella di testo **Nome**, inserire SLWebPartTest e selezionare il pulsante **OK**.  
  
     Viene visualizzata la finestra di dialogo **Personalizzazione guidata SharePoint**.  
  
5.  Nella pagina **Specificare il sito e il livello di sicurezza per il debug** immettere l'URL per il server del sito SharePoint in cui si desidera eseguire il debug della definizione del sito o utilizzare il percorso predefinito \(http:\/\/*system name*\/\).  
  
6.  Nella sezione **Selezionare il livello di attendibilità per la soluzione SharePoint** scegliere il pulsante di opzione **Distribuisci come soluzione farm**.  
  
     Anche se in questo esempio viene utilizzata una soluzione farm, i progetti web part di Silverlight possono essere distribuiti sia come farm o mediate la creazione di soluzioni di sandbox.  Per ulteriori informazioni sulle differenze tra le soluzioni create mediante sandbox e quelle farm, vedere [Considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Nella sezione **Come si desidera associare la Web part Silverlight** della pagina **Specifica informazioni di configurazione Silverlight**, scegliere il pulsante di opzione **Crea nuovo progetto Silverlight e associalo alla web part**.  
  
8.  Modificare **Nome** in SLApplication, impostare **Linguaggio** su **Visual Basic** o **Visual C\#**, quindi impostare **Versione di Silverlight** su **Silverlight 4.0**.  
  
9. Fare clic sul pulsante **Fine**.  Il progetto viene visualizzato in **Esplora soluzioni**.  
  
     La soluzione contiene due progetti: un'applicazione Silverlight e una web part di Silverlight.  L'applicazione Silverlight recuperare e visualizza l'elenco dei dati da SharePoint e la web part di Silverlight ospita l'applicazione Silverlight, consentendo la visualizzazione su SharePoint.  
  
##  <a name="BKMK_customizeSLApp"></a> Personalizzazione dell'applicazione Silverlight  
 Aggiungere gli elementi di progettazione e il codice all'applicazione Silverlight  
  
#### Per personalizzare l'applicazione Silverlight  
  
1.  Aggiungere un riferimento ad un assembly a System.Windows.Data nell'applicazione Silverlight.  Per ulteriori informazioni, vedere [Procedura: aggiungere o rimuovere riferimenti utilizzando la finestra di dialogo Aggiungi riferimento](http://msdn.microsoft.com/it-it/3bd75d61-f00c-47c0-86a2-dd1f20e231c9).  
  
2.  In **Esplora soluzioni** aprire il menu di scelta rapida per **Riferimento**, quindi scegliere **Aggiungi riferimento**.  
  
    > [!NOTE]  
    >  Se si utilizza Visual Basic, è necessario scegliere l'icona **Mostra tutti i file** all'inizio di **Esplora soluzioni** per visualizzare il nodo **Riferimenti**.  
  
3.  Nella casella Indirizzo della finestra di dialogo **Aggiungi riferimento al servizio**, immettere l'url del sito di SharePoint, ad esempio **http:\/\/MySPSite**quindi scegliere il pulsante **Vai**.  
  
     Quando Silverlight individua il servizio ListData.svc di SharePoint OData, sostituisce l'indirizzo con il servizio URL completo.  Per questo esempio, http:\/\/myserver è http:\/\/myserver\/\_vti\_bin\/ListData.svc.  
  
4.  Selezionare il pulsante **OK** per aggiungerlo ad un progetto e utilizzare il nome predefinito del servizio, ServiceReference1.  
  
5.  Sulla barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
6.  Aggiungere una nuova origine dei dati al progetto in base al servizio di SharePoint.  Per fare questo, nel menu, scegliere **Visualizza**, **Altre finestre**, **Origini dati**.  
  
     La finestra **Origini dati** mostra tutti i dati disponibili nell'elenco di SharePoint, ad esempio attività, annunci e calendario.  
  
7.  Aggiungere dati dell'elenco di annunci all'applicazione Silverlight.  È possibile trascinare "Annunci" dalla finestra di **Origini dati** nella finestra di progettazione Silverlight.  
  
     Verrà creata una griglia di controllo associata all'elenco degli annunci sul sito SharePoint.  
  
8.  Ridimensionare la griglia di controllo per adattarla alla pagina Silverlight.  
  
9. Nel file di codice MainPage.xaml \(MainPage.xaml.cs per Visual C\# o in MainPage.xaml.vb per Visual Basic\), aggiungere i seguenti riferimenti allo spazi dei nomi.  
  
    ```vb  
    ' Add the following three Imports statements.  
    Imports SLApplication.ServiceReference1  
    Imports System.Windows.Data  
    Imports System.Data.Services.Client  
    ```  
  
    ```csharp  
    // Add the following three using statements.  
    using SLApplication.ServiceReference1;  
    using System.Windows.Data;  
    using System.Data.Services.Client;  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#1](SP_SLWebPart#1)]  -->  
  
10. Aggiungere la seguente dichiarazione della variabile all'inizio della classe.  
  
    ```vb  
    Private context As TeamSiteDataContext  
    Private myCollectionViewSource As CollectionViewSource  
    Private announcements As New DataServiceCollection(Of AnnouncementsItem)()  
    ```  
  
    ```csharp  
    private TeamSiteDataContext context;  
    private CollectionViewSource myCollectionViewSource;  
    DataServiceCollection<AnnouncementsItem> announcements = new DataServiceCollection<AnnouncementsItem>();  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#2](SP_SLWebPart#2)]  -->  
  
11. Sostituire la procedura `UserControl_Loaded` con quanto riportato di seguito:  
  
    ```vb  
    Private Sub UserControl_Loaded_1(sender As Object, e As RoutedEventArgs)  
        ' The URL for the OData service.  
        ' Replace <server name> in the next line with the name of your SharePoint server.  
        context = New TeamSiteDataContext(New Uri("http://<server name>/_vti_bin/ListData.svc"))  
  
        ' Do not load your data at design time.  
        If Not System.ComponentModel.DesignerProperties.GetIsInDesignMode(Me) Then  
            'Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource =   DirectCast(Me.Resources("announcementsViewSource"), System.Windows.Data.CollectionViewSource)  
            announcements.LoadCompleted += New EventHandler(Of LoadCompletedEventArgs)(AddressOf announcements_LoadCompleted)  
            announcements.LoadAsync(context.Announcements)  
        End If  
    End Sub  
    ```  
  
    ```csharp  
    private void UserControl_Loaded_1(object sender, RoutedEventArgs e)  
    {  
        // The URL for the OData service.  
        // Replace <server name> in the next line with the name of your   
        // SharePoint server.  
        context = new TeamSiteDataContext(new Uri("http://ServerName>/_vti_bin/ListData.svc"));  
  
        // Do not load your data at design time.  
        if (!System.ComponentModel.DesignerProperties.GetIsInDesignMode(this))  
        {  
            //Load your data here and assign the results to the CollectionViewSource.  
            myCollectionViewSource = (System.Windows.Data.CollectionViewSource)this.Resources["announcementsViewSource"];  
            announcements.LoadCompleted += new EventHandler<LoadCompletedEventArgs>(announcements_LoadCompleted);  
            announcements.LoadAsync(context.Announcements);  
        }  
    }  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#3](SP_SLWebPart#3)]  -->  
  
     Assicurarsi di sostituire il segnaposto *ServerName* con il nome del server che esegue SharePoint.  
  
12. Aggiungere la seguente routine di gestione degli errori.  
  
    ```vb  
    Private Sub announcements_LoadCompleted(sender As Object, e As LoadCompletedEventArgs)  
        ' Handle any errors.  
        If e.[Error] Is Nothing Then  
            myCollectionViewSource.Source = announcements  
        Else  
            MessageBox.Show(String.Format("ERROR: {0}", e.[Error].Message))  
        End If  
    End Sub  
  
    ```  
  
    ```csharp  
    void announcements_LoadCompleted(object sender, LoadCompletedEventArgs e)  
    {  
        // Handle any errors.  
        if (e.Error == null)  
        {  
            myCollectionViewSource.Source = announcements;  
        }  
        else  
        {  
            MessageBox.Show(string.Format("ERROR: {0}", e.Error.Message));  
        }  
    }  
    ```  
  
<!-- TODO: review snippet reference      [!CODE [SP_SLWebPart#4](SP_SLWebPart#4)]  -->  
  
## Modificare la Web part di Silverlight  
 Modificare una proprietà nel progetto della web part di Silverlight per abilitare il debugging di Silverlight.  
  
#### Per modificare la web part di Silverlight  
  
1.  Aprire il menu di scelta rapida per il progetto della web part di Silverlight \(**SLWebPartTest**\), e scegliere **Proprietà**.  
  
2.  Nella finestra **Proprietà** scegliere la scheda **SharePoint**.  
  
3.  Se non è già selezionata, selezionare la casella di controllo **Abilita debug Silverlight \(anziché il debug degli script\)**.  
  
4.  Salvare il progetto.  
  
##  <a name="BKMK_testSLApp"></a> Test delle web part di Silverlight  
 Verificare la nuova web part di Silverlight in SharePoint per garantire che visualizzi l'elenco dei dati di SharePoint correttamente.  
  
#### Per testare la web part di Silverlight  
  
1.  Premere il tasto F5 per compilare ed eseguire la soluzione SharePoint.  
  
2.  In SharePoint, nel menu **Azioni sito**, scegliere **Nuova pagina**.  
  
3.  Nella finestra di dialogo **Nuova pagina**, immettere un titolo, come ad esempio SL Web Part Test, quindi selezionare il pulsante **Crea**.  
  
4.  Nella finestra di progettazione della pagina, nella scheda **Strumenti di modifica**, scegliere **Inserimento**.  
  
5.  Nell'elenco schede, scegliere **Web part**.  
  
6.  Nella casella **Categorie**, scegliere la cartella **Personalizza**.  
  
7.  Nell'elenco di **Web part**, selezionare la web part di Silverlight e scegliere il pulsante **Aggiungi** per aggiungere la web part alla finestra di progettazione.  
  
8.  Dopo avere apportato tutte le aggiunte desiderate alla pagina Web, scegliere la scheda **Pagina** quindi scegliere il pulsante di **Salva & Chiudi** sulla barra degli strumenti.  
  
     La web part di Silverlight dovrebbe ora visualizzare i dati degli annunci dal sito SharePoint.  Per impostazione predefinita, la pagina viene archiviata nelle pagine del sito elencate in SharePoint.  
  
    > [!NOTE]  
    >  Quando si accede ai dati in Silverlight tramite i domini, Silverlight protegge dalle vulnerabilità di sicurezza che possono essere utilizzare per effettuare uno exploit dell'applicazione web.  Se si verificano problemi durante l'accesso ai dati remoti in Silverlight, vedere [Rendere disponibile un servizio tra i limiti di dominio](http://go.microsoft.com/fwlink/?LinkId=223276).  
  
## Vedere anche  
 [Creazione di web part per SharePoint](../sharepoint/creating-web-parts-for-sharepoint.md)   
 [Distribuzione, pubblicazione e aggiornamento dei pacchetti delle soluzioni SharePoint](../sharepoint/deploying-publishing-and-upgrading-sharepoint-solution-packages.md)  
  
  