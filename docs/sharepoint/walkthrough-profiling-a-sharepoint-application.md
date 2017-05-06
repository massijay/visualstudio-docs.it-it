---
title: "Walkthrough: Profiling a SharePoint Application"
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
helpviewer_keywords: 
  - "SharePoint development in Visual Studio, profiling"
  - "performance testing [SharePoint development in Visual Studio]"
  - "SharePoint development in Visual Studio, performance testing"
  - "profiling [SharePoint development in Visual Studio]"
ms.assetid: 0b19d4b7-5fcc-42a2-b411-96eccd00137f
caps.latest.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 15
---
# Walkthrough: Profiling a SharePoint Application
  In questa procedura dettagliata viene illustrato come utilizzare gli strumenti di profilatura in Visual Studio per ottimizzare le prestazioni di un'applicazione SharePoint.  L'applicazione di esempio è un ricevitore di eventi di funzionalità SharePoint contenente un ciclo inattivo che comporta una riduzione delle prestazioni del ricevitore di eventi di funzionalità.  Con il profiler di Visual Studio è possibile individuare ed eliminare la parte più dispendiosa del progetto \(esecuzione più lenta\), nota anche come *percorso ricorrente*.  
  
 In questa procedura dettagliata vengono descritte le attività seguenti:  
  
