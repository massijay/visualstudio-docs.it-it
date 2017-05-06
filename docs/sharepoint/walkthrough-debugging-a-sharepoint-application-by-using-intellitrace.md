---
title: "Procedura dettagliata: debug di un&#39;applicazione di SharePoint tramite IntelliTrace"
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
  - "IntelliTrace [sviluppo per SharePoint in Visual Studio]"
  - "agente di raccolta dati indipendente"
  - "sviluppo per SharePoint in Visual Studio, IntelliTrace"
  - "agente di raccolta dati"
  - "IntelliTrace"
ms.assetid: 4bd80d2f-f680-4bf4-81c3-f14e8185f6a4
caps.latest.revision: 27
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 26
---
# Procedura dettagliata: debug di un&#39;applicazione di SharePoint tramite IntelliTrace
  Tramite IntelliTrace, è possibile eseguire più facilmente il debug di soluzioni SharePoint.  I debugger tradizionali offrono solo uno snapshot della soluzione al momento corrente.  Tuttavia, è possibile utilizzare IntelliTrace per esaminare eventi passati occorsi nella soluzione e il contesto in cui sono occorsi e navigare attraverso il codice.  
  
 In questa procedura dettagliata viene illustrato come eseguire il debug di un progetto SharePoint 2010 o SharePoint 2013 in Visual Studio Ultimate tramite Microsoft Monitoring Agent per raccogliere dati IntelliTrace dalle applicazioni distribuite.  Per analizzare i dati, è necessario utilizzare Visual Studio Ultimate.  In questo progetto è incorporato un ricevitore di funzionalità che, quando la funzionalità è attivata, consente di aggiungere un'attività all'elenco delle attività e un annuncio all'elenco degli annunci.  Quando la funzionalità viene disattivata, l'attività viene contrassegnata come completata e all'elenco degli annunci viene aggiunto un secondo annuncio.  Tuttavia, nella procedura è contenuto un errore logico che impedisce la corretta esecuzione del progetto.  Tramite IntelliTrace, l'errore verrà individuato e corretto.  
  
 **Si applica a:** Le informazioni contenute in questo argomento si applicano a soluzioni SharePoint 2010 e SharePoint 2013 create in Visual Studio.  
  
 In questa procedura dettagliata vengono illustrate le attività seguenti:  
  
