---
title: "How to: Publish a Project That Has a Specific Locale | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-deployment"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "publishing, localized projects"
  - "locales, publishing for"
  - "deploying applications [ClickOnce], localized projects"
  - "locales, deploying for"
  - "publishing localized projects"
  - "macros, deploying with"
  - "macros, publishing with"
ms.assetid: 7c4cd83a-f985-4c85-9022-fadb5dbd2b39
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# How to: Publish a Project That Has a Specific Locale
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Accade spesso che un'applicazione contenga componenti con impostazioni locali diverse.  In questi casi si crea una soluzione con più progetti, che vengono poi pubblicati con impostazioni locali differenti.  Questa procedura illustra come usare una macro per pubblicare il primo progetto in una soluzione con le impostazioni locali 'en'.  Se si vuole provare la procedura con impostazioni locali diverse da 'en', impostare `localeString` nella macro in modo che corrisponda alle impostazioni locali in uso \(ad esempio, 'de' o 'de\-DE'\).  
  
> [!NOTE]
>  Quando si usa questa macro, il percorso di pubblicazione deve essere una condivisione UNC \(Universal Naming Convention\) o un URL valido.  È anche necessario installare Internet Information Services \(IIS\) nel computer.  Per installare IIS, fare clic sul menu **Start**, quindi scegliere **Panello di controllo**.  Fare doppio clic su **Installazione applicazioni**.  In **Installazione applicazioni** fare clic su **Installazione componenti di Windows**.  In **Aggiunta guidata componenti di Windows** selezionare la casella di controllo **Internet Information Services \(IIS\)** nell'elenco **Componenti**.  Fare clic su **Fine** per chiudere la procedura guidata.  
  
### Per creare la macro di pubblicazione  
  
1.  Per aprire Esplora macro, scegliere **Macro** dal menu **Strumenti** e quindi fare clic su **Esplora macro**.  
  
2.  Creare un nuovo modulo macro.  In Esplora macro selezionare **MyMacros**.  Scegliere **Macro** dal menu **Strumenti** e quindi fare clic su **Nuovo modulo macro**.  Denominare il modulo PublishSpecificCulture.  
  
3.  In Esplora macro espandere il nodo **MyMacros**, quindi fare doppio clic sul modulo **PublishAllProjects** per aprirlo. In alternativa, scegliere **Macro** dal menu **Strumenti** e fare clic su **IDE macro**.  
  
4.  In IDE macro aggiungere il codice seguente al modulo, dopo le istruzioni `Import`:  
  
    ```vb#  
    Module PublishSpecificCulture  
        Sub PublishProjectFirstProjectWithEnLocale()  
            ' Note: You should publish projects by using the IDE at least once  
            ' before you use this macro. Items such as the certficate and the   
            ' security zone must be set.  
            Dim localeString As String = "en"  
  
            ' Get first project.  
            Dim proj As Project = DTE.Solution.Projects.Item(1)  
            Dim publishProperties As Object = proj.Properties.Item("Publish").Value  
  
            ' GenerateManifests and SignManifests must always be set to  
            ' True for publishing to work.   
            proj.Properties.Item("GenerateManifests").Value = True  
            proj.Properties.Item("SignManifests").Value = True  
  
            'Set the publish language.  
            'This will set the deployment language and pick up all   
            ' en resource dlls:  
            Dim originalTargetCulture As String = _  
                publishProperties.Item("TargetCulture").Value  
            publishProperties.Item("TargetCulture").Value = localeString  
  
            'Append 'en' to end of publish, install, and update URLs if needed:  
            Dim originalPublishUrl As String = _  
                publishProperties.Item("PublishUrl").Value  
            Dim originalInstallUrl As String = _  
                publishProperties.Item("InstallUrl").Value  
            Dim originalUpdateUrl As String = _  
                publishProperties.Item("UpdateUrl").Value  
            publishProperties.Item("PublishUrl").Value = _  
                AppendStringToUrl(localeString, New Uri(originalPublishUrl))  
            If originalInstallUrl <> String.Empty Then  
                publishProperties.Item("InstallUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalInstallUrl))  
            End If  
            If originalUpdateUrl <> String.Empty Then  
                publishProperties.Item("UpdateUrl").Value = _  
                    AppendStringToUrl(localeString, New Uri(originalUpdateUrl))  
            End If  
            proj.Save()  
  
            Dim slnbld2 As SolutionBuild2 = _  
                CType(DTE.Solution.SolutionBuild, SolutionBuild2)  
            slnbld2.Clean(True)  
  
            slnbld2.BuildProject( _  
            proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
            proj.UniqueName, True)  
  
            ' Only publish if build is successful.  
            If slnbld2.LastBuildInfo <> 0 Then  
                MsgBox("Build failed for " & proj.UniqueName)  
            Else  
                slnbld2.PublishProject( _  
                proj.ConfigurationManager.ActiveConfiguration.ConfigurationName, _  
                proj.UniqueName, True)  
                If slnbld2.LastPublishInfo = 0 Then  
                    MsgBox("Publish succeeded for " & proj.UniqueName _  
                    & vbCrLf & "." _  
                    & " Publish Language was '" & localeString & "'.")  
                Else  
                    MsgBox("Publish failed for " & proj.UniqueName)  
                End If  
            End If  
  
            ' Return URLs and target culture to their previous state.  
            publishProperties.Item("PublishUrl").Value = originalPublishUrl  
            publishProperties.Item("InstallUrl").Value = originalInstallUrl  
            publishProperties.Item("UpdateUrl").Value = originalUpdateUrl  
            publishProperties.Item("TargetCulture").Value = originalTargetCulture  
            proj.Save()  
        End Sub  
  
        Private Function AppendStringToUrl(ByVal str As String, _  
        ByVal baseUri As Uri) As String  
            Dim returnValue As String = baseUri.OriginalString  
            If baseUri.IsFile OrElse baseUri.IsUnc Then  
                returnValue = IO.Path.Combine(baseUri.OriginalString, str)  
            Else  
                If Not baseUri.ToString.EndsWith("/") Then  
                    returnValue = baseUri.OriginalString & "/" & str  
                Else  
                    returnValue = baseUri.OriginalString & str  
                End If  
            End If  
            Return returnValue  
        End Function  
    End Module  
    ```  
  