-   [Aggiunta di una funzionalità e di un ricevitore di eventi di funzionalità](#BKMK_AddFtrandFtrEvntReceiver).  
  
-   [Configurazione e distribuzione dell'applicazione SharePoint](#BKMK_ConfigSharePointApp).  
  
-   [Esecuzione dell'applicazione SharePoint](#BKMK_RunSPApp).  
  
-   [Visualizzazione e interpretazione dei risultati di profilatura](#BKMK_ViewResults).  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Microsoft Windows e SharePoint.  [!INCLUDE[crdefault](../sharepoint/includes/crdefault-md.md)] [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)].  
  
## Creazione di un progetto SharePoint  
 Creare innanzitutto un progetto SharePoint.  
  
#### Per creare un progetto SharePoint  
  
1.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto** per visualizzare la finestra di dialogo **Nuovo progetto**.  
  
2.  Espandere il nodo **SharePoint** sotto **Visual C\#** o **Visual Basic**, quindi scegliere il nodo **2010**.  
  
3.  Nel riquadro dei modelli scegliere il modello **Progetto SharePoint 2010**.  
  
4.  Nella casella **Nome** immettere ProfileTest, quindi scegliere il pulsante **OK**.  
  
     Viene visualizzata la **Personalizzazione guidata SharePoint**.  
  
5.  Nella pagina **Specificare il sito e il livello di sicurezza per il debug** immettere l'URL per il sito del server SharePoint in cui si desidera eseguire il debug della definizione di sito o usare il percorso predefinito \(http:\/\/*nome sistema*\/\).  
  
6.  Nella sezione **Selezionare il livello di attendibilità per la soluzione SharePoint** scegliere il pulsante di opzione **Distribuisci come soluzione farm**.  
  
     Attualmente, è possibile profilare solo soluzioni farm.  Per altre informazioni sulle soluzioni create mediante sandbox e sulle soluzioni farm, vedere [Considerazioni sulle soluzioni create mediante sandbox](../sharepoint/sandboxed-solution-considerations.md).  
  
7.  Fare clic sul pulsante **Fine**.  Il progetto verrà visualizzato in **Esplora soluzioni**.  
  
##  <a name="BKMK_AddFtrandFtrEvntReceiver"></a> Aggiunta di una funzionalità e di un ricevitore di eventi di funzionalità  
 Successivamente, aggiungere una funzionalità al progetto insieme a un ricevitore di eventi per la funzionalità.  In questo ricevitore di eventi sarà incluso il codice da profilare.  
  
#### Per aggiungere una funzionalità e un ricevitore di eventi di funzionalità  
  
1.  In **Esplora soluzioni** aprire il menu di scelta rapida del nodo **Funzionalità**, scegliere **Aggiungi funzionalità** e lasciare il nome del valore predefinito, **Feature1**.  
  
2.  In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo **Feature1**, quindi scegliere **Aggiungi ricevitore di eventi**.  
  
     Verrà aggiunto un file di codice alla funzionalità con diversi gestori di eventi impostati come commenti e viene aperto il file da modificare.  
  
3.  Nella classe del ricevitore di eventi aggiungere le seguenti dichiarazioni di variabili.  
  
    ```vb  
    ' SharePoint site/subsite.  
    Private siteUrl As String = "http://localhost"  
    Private webUrl As String = "/"  
    ```  
  
    ```csharp  
    // SharePoint site/subsite.  
    private string siteUrl = "http://localhost";  
    private string webUrl = "/";  
    ```  
  
4.  Sostituire la procedura `FeatureActivated` con il codice seguente.  
  
    ```vb  
    Public Overrides Sub FeatureActivated(properties As SPFeatureReceiverProperties)  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
  
                    ' Add a new announcement to the Announcements list.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()  
                    ' Waste some time.  
                    TimeCounter()  
                    ' Update the list.  
                    listItem.Update()  
                End Using  
            End Using  
  
        Catch e As Exception  
            Console.WriteLine("Error: " & e.ToString())  
        End Try  
    End Sub  
    ```  
  
    ```csharp  
    public override void FeatureActivated(SPFeatureReceiverProperties properties)  
    {  
        try  
        {  
            using (SPSite site = new SPSite(siteUrl))  
            {  
                using (SPWeb web = site.OpenWeb(webUrl))  
                {  
                    // Reference the lists.  
                    SPList announcementsList = web.Lists["Announcements"];  
  
                    // Add a new announcement to the Announcements list.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " +   
    DateTime.Now.ToString();  
                    // Waste some time.  
                    TimeCounter();  
                    // Update the list.  
                    listItem.Update();                          
                }  
            }  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
    }  
    ```  
  
5.  Aggiungere la procedura seguente sotto la procedura `FeatureActivated`.  
  
    ```vb  
  
    Public Sub TimeCounter()  
        Dim result As Integer  
        For i As Integer = 0 To 99999  
            For j As Integer = 0 To 9999  
                result = i * j  
            Next j  
        Next i  
    End Sub  
    ```  
  
    ```csharp  
    public void TimeCounter()  
    {  
        for (int i = 0; i < 100000; i++)  
        {  
            for (int j = 0; j < 10000; j++)  
            {  
                int result = i * j;  
            }  
        }  
    }  
    ```  
  
6.  In **Esplora soluzioni** aprire il menu di scelta rapida per il progetto \(**ProfileTest**\), quindi scegliere **Proprietà**.  
  
7.  Nella finestra di dialogo **Proprietà** scegliere la scheda **SharePoint**.  
  
8.  Nell'elenco **Configurazione distribuzione attiva** scegliere **Nessuna attivazione**.  
  
     Se si seleziona questa configurazione di distribuzione è possibile attivare manualmente la funzionalità in un secondo momento in SharePoint.  
  
9. Salvare il progetto.  
  
##  <a name="BKMK_ConfigSharePointApp"></a> Configurazione e distribuzione dell'applicazione SharePoint  
 Una volta pronto il progetto SharePoint, è possibile configurarlo e distribuirlo nel server SharePoint.  
  
#### Per configurare e distribuire l'applicazione SharePoint  
  
1.  Nel menu **Analizza** scegliere **Avvia Creazione guidata sessione di prestazioni**.  
  
2.  Nella prima pagina della **Creazione guidata sessione di prestazioni** lasciare il metodo di profilatura come **Campionamento CPU** e scegliere il pulsante **Avanti**.  
  
     Gli altri metodi di profilatura possono essere utilizzati in situazioni di profilatura più avanzate.  Per altre informazioni, vedere [Informazioni sui metodi di profilatura](../profiling/understanding-performance-collection-methods.md).  
  
3.  Nella seconda pagina della **Creazione guidata sessione di prestazioni** lasciare la destinazione di profilo come **ProfileTest** e scegliere il pulsante **Avanti**.  
  
     Se in una soluzione sono disponibili più progetti, vengono visualizzati in questo elenco.  
  
4.  Nella terza pagina della **Creazione guidata sessione di prestazioni** deselezionare la casella di controllo **Abilita profilatura interazione tra livelli**, quindi scegliere il pulsante **Avanti**.  
  
     La funzionalità di profilatura interazione tra livelli \(TIP\) è utile per misurare le prestazioni di applicazioni in cui vengono eseguite query sui database e per visualizzare il numero di volte in cui viene richiesta una pagina Web.  Poiché i dati non sono necessari per questo esempio, la funzionalità non verrà abilitata.  
  
5.  Nella quarta pagina della **Creazione guidata sessione di prestazioni** lasciare selezionata la casella di controllo **Avvia profilatura al termine della procedura guidata**, quindi scegliere il pulsante **Fine**.  
  
     La procedura guidata consente la profilatura dell'applicazione nel server, la visualizzazione della finestra **Esplora prestazioni**, quindi la compilazione, la distribuzione e l'esecuzione dell'applicazione SharePoint.  
  
##  <a name="BKMK_RunSPApp"></a> Esecuzione dell'applicazione SharePoint  
 Attivare la funzionalità in SharePoint, attivando il codice dell'evento `FeatureActivation` da eseguire.  
  
#### Per eseguire l'applicazione SharePoint  
  
1.  In SharePoint aprire il menu **Azioni sito**, quindi scegliere **Impostazioni sito**.  
  
2.  Nell'elenco **Azioni sito** scegliere il collegamento **Gestisci caratteristiche sito**.  
  
3.  Nell'elenco **Funzionalità** scegliere il pulsante **Attiva** accanto a **ProfileTest Feature1**.  
  
     Vi sarà una pausa quando verrà eseguita questa operazione, a causa del ciclo inattivo chiamato nella funzione `FeatureActivated`.  
  
4.  Nella barra **Avvio veloce** scegliere **Elenchi**, quindi nell'elenco **Elenchi** scegliere **Annunci**.  
  
     Si noti che un nuovo annuncio è stato aggiunto all'elenco per indicare che la funzionalità è stata attivata.  
  
5.  Chiudere il sito di SharePoint.  
  
     Dopo aver chiuso SharePoint, tramite il profiler viene creato e visualizzato un Rapporto sulla profilatura dei campioni che viene salvato come file con estensione vsp nella cartella del progetto **ProfileTest**.  
  
##  <a name="BKMK_ViewResults"></a> Visualizzazione e interpretazione dei risultati di profilatura  
 Dopo aver eseguito e profilato l'applicazione SharePoint, visualizzare i risultati del test.  
  
#### Per visualizzare e interpretare i risultati di profilatura  
  
1.  Nella sezione **Funzioni che svolgono più lavoro individuale** del Rapporto sulla profilatura dei campioni si noti che `TimeCounter` è vicino alla parte superiore dell'elenco.  
  
     Questa posizione indica che `TimeCounter` è una delle funzioni con il numero più elevato di campioni, pertanto è uno dei più grandi colli di bottiglia delle prestazioni nell'applicazione.  Questa situazione non è insolita, tuttavia, dal momento che si tratta di una modalità progettata espressamente a scopo dimostrativo.  
  
2.  Nella sezione **Funzioni che svolgono più lavoro individuale** scegliere il collegamento `ProcessRequest` per visualizzare la distribuzione dei costi per la funzione `ProcessRequest`.  
  
     Nella sezione **Funzioni chiamate** per `ProcessRequest` si noti che la funzione **FeatureActiviated** è elencata come la funzione chiamata più costosa.  
  
3.  Nella sezione **Funzioni chiamate** scegliere il pulsante **FeatureActivated**.  
  
     Nella sezione **Funzioni chiamate** per **FeatureActivated** la funzione `TimeCounter` è elencata come la funzione chiamata più costosa.  Nel riquadro **Visualizzazione codice funzione** il codice evidenziato \(`TimeCounter`\) è l'area sensibile e indica il punto in cui è necessaria la correzione.  
  
4.  Chiudere il Rapporto sulla profilatura dei campioni.  
  
     Per visualizzare di nuovo il rapporto in qualsiasi momento, aprire il file con estensione vsp nella finestra **Esplora prestazioni**.  
  
## Correzione del codice e riprofilatura dell'applicazione  
 Una volta identificata la funzione relativa all'area sensibile nell'applicazione SharePoint, correggerla.  
  
#### Per correggere il codice e riprofilare l'applicazione  
  
1.  Nel codice del ricevitore di eventi di funzionalità impostare come commento la chiamata al metodo `TimeCounter` in `FeatureActivated` per impedire che venga chiamato.  
  
2.  Salvare il progetto.  
  
3.  In **Esplora prestazioni** aprire la cartella Destinazioni, quindi scegliere il nodo **ProfileTest**.  
  
4.  Nella scheda **Azioni** sulla barra degli strumenti **Esplora prestazioni** scegliere il pulsante **Avvia profilatura**.  
  
     Se si desidera modificare alcune proprietà di profilatura prima di riprofilare l'applicazione, scegliere invece il pulsante **Avvia Creazione guidata sessione di prestazioni**.  
  
5.  Seguire le istruzioni nella sezione **Esecuzione dell'applicazione SharePoint**, precedentemente in questo argomento.  
  
     L'attivazione della funzionalità dovrebbe essere molto più veloce una volta che è stata eliminata la chiamata al ciclo inattivo.  Il Rapporto sulla profilatura dei campioni dovrebbe riflettere questa situazione.  
  
## Vedere anche  
 [Utilizzo degli strumenti di profilatura](../profiling/performance-explorer.md)   
 [Panoramica delle sessioni di prestazioni degli strumenti per la profilatura](../profiling/performance-session-overview.md)   
 [Guida per principianti alla profilatura delle prestazioni](../profiling/beginners-guide-to-performance-profiling.md)   
 [Individuazione dei colli di bottiglia delle applicazioni con Visual Studio Profiler](http://go.microsoft.com/fwlink/?LinkID=137266)  
  
  