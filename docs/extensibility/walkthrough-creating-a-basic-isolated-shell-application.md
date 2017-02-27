---
title: "Procedura dettagliata: Creazione di un&#39;applicazione di base Shell isolata | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio shell, procedure dettagliate"
  - "Shell [Visual Studio], procedure dettagliate"
  - "applicazioni basate su shell isolate procedure dettagliate [Visual Studio]"
ms.assetid: 8b12e223-aae3-4c23-813d-ede1125f5f69
caps.latest.revision: 54
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 54
---
# Procedura dettagliata: Creazione di un&#39;applicazione di base Shell isolata
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Questa procedura dettagliata viene illustrato come creare una soluzione shell isolata, personalizzare la finestra informazioni su strumento e creare un programma di installazione che viene installata la shell isolata.  
  
## Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per altre informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Per distribuire la shell isolata, è inoltre necessario utilizzare Visual Studio Shell \(Isolated\) Redistributable Package.  
  
## Creazione di una soluzione Shell isolata  
 In questa sezione viene illustrato come utilizzare il modello di progetto Visual Studio Shell isolata per creare una soluzione shell isolata. La soluzione contiene progetti seguenti:  
  
-   Il *SolutionName*. Progetto AboutBoxPackage, che consente di personalizzare l'aspetto degli argomenti della Guida\/finestra informazioni su.  
  
-   Il progetto ShellExtensionsVSIX, che contiene il file source.extension.vsixmanifest che definisce i diversi componenti dell'applicazione shell isolata.  
  
-   Il *SolutionName* progetto, che genera il file eseguibile che richiama l'applicazione shell isolata. Questo progetto contiene la cartella di personalizzazione della Shell, che consente di personalizzare l'aspetto e comportamento dell'applicazione shell isolata.  
  
-   Il *SolutionName* progetto dell'interfaccia utente, che genera un assembly satellite che definisce i comandi di menu attiva e stringhe localizzabili.  
  
#### Per creare una soluzione di base shell isolata  
  
1.  Aprire Visual Studio e creare un nuovo progetto.  
  
2.  Nel **Nuovo progetto** finestra, espandere **altri tipi di progetto** e quindi **estendibilità**. Selezionare il **Visual Studio Shell isolata** modello di progetto.  
  
3.  Denominare il progetto `MyVSShellStub` e specificare un percorso. Assicurarsi che **Crea directory per soluzione** è selezionata e quindi fare clic su **OK**.  
  
     Verrà visualizzata la nuova soluzione **Esplora**.  
  
4.  Compilare la soluzione e avviare il debug dell'applicazione shell isolata.  
  
     Visual Studio shell isolata viene visualizzata. Legge la barra del titolo **MyVSShellStub**. L'icona della barra del titolo viene generato da \\MyVSShellStub\\Resource Files\\ApplicationIcon.ico.  
  
## Personalizzare il nome dell'applicazione e l'icona  
 Si consiglia di personalizzare l'applicazione utilizzando il nome dell'azienda e del logo nella barra del titolo. La procedura seguente viene illustrato come modificare il nome e l'icona che vengono visualizzati nella barra del titolo dell'applicazione personalizzata modificando il file di definizione del pacchetto, MyVSShellStub.Application.pkgdef.  
  
#### Per personalizzare il nome dell'applicazione e l'icona  
  
1.  Nel progetto MyVSShellStub aprire \\Shell Customization\\MyVSShellStub.Application.pkgdef.  
  
2.  Modifica il `AppName` elemento **"AppName" \= "Fabrikam musica Editor"**  
  
3.  Per modificare l'icona dell'applicazione, copiare un'icona diversa nella directory \\MyVSShellStub\\MyVSShellStub\\MyVSShellStub\\. Rinominare il file esistente ApplicationIcon.ico ApplicationIcon1.ico. Rinominare il nuovo file ApplicationIcon.ico.  
  
4.  Compilare la soluzione e avviare il debug. Verrà visualizzata la shell isolata IDE. La barra del titolo è la nuova icona accanto alle parole **Fabrikam musica Editor**.  
  
## Personalizzazione della pagina della home page del Browser Web  
 In questa sezione viene illustrato come modificare la home page predefinita di **Browser Web** finestra modificando il file di definizione del pacchetto.  
  
#### Per personalizzare la home page del Browser Web predefinito  
  
