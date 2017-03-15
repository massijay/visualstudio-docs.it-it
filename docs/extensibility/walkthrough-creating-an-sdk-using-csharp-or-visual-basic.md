---
title: 'Procedura dettagliata: Creazione di un SDK tramite c# o Visual Basic | Documenti di Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef96a249-5eef-402a-a8d5-d74cb49239bd
caps.latest.revision: 20
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: c43f3022ba53e67ff510ed63aa419c9f23964a58
ms.openlocfilehash: ce17214ec4bfc49f82ee537d6dee13a471a36ca2
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-an-sdk-using-c-or-visual-basic"></a>Procedura dettagliata: Creazione di un SDK tramite c# o Visual Basic
In questa procedura dettagliata, si apprenderà come creare un semplice SDK libreria matematica usando Visual c# e quindi creare il pacchetto SDK come un Visual Studio Extension (VSIX). È necessario completare le procedure seguenti:  
  
-   [Per creare il componente Windows Runtime SimpleMath](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createClassLibrary)  
  
-   [Per creare il progetto di estensione SimpleMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createVSIX)  
  
-   [Per creare un'applicazione di esempio che utilizza la libreria di classi](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md#createSample)  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="a-namecreateclasslibrarya-to-create-the-simplemath-windows-runtime-component"></a><a name="createClassLibrary"></a>Per creare il componente Windows Runtime SimpleMath  
  
1.  Nella barra dei menu, scegliere **File**, **New**, **nuovo progetto**.  
  
2.  Nell'elenco dei modelli espandere **Visual c#** o **Visual Basic**, scegliere il **Windows Store** nodo, quindi scegliere il **componente Windows Runtime** modello.  
  
3.  Nel **nome** specificare **SimpleMath**, quindi scegliere il **OK** pulsante.  
  
4.  In **Esplora**, aprire il menu di scelta rapida per il **SimpleMath** nodo di progetto e quindi scegliere **proprietà**.  
  
5.  Rinominare **Class1. cs** a **Arithmetic.cs** e aggiornarlo in modo che corrisponda al codice seguente:  
  
     [!code-cs[N.&3; CreatingAnSDKUsingWinRT](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.cs) ] 
     [!code-vb [CreatingAnSDKUsingWinRT n.&3;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_1.vb)]  
  
6.  In **Esplora**, aprire il menu di scelta rapida per il **soluzione 'SimpleMath'** nodo, quindi scegliere **Configuration Manager**.  
  
     Il **Configuration Manager** verrà visualizzata la finestra di dialogo.  
  
7.  Nel **configurazione soluzione attiva** scegliere **versione**.  
  
8.  Nel **configurazione** colonna, verificare che **SimpleMath** riga è impostata su **versione**, quindi scegliere il **Chiudi** pulsante per accettare la modifica.  
  
    > [!IMPORTANT]
    >  il SDK per il componente SimpleMath include solo una configurazione. Questa configurazione deve essere la build di rilascio o le applicazioni che utilizzano il componente non passano la certificazione il[!INCLUDE[win8_appstore_long](../debugger/includes/win8_appstore_long_md.md)].  
  
9. In **Esplora**, aprire il menu di scelta rapida per il **SimpleMath** nodo di progetto, quindi fare clic **Build**.  
  
##  <a name="a-namecreatevsixa-to-create-the-simplemathvsix-extension-project"></a><a name="createVSIX"></a>Per creare il progetto di estensione SimpleMathVSIX  
  
1.  Nel menu di scelta rapida per il **soluzione 'SimpleMath'** nodo, scegliere **Aggiungi**, **nuovo progetto**.  
  
2.  Nell'elenco dei modelli espandere **Visual c#** o **Visual Basic**, scegliere il **estendibilità** nodo, quindi scegliere il **progetto VSIX** modello.  
  
3.  Nel **nome** specificare **SimpleMathVSIX**, quindi scegliere il **OK** pulsante.  
  
4.  In **Esplora**, scegliere il **source.extension.vsixmanifest** elemento.  
  
5.  Nella barra dei menu scegliere **Visualizza**, **Codice**.  
  
6.  Sostituire il codice XML esistente con il codice XML seguente:  
  
     [!code-xml[CreatingAnSDKUsingWinRT n.&1;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_2.xml)]
  
7.  In **Esplora**, scegliere il **SimpleMathVSIX** progetto.  
  
8.  Nella barra dei menu, scegliere **progetto**, **Aggiungi nuovo elemento**.  
  
9. Nell'elenco di **elementi comuni**, espandere **dati**, quindi scegliere **File XML**.  
  
10. Nel **nome** specificare `SDKManifest.xml`, quindi scegliere il **Aggiungi** pulsante.  
  
11. In **Esplora**, aprire il menu di scelta rapida per `SDKManifest.xml`, scegliere **proprietà**e quindi modificare il valore di **Includi in VSIX** proprietà **True**.  
  
12. Sostituisci il contenuto del file con il codice XML riportato di seguito:  

    **LINGUAGGIO C#**
    ```xml
    <FileList
      DisplayName="WinRT Math Library (CS)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="http://www.msdn.microsoft.com/">
    </FileList>
    ```

    **Visual Basic**
    ```xml
    <FileList
      DisplayName="WinRT Math Library (VB)"
      MinVSVersion="11.0"
      TargetFramework=".NETCore,version=v4.5"
      AppliesTo="WindowsAppContainer"
      SupportsMultipleVersions="Error"
      MoreInfo="http://www.msdn.microsoft.com/">
    </FileList>
    ```  
  
13. In **Esplora**, aprire il menu di scelta rapida per il **SimpleMathVSIX** del progetto, scegliere **Aggiungi**, quindi scegliere **nuova cartella**.  
  
14. Rinominare la cartella in `references`.  
  
15. Aprire il menu di scelta rapida per il **riferimenti** cartella, scegliere **Aggiungi**, quindi scegliere **nuova cartella**.  
  
16. Rinominare la sottocartella in `commonconfiguration`, creare una sottocartella all'interno di esso e denominare la sottocartella `neutral`.  
  
17. Ripetere i quattro passaggi precedenti, questa volta rinominato la cartella prima di `redist`.  
  
     Il progetto contiene ora la struttura di cartelle seguente:  
  
    ```
    references\commonconfiguration\neutral  
    redist\commonconfiguration\neutral  
    ```  
  
18. In **Esplora**, aprire il menu di scelta rapida per il **SimpleMath** del progetto, quindi fare clic **Apri cartella in Esplora File**.  
  
19. In **Esplora File**, passare alla cartella bin\Release, aprire il menu di scelta rapida per il file SimpleMath.winmd e quindi scegliere **copia**.  
  
20. In **Esplora**, incollare il file nella cartella references\commonconfiguration\neutral di **SimpleMathVSIX** progetto.  
  
21. Ripetere il passaggio precedente, incollare il file SimpleMath.pri nella cartella redist\commonconfiguration\neutral di **SimpleMathVSIX** progetto.  
  
22. In **Esplora**, scegliere **SimpleMath.winmd**.  
  
23. Nella barra dei menu, scegliere **visualizzazione**, **proprietà** (tastiera: premere il tasto F4).  
  
24. Nel **proprietà** finestra, modifica il **operazione di compilazione** proprietà **contenuto**e quindi modificare il **Includi in VSIX** proprietà **True**.  
  
25. In **Esplora**, ripetere questo processo per **SimpleMath.pri**.  
  
26. In **Esplora**, scegliere il **SimpleMathVSIX** progetto.  
  
27. Nella barra dei menu, scegliere **compilare**, **SimpleMathVSIX Build**.  
  
28. In **Esplora**, aprire il menu di scelta rapida per il **SimpleMathVSIX** del progetto, quindi fare clic **Apri cartella in Esplora File**.  
  
29. In **Esplora File**, passare alla cartella \bin\Release, e quindi eseguire SimpleMathVSIX.vsix per installarlo.  
  
30. Scegliere il **installare** pulsante, attendere il completamento dell'installazione e quindi riavviare Visual Studio.  
  
##  <a name="a-namecreatesamplea-to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Per creare un'applicazione di esempio che utilizza la libreria di classi  
  
1.  Nella barra dei menu, scegliere **File**, **New**, **nuovo progetto**.  
  
2.  Nell'elenco dei modelli espandere **Visual c#** o **Visual Basic**, quindi scegliere il **Windows Store** nodo.  
  
3.  Scegliere il **applicazione vuota** modello, denominare il progetto **ArithmeticUI**, quindi scegliere il **OK** pulsante.  
  
4.  In **Esplora**, aprire il menu di scelta rapida per il **ArithmeticUI** del progetto, quindi fare clic **Aggiungi**, **riferimento**.  
  
5.  Nell'elenco dei tipi di riferimento, espandere **Windows**, quindi scegliere **estensioni**.  
  
6.  Nel riquadro dei dettagli, scegliere il **SDK matematiche semplici** estensione.  
  
     Vengono visualizzate ulteriori informazioni sul SDK. È possibile scegliere di **informazioni** collegamento per aprire http://www.msdn.microsoft.com, come specificato nel file SDKManifest.xml in precedenza in questa procedura dettagliata.  
  
7.  Nel **gestione riferimenti** la finestra di dialogo, selezionare il **SDK matematiche semplici** casella di controllo e quindi scegliere il **OK** pulsante.  
  
8.  Nella barra dei menu, scegliere **visualizzazione**, **Visualizzatore oggetti**.  
  
9. Nel **Sfoglia** scegliere **semplici operazioni matematiche**.  
  
     È ora possibile esplorare novità nel SDK.  
  
10. In **Esplora**, aprire MainPage. XAML e sostituirne il contenuto con il codice XAML seguente:  

    **LINGUAGGIO C#**
    ```xml
    <Page
        x:Class="WinRTMathTestCS.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTestCS"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```
    
    **Visual Basic**
    ```xml
    <Page
        x:Class="WinRTMathTest.MainPage"
        IsTabStop="False"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:local="using:WinRTMathTest"
        xmlns:d="http://schemas.microsoft.com/expression/blend/2008"
        xmlns:mc="http://schemas.openxmlformats.org/markup-compatibility/2006"
        mc:Ignorable="d">

        <Grid Background="{StaticResource ApplicationPageBackgroundThemeBrush}">
            <TextBox x:Name="_firstNumber" HorizontalAlignment="Left" Margin="414,370,0,0" TextWrapping="Wrap" Text="First Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <TextBox x:Name="_secondNumber" HorizontalAlignment="Left" Margin="613,370,0,0" TextWrapping="Wrap" Text="Second Number" VerticalAlignment="Top" Height="32" Width="135" TextAlignment="Center"/>
            <Button Content="+" HorizontalAlignment="Left" Margin="557,301,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="-" HorizontalAlignment="Left" Margin="557,345,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="*" HorizontalAlignment="Left" Margin="557,389,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="/" HorizontalAlignment="Left" Margin="557,433,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnOperatorClick"/>
            <Button Content="=" HorizontalAlignment="Left" Margin="755,367,0,0" VerticalAlignment="Top" Height="39" Width="49" Click="OnResultsClick"/>
            <TextBox x:Name="_result" HorizontalAlignment="Left" Margin="809,370,0,0" TextWrapping="Wrap" Text="Result" VerticalAlignment="Top" Height="32" Width="163" TextAlignment="Center" IsReadOnly="True"/>
        </Grid>
    </Page>
    ```
  
11. Aggiornamento MainPage.xaml.cs affinché corrisponda al codice seguente:  
  
     [!code-cs[N.&2; CreatingAnSDKUsingWinRTDemoApp](../extensibility/codesnippet/CSharp/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.cs) ] 
     [!code-vb [CreatingAnSDKUsingWinRTDemoApp n.&2;](../extensibility/codesnippet/VisualBasic/walkthrough-creating-an-sdk-using-csharp-or-visual-basic_5.vb)]  
  
12. Premere il tasto F5 per eseguire l'app.  
  
13. Nell'app, immettere i due numeri, scegliere un'operazione e quindi scegliere il ** = ** pulsante.  
  
     Viene visualizzato il risultato corretto.  
  
 Aver creato e utilizzato un SDK di estensione.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione di un SDK mediante C++](../extensibility/walkthrough-creating-an-sdk-using-cpp.md)   
 [Procedura dettagliata: Creazione di un SDK tramite JavaScript](http://msdn.microsoft.com/en-us/6195ff56-4a27-45fc-bd29-4b0451225f4b)   
 [Creazione di un Software Development Kit](../extensibility/creating-a-software-development-kit.md)