-   [Creare un ricevitore di funzionalità](#BKMK_CreateReceiver)  
  
-   [Aggiungere codice al ricevitore di funzionalità](#BKMK_AddCode)  
  
-   [Testare il progetto](#BKMK_Test1)  
  
-   [Raccogliere dati IntelliTrace tramite Microsoft Monitoring Agent.](#BKMK_CollectDiagnosticData)  
  
-   [Eseguire il debug e correggere la soluzione SharePoint](#BKMK_DebugSolution)  
  
 [!INCLUDE[note_settings_general](../sharepoint/includes/note-settings-general-md.md)]  
  
## Prerequisiti  
 Per completare la procedura dettagliata, è necessario disporre dei componenti seguenti:  
  
-   Edizioni supportate di Windows e SharePoint.  Vedere [Requisiti per lo sviluppo di soluzioni SharePoint](../sharepoint/requirements-for-developing-sharepoint-solutions.md).  
  
-   Visual Studio Ultimate.  
  
##  <a name="BKMK_CreateReceiver"></a> Creare un ricevitore di funzionalità  
 Innanzitutto, creare un progetto SharePoint vuoto con un ricevitore di funzionalità.  
  
#### Per creare un ricevitore di funzionalità  
  
1.  Creare un progetto di soluzione SharePoint 2010 o SharePoint 2013 e denominarlo IntelliTraceTest.  
  
     Verrà visualizzata la **Personalizzazione guidata SharePoint** in cui è possibile specificare sia il sito SharePoint per il progetto sia il livello di attendibilità della soluzione.  
  
2.  Scegliere il pulsante di opzione **Distribuisci come soluzione farm** quindi premere il pulsante **Fine**.  
  
     IntelliTrace funziona solo in soluzioni farm.  
  
3.  In **Esplora soluzioni** aprire il menu di scelta rapida per il nodo **Funzionalità**, quindi scegliere **Aggiungi Funzionalità**.  
  
     Verrà visualizzato Feature1.feature.  
  
4.  Aprire il menu di scelta rapida per Feature1.feature quindi scegliere **Aggiungi ricevitore di eventi** per aggiungere un modulo di codice alla funzionalità.  
  
##  <a name="BKMK_AddCode"></a> Aggiungere codice al ricevitore di funzionalità  
 Successivamente aggiungere codice ai due metodi nel ricevitore di funzionalità `FeatureActivated` e `FeatureDeactivating`.  Questi metodi vengono attivati ogni volta che una funzionalità viene rispettivamente attivata o disattivata in SharePoint.  
  
#### Per aggiungere codice al ricevitore di funzionalità  
  
1.  All'inizio della classe `Feature1EventReceiver` aggiungere il codice seguente il quale dichiara variabili mediante le quali vengono specificati il sito e il sito secondario di SharePoint:  
  
    ```vb  
    ' SharePoint site and subsite.  
    Private siteUrl As String = "http://localhost"  
    Private webUrl As String = "/"  
    ```  
  
    ```csharp  
    // SharePoint site and subsite.  
    private string siteUrl = "http://localhost";  
    private string webUrl = "/";  
    ```  
  
2.  Sostituire il metodo `FeatureActivated` con il codice seguente:  
  
    ```vb  
    Public Overrides Sub FeatureActivated(ByVal properties As SPFeatureReceiverProperties)  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
                    Dim taskList As SPList = web.Lists("Tasks")  
  
                    ' Add an announcement to the Announcements list.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Activated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was activated on: " & DateTime.Now.ToString()  
                    listItem.Update()  
  
                    ' Add a task to the Task list.  
                    Dim newTask As SPListItem = taskList.Items.Add()  
                    newTask("Title") = "Deactivate feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    newTask.Update()  
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
                    SPList taskList = web.Lists["Tasks"];  
  
                    // Add an announcement to the Announcements list.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Activated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was activated on: " + DateTime.Now.ToString();  
                    listItem.Update();  
  
                    // Add a task to the Task list.  
                    SPListItem newTask = taskList.Items.Add();  
                    newTask["Title"] = "Deactivate feature: " + properties.Definition.DisplayName;  
                    newTask.Update();  
                }  
            }  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
  
    }  
    ```  
  
3.  Sostituire il metodo `FeatureDeactivating` con il codice seguente:  
  
    ```vb  
    Public Overrides Sub FeatureDeactivating(ByVal properties As SPFeatureReceiverProperties)  
        ' The following line induces an error to demonstrate debugging.  
        ' Remove this line later for proper operation.  
        Throw New System.InvalidOperationException("Serious error occurred!")  
        Try  
            Using site As New SPSite(siteUrl)  
                Using web As SPWeb = site.OpenWeb(webUrl)  
                    ' Reference the lists.  
                    Dim taskList As SPList = web.Lists("Tasks")  
                    Dim announcementsList As SPList = web.Lists("Announcements")  
  
                    ' Add an announcement that the feature was deactivated.  
                    Dim listItem As SPListItem = announcementsList.Items.Add()  
                    listItem("Title") = "Deactivated Feature: " & Convert.ToString(properties.Definition.DisplayName)  
                    listItem("Body") = Convert.ToString(properties.Definition.DisplayName) & " was deactivated on: " & DateTime.Now.ToString()  
                    listItem.Update()  
  
                    ' Find the task that the feature receiver added to the Task list when the  
                    ' feature was activated.  
                    Dim qry As New SPQuery()  
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>"  
                    Dim taskItems As SPListItemCollection = taskList.GetItems(qry)  
  
                    For Each taskItem As SPListItem In taskItems  
                        ' Mark the task as complete.  
                        taskItem("PercentComplete") = 1  
                        taskItem("Status") = "Completed"  
                        taskItem.Update()  
                    Next  
                End Using  
  
            End Using  
  
        Catch e As Exception  
            Console.WriteLine("Error: " & e.ToString())  
        End Try  
  
    End Sub  
    ```  
  
    ```csharp  
    public override void FeatureDeactivating(SPFeatureReceiverProperties properties)  
    {  
        // The following line induces an error to demonstrate debugging.  
        // Remove this line later for proper operation.  
        throw new System.InvalidOperationException("A serious error occurred!");   
        try  
        {  
            using (SPSite site = new SPSite(siteUrl))  
            {  
                using (SPWeb web = site.OpenWeb(webUrl))  
                {  
                    // Reference the lists.  
                    SPList taskList = web.Lists["Tasks"];  
                    SPList announcementsList = web.Lists["Announcements"];  
  
                    // Add an announcement that the feature was deactivated.  
                    SPListItem listItem = announcementsList.Items.Add();  
                    listItem["Title"] = "Deactivated Feature: " + properties.Definition.DisplayName;  
                    listItem["Body"] = properties.Definition.DisplayName + " was deactivated on: " + DateTime.Now.ToString();  
                    listItem.Update();  
  
                    // Find the task that the feature receiver added to the Task list when the  
                    // feature was activated.  
                    SPQuery qry = new SPQuery();  
                    qry.Query = "<Where><Contains><FieldRef Name='Title' /><Value Type='Text'>Deactivate</Value></Contains></Where>";  
                    SPListItemCollection taskItems = taskList.GetItems(qry);  
  
                    foreach (SPListItem taskItem in taskItems)  
                    {  
                        // Mark the task as complete.  
                        taskItem["PercentComplete"] = 1;  
                        taskItem["Status"] = "Completed";  
                        taskItem.Update();  
                    }  
                }  
            }  
  
        }  
  
        catch (Exception e)  
        {  
            Console.WriteLine("Error: " + e.ToString());  
        }  
    }  
    ```  
  
##  <a name="BKMK_Test1"></a> Testare il progetto  
 Ora che è stato aggiunto il codice al ricevitore di funzionalità e l'agente di raccolta dati è in esecuzione, distribuire ed eseguire la soluzione SharePoint per verificare che funzioni correttamente.  
  
> [!IMPORTANT]  
>  Per questo esempio, verrà generato un errore nel gestore eventi FeatureDeactivating.  Più avanti in questa procedura dettagliata, si individua questo errore utilizzando il file .iTrace che l'agente di raccolta dati ha creato.  
  
#### Per verificare il progetto  
  
1.  Distribuire la soluzione in SharePoint e aprire il sito di SharePoint in un browser.  
  
     La funzionalità viene attivata automaticamente, determinando l'aggiunta di un annuncio e di un'attività da parte del ricevitore di funzionalità.  
  
2.  Visualizzare il contenuto degli annunci e degli elenchi Attività.  
  
     L'elenco degli annunci dovrebbe avere un nuovo annuncio denominato **Funzionalità attivata: IntelliTraceTest\_Feature1** e l'elenco delle attività dovrebbe avere una nuova attività denominata **Disattiva funzionalità: IntelliTraceTest\_Feature1**.  Se uno di questi elementi è mancante, verificare se la funzionalità in uso.  Se non è attivata, attivarla.  
  
3.  Disattivare la funzionalità effettuando i passaggi seguenti:  
  
    1.  Nel menu **Impostazioni sito** in SharePoint, scegliere **Impostazioni sito**.  
  
    2.  In **Azioni del sito**, scegliere il collegamento **Gestire le funzionalità del sito**.  
  
    3.  Accanto a **IntelliTraceTest Funzionalità1**, scegliere il pulsante **Disattiva**.  
  
    4.  Nella pagina avviso, scegliere il collegamento **Disattiva questa funzionalità**.  
  
     Il gestore eventi di FeatureDeactivating\(\) genera un errore.  
  
##  <a name="BKMK_CollectDiagnosticData"></a> Raccogliere dati IntelliTrace tramite Microsoft Monitoring Agent.  
 Se si installa Microsoft Monitoring Agent nel sistema che sta eseguendo SharePoint, è possibile eseguire il debug di soluzioni SharePoint utilizzando i dati che sono più specifici delle informazioni generiche che restituisce IntelliTrace.  L'agente viene eseguito all'esterno di Visual Studio tramite i cmdlet di PowerShell per acquisire informazioni di debug mentre la soluzione SharePoint viene eseguita.  
  
> [!NOTE]  
>  Le informazioni di configurazione in questa sezione sono specifiche di questo esempio.  Per ulteriori informazioni sulle altre opzioni di configurazione, vedere [Uso dell'agente di raccolta autonomo IntelliTrace](../debugger/using-the-intellitrace-stand-alone-collector.md) .  
  
1.  Sul computer che esegue SharePoint, [installare Microsoft Monitoring Agent e avviarlo per monitorare la soluzione](../debugger/using-the-intellitrace-stand-alone-collector.md).  
  
2.  Disattivare la funzionalità:  
  
    1.  Nel menu **Impostazioni sito** in SharePoint, scegliere **Impostazioni sito**.  
  
    2.  In **Azioni del sito**, scegliere il collegamento **Gestire le funzionalità del sito**.  
  
    3.  Accanto a **IntelliTraceTest Funzionalità1**, scegliere il pulsante **Disattiva**.  
  
    4.  Nella pagina avviso, scegliere il collegamento **Disattiva questa funzionalità**.  
  
     Si verifica un errore \(in questo caso, a causa dell'errore generato nel gestore eventi di FeatureDeactivating\(\)\).  
  
3.  Nella finestra di PowerShell, eseguire il comando [Stop\-WebApplicationMonitoring](http://go.microsoft.com/fwlink/?LinkID=313687) per creare il file .iTrace, terminare di monitorare e riavviare la soluzione SharePoint.  
  
     **Stop\-WebApplicationMonitoring**  *"\<SharePointSite\>\\\<SharePointAppName\>"*  
  
##  <a name="BKMK_DebugSolution"></a> Eseguire il debug e correggere la soluzione SharePoint  
 Ora è possibile visualizzare il file di log IntelliTrace in Visual Studio per individuare e correggere l'errore nella soluzione SharePoint.  
  
#### Per eseguire il debug e correggere la soluzione SharePoint  
  
1.  Nella cartella \\IntelliTraceLogs, aprire il file .iTrace in Visual Studio.  
  
     Viene visualizzata la pagina **Riepilogo IntelliTrace**.  Poiché l'errore non è stato gestito, una correlazione ID di SharePoint \(un GUID\) viene visualizzata nell'area di eccezione non gestita della sezione **Analisi**.  Scegliere il pulsante **Stack di chiamate** se si desidera visualizzare lo stack di chiamate in cui si è verificato l'errore.  
  
2.  Scegliere il pulsante **Debug eccezione**.  
  
     Se necessario, caricare i file di simboli.  Nella finestra **IntelliTrace**, l'eccezione viene evidenziata come "Thrown: Serious error occurred\!".  
  
     Nella finestra IntelliTrace, scegliere l'eccezione per visualizzare il codice che ha avuto esito negativo.  
  
3.  Correggere l'errore aprendo la soluzione SharePoint e quindi commentando o rimuovendo l'istruzione **throw** all'inizio della procedura FeatureDeactivating\(\).  
  
4.  Ricompilare la soluzione in Visual Studio e quindi ridistribuirla in SharePoint.  
  
5.  Disattivare la funzionalità effettuando i passaggi seguenti:  
  
    1.  Nel menu **Impostazioni sito** in SharePoint, scegliere **Impostazioni sito**.  
  
    2.  In **Azioni del sito**, scegliere il collegamento **Gestire le funzionalità del sito**.  
  
    3.  Accanto a **IntelliTraceTest Funzionalità1**, scegliere il pulsante **Disattiva**.  
  
    4.  Nella pagina avviso, scegliere il collegamento **Disattiva questa funzionalità**.  
  
6.  Aprire l'elenco delle attività e verificare che il valore **Stato** dell'attività Deactivate sia impostato su "Completata" e il relativo valore **% Completata** sia 100%.  
  
     Il codice verrà eseguito correttamente.  
  
## Vedere anche  
 [Verifica e debug del codice di SharePoint](../sharepoint/verifying-and-debugging-sharepoint-code.md)   
 [Utilizzo di IntelliTrace](../debugger/intellitrace.md)   
 [Procedura dettagliata: verifica del codice di SharePoint tramite unit test](http://msdn.microsoft.com/it-it/3d2c4aaf-3cb5-4825-b21b-f10222abe818)  
  
  