1.  Nel file MyVSShellStub.Application.pkgdef, modificare il `DefaultHomePage` valore dell'elemento a "http:\/\/www.microsoft.com".  
  
2.  Ricompilare il progetto MyVSShellStub.  
  
3.  Compilare la soluzione e avviare il debug.  
  
4.  In **Vista o altre finestre**, fare clic su **Browser Web**. Il **Browser Web** finestra consente di visualizzare la home page di Microsoft Corporation.  
  
## Rimuovere il comando di stampa  
 Il file vsct in un progetto dell'interfaccia utente shell isolata è costituito da un insieme di dichiarazioni del modulo di `<Define name=No_`*elemento*`>`, dove *elemento* è uno dei comandi e menu di Visual Studio standard.  
  
 Se una dichiarazione è rimosso, il menu o il comando viene escluso dalla shell isolata. Al contrario, se è impostata come commento una dichiarazione, il menu o il comando è incluso nella shell isolata.  
  
 Nei passaggi seguenti, si rimuove il commento comando Stampa del file vsct.  
  
#### Per rimuovere il comando di stampa  
  
1.  Verificare che il **Stampa** comando viene visualizzato di **File** menu nell'applicazione shell isolata.  
  
2.  Nel progetto MyVSShellStubUI aprire \\Resource Files\\MyVSShellStubUI.vsct per la modifica.  
  
3.  Rimuovere questa riga:  
  
    ```  
    <!-- <Define name="No_PrintChildrenCommand"/> -->  
    ```  
  
4.  Consente di rimuovere il comando di stampa.  
  
5.  Avviare il debug dell'applicazione shell isolata. Verificare che il **File \/ stampa** comando non è più presente.  
  
## Rimozione di funzionalità da Shell isolata  
 È possibile rimuovere alcuni dei pacchetti che vengono caricati con Visual Studio modificando il file .pkgundef se non si desidera queste funzionalità nell'applicazione shell isolata personalizzata. Specificare il pacchetto in una delle sottochiavi della chiave del Registro di sistema \\Packages $ $RootKey.  
  
> [!NOTE]
>  Per trovare le funzionalità di GUID di Visual Studio, vedere [GUID del pacchetto di funzionalità di Visual Studio](../extensibility/package-guids-of-visual-studio-features.md).  
  
 La procedura seguente viene illustrato come rimuovere il codice XML editor dalla shell isolata.  
  
#### Per rimuovere l'editor XML  
  
1.  Aprire il file MyVSShellStub.pkgundef nella cartella del progetto MyVSShellStub personalizzazione della Shell.  
  
2.  Rimuovere il commento la riga seguente:  
  
     \[$RootKey \\Packages\\$ {87569308\-4813\-40a0\-9cd0\-d7a30838ca3f}\]  
  
3.  Ricompilare la soluzione e avviare il debug la shell isolata. Aprire un file XML, ad esempio, \\MyVSShellStub\\MyVSShellStub\\MyVSShellStubUI\\MyVSShellStubUI.vsct. Verificare che le parole chiave XML nel file non sono colorate e tale digitando "\<" su una riga non viene visualizzata la descrizione comandi XML.  
  
## Personalizzare la Guida in linea\/finestra informazioni su  
 È possibile personalizzare la Guida in linea\/sulla casella che viene creato come parte del modello di progetto shell isolata.  
  
#### Per personalizzare il nome della società  
  
1.  Il nome della società, le informazioni sul copyright, versione del prodotto e descrizione del prodotto si trovano nel progetto MyVSShellStub.AboutBoxPackage nel file \\Properties\\AssemblyInfo.cs. Aprire il file.  
  
2.  Modifica il `AssemblyCompany` valore **Fabrikam**, la `AssemblyProduct` e `AssemblyTitle` valori **Fabrikam musica Editor**, e `AssemblyCopyright` valore **Copyright © 2015 Fabrikam**:  
  
    ```  
    [assembly: AssemblyTitle("Fabrikam Music Editor")] [assembly: AssemblyDescription("")] [assembly: AssemblyConfiguration("")] [assembly: AssemblyCompany("Fabrikam")] [assembly: AssemblyProduct("Fabrikam Music Editor")] [assembly: AssemblyCopyright("Copyright © Fabrikam 2015")] [assembly: AssemblyCompany("Fabrikam")] [assembly: AssemblyProduct("Fabrikam Music Editor ")] [assembly: AssemblyCopyright("Copyright © Fabrikam 2015”)]  
    ```  
  