5.  Chiudere IDE macro.  La stato attivo ritornerà su Visual Studio.  
  
### Per pubblicare un progetto per impostazioni locali specifiche  
  
1.  Per creare un progetto Applicazione Windows di Visual Basic, scegliere **Nuovo** dal menu **File** e quindi fare clic su **Progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** selezionare **Applicazione Windows** nel nodo **Visual Basic**.  Denominare il progetto PublishLocales.  
  
3.  Fare clic su Form1.  Nella finestra **Proprietà**, in **Progettazione** , modificare la proprietà **Lingua** da**\(Predefinito\)** a **Inglese**.  Impostare la proprietà **Text** del form su MyForm.  
  
     Notare che i file DDL delle risorse localizzate non vengono creati finché non sono necessari.  Vengono creati, ad esempio, quando si modifica il testo del form o uno dei relativi controlli dopo avere specificato le nuove impostazioni locali.  
  
4.  Pubblicare il progetto PublishLocales usando l'IDE di Visual Studio.  
  
     In **Esplora soluzioni** selezionare PublishLocales.  Scegliere **Proprietà** dal menu **Progetto**.  In Progettazione progetti, nella pagina **Pubblica** specificare il percorso di pubblicazione http:\/\/localhost\/PublishLocales, quindi fare clic su **Pubblica**.  
  
     Chiudere la pagina Web di pubblicazione non appena viene visualizzata.  In questa fase non è necessario installare il progetto, ma solo pubblicarlo  
  
5.  Pubblicare di nuovo il progetto PublishLocales richiamando la macro nella finestra del prompt dei comandi di Visual Studio.  Per visualizzare la finestra del prompt dei comandi, scegliere **Altre finestre** dal menu **Visualizza** e quindi fare clic su **Finestra di comando** oppure premere CTRL\+ALT\+A.  Nella finestra del prompt dei comandi digitare `macro`. La funzionalità Completamento automatico fornirà un elenco delle macro disponibili.  Selezionare la macro seguente e premere INVIO:  
  
     `Macros.MyMacros.PublishSpecificCulture.PublishProjectFirstProjectWithEnLocale`  
  
6.  Dopo il completamento del processo di pubblicazione verrà generato il messaggio "Publish succeeded for PublishLocales\\PublishLocales.vbproj.  Publish language was 'en'." Fare clic su **OK** nella finestra di messaggio.  Quando viene visualizzata la pagina Web di pubblicazione, fare clic su **Installa**.  
  
7.  Controllare il percorso C:\\Inetpub\\wwwroot\\PublishLocales\\en.  Dovrebbero essere presenti i file installati, tra cui i manifesti, setup.exe e il file della pagina Web di pubblicazione, oltre alla DLL delle risorse localizzate.  Per impostazione predefinita, ClickOnce aggiunge ai file EXE e DLL l'estensione deploy, che può essere rimossa dopo la distribuzione.  
  
## Vedere anche  
 [Publishing ClickOnce Applications](../deployment/publishing-clickonce-applications.md)   
 [Macros Development Environment](http://msdn.microsoft.com/it-it/d23105d8-34fe-4ad9-8278-fae2c660aeac)   
 [Macro Explorer Window](http://msdn.microsoft.com/it-it/762169e6-f83f-44b4-bffa-d0f107cae9a3)   
 [How to: Edit and Programmatically Create Macros](http://msdn.microsoft.com/it-it/6716f820-1feb-48ad-a718-27eb6b473c5a)