3.  Per aggiungere una descrizione del prodotto, modificare il `AssemblyDescription` valore **la descrizione dell'editor di musica di Fabrikam.**:  
  
    ```  
    [assembly: AssemblyDescription("The description of Fabrikam Music editor.”)]  
    ```  
  
4.  Avviare il debug e nell'applicazione di shell isolata, aprire il **Guida informazioni su** casella. Dovrebbe essere stringhe modificate. Il titolo della Guida\/sulla casella equivale il `AssemblyTitle` valore nel file AssemblyInfo.cs.  
  
5.  Le proprietà del **informazioni su** casella vengono trovati nel file MyVSShellStub.AboutBoxPackage\\AboutBox.xaml. Per modificare la larghezza della Guida\/sulla casella, passare al `AboutDialogStyle` bloccare e impostare il `Width` proprietà 200:  
  
    ```  
    <Style x:Key="AboutDialogStyle" TargetType="Window"> <Setter Property="Height" Value="Auto" /> <Setter Property="Width" Value="200" /> <Setter Property="ShowInTaskbar" Value="False" /> <Setter Property="ResizeMode" Value="NoResize" /> <Setter Property="WindowStyle" Value="SingleBorderWindow" /> <Setter Property="SizeToContent" Value="Height" /> </Style>  
    ```  
  
6.  Ricompilare la soluzione e avviare il debug la shell isolata. La Guida in linea\/sulla casella deve essere circa quadrato.  
  
## Prima di distribuire l'applicazione Shell isolata  
 Può essere installata l'applicazione shell isolata in qualsiasi computer con Visual Studio Shell \(Isolated\) Redistributable Package. Per ulteriori informazioni sul pacchetto ridistribuibile, vedere il [download di Visual Studio Extensibility](http://go.microsoft.com/fwlink/?LinkID=119298) sito Web.  
  
## Distribuzione dell'applicazione Shell isolata  
 Distribuire l'applicazione shell isolata in un computer di destinazione creando un progetto di installazione. È necessario specificare queste operazioni:  
  
-   Il layout delle cartelle e file nel computer di destinazione.  
  
-   Le condizioni di avvio che garantiscano che .NET Framework e Visual Studio shell runtime vengono installate nel computer di destinazione.  
  
 Nella procedura seguente è necessario installare InstallShield Limited Edition nel computer.  
  
#### Per creare il progetto di installazione  
  
1.  In **Esplora**, pulsante destro del mouse sul nodo della soluzione e quindi fare clic su **Aggiungi nuovo progetto**.  
  
2.  Nel **Nuovo progetto** finestra di dialogo espandere **altri tipi di progetto** e quindi selezionare **installazione e distribuzione**. Selezionare il modello di InstallShield. Denominare il nuovo progetto `MySetup` e quindi fare clic su **OK**.  
  
3.  Se InstallShield Limited Edition è già installato, andare al passaggio successivo.  
  
     Se InstallShield Limited Edition non è già installato, verrà visualizzata la pagina di download di InstallShield. Seguire le istruzioni per scaricare e installare il prodotto, scegliere la versione di InstallShield compatibile con la versione di Visual Studio. È necessario decidere se si desidera registrare l'installazione di InstallShield o utilizzarlo come una versione di valutazione. Dopo aver completato l'installazione, è necessario riavviare Visual Studio.  
  
    > [!IMPORTANT]
    >  Prima di creare un progetto InstallShield, è necessario avviare Visual Studio come amministratore. Se in caso contrario, si verificherà un errore quando si compila il progetto.  
  
 Passaggi successivi viene illustrato come configurare il progetto di installazione.  
  
> [!IMPORTANT]
>  Assicurarsi di avere creato la configurazione di rilascio del progetto shell isolata almeno una volta prima di configurare il progetto di installazione.  
  
#### Per configurare il progetto di installazione  
  
1.  Nel **Esplora**, sotto il **MySetup** del progetto, scegliere **Project Assistant**. Nella riga inferiore del **Project Assistant** finestra, scegliere **informazioni sull'applicazione**. Immettere **Fabrikam** come nome della società e **Fabrikam musica Editor** come il nome dell'applicazione. Scegliere la freccia avanti nella parte inferiore destra del **Project Assistant**.  
  
2.  Selezionare **Sì** in **l'applicazione necessita di qualsiasi software da installare nel computer?** e quindi selezionare **pacchetto completo di Microsoft .NET Framework 4.5**.  
  
3.  Scegliere il **file dell'applicazione** pulsante nella parte inferiore della finestra e verificare che il **Fabrikam musica Editor** viene selezionata la cartella.  
  
4.  Scegliere il **aggiungere file** pulsante. Nel **aggiungere file** finestra di dialogo, aggiungere i file seguenti dal **MyVSShellStub\\Release** cartella:  
  
    1.  MyVSShellStub.exe.config  
  
    2.  DebuggerProxy.dll  
  
    3.  DebuggerProxy.dll.manifest  
  
    4.  MyVSShellStub.pkgdef  
  
    5.  MyVSShellStub.pkgundef  
  
    6.  MyVSShellStub.winprf  
  
    7.  Splash.bmp  
  
5.  Fare clic su di **Aggiungi output progetto** pulsante e aggiungere **MyVSShellStub\/primario Output**. Fare clic su **OK**.  
  
6.  Nel riquadro a sinistra, sotto **Computer di destinazione**, fare doppio clic su di **Fabrikam musica Editor \[INSTALLDIR\]** nodo e aggiungere un **nuova cartella** denominato **estensioni**.  
  
7.  Fare doppio clic su di **estensioni** nodo nel riquadro a sinistra e aggiungere una nuova cartella denominata **applicazione**.  
  
8.  Selezionare il **applicazione** cartella, scegliere il **Aggiungi output progetto** pulsante, quindi selezionare l'output primario dal progetto MyVSShellStub.AboutBoxPackage.  
  
9. Fare clic su di **aggiungere file** pulsante e aggiungere i seguenti file dalla cartella \\MyVSShellStub\\Release\\Extensions\\Application\\:  
  
    -   MyVSShellStub.AboutBoxPackage.pkgdef  
  
    -   MyVSShellStub.Application.pkgdef  
  
10. Fare doppio clic su di **Fabrikam musica Editor \[INSTALLDIR\]** nodo nel riquadro a sinistra e aggiungere una nuova cartella denominata **1033**.  
  
11. Selezionare la cartella 1033, quindi scegliere il **Aggiungi output progetto** pulsante e selezionare l'output primario dal progetto MyVSShellStubUI.  
  
12. Spostare il **i collegamenti alle applicazioni** finestra.  
  
13. Fare clic su **New** per creare un collegamento e selezionare **\[ProgramFilesFolder\] \\Fabrikam\\Fabrikam Music Editor\\MyVSShellStub.Primary Output**.  
  
14. Spostare il **domanda per l'installazione** riquadro.  
  
15. Impostare tutti gli elementi **No**.  
  
16. In **Esplora**, nel progetto MySetup aprire **definire requisiti di installazione e le azioni \\ requisiti**. Il **requisiti** verrà visualizzata la finestra.  
  
17. Fare clic **requisiti Software di sistema** e selezionare **Crea nuova condizione di avvio**. Il **System ricerca guidata** viene visualizzata.  
  
18. Nel **ciò che si desidera trovare?** riquadro, scegliere **voce del Registro di sistema** nell'elenco a discesa fare clic su **Avanti**.  
  
19. Nel **come si desidera cercare l'elemento?** selezionare **HKEY\_LOCAL\_MACHINE** come radice del Registro di sistema. Immettere **SOFTWARE\\Wow6432Node\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell** per sistemi a 64 bit o **SOFTWARE\\Microsoft\\DevDiv\\vs\\Servicing\\14.0\\isoshell** per sistemi a 32 bit e immettere **installare** come valore del Registro di sistema. Scegliere **Avanti**.  
  
20. Nel **ciò che si desidera eseguire con il valore?** riquadro immettere **questo prodotto richiede Visual Studio 2015 isolato Shell Redistributable da installare.** come il testo visualizzato e fare clic su **Fine**.  
  
21. Ricompilare la soluzione shell isolata per creare il progetto di installazione.  
  
     È possibile trovare il file setup.exe nella cartella seguente:  
  
     \\MyVSShellStub\\MySetup\\MySetup\\Express\\SingleImage\\DiskImages\\DISK1  
  
## Test del programma di installazione  
 Per testare il programma di installazione, copiare il file setup.exe in un computer diverso ed eseguire il file eseguibile di installazione. Dovrebbe essere possibile eseguire l'applicazione shell isolata.