---
title: 'Procedura dettagliata: Salvataggio delle impostazioni utente in una pagina di avvio | Documenti di Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 754b9bf3-8681-4c77-b0a4-09146a4e1d2d
caps.latest.revision: 18
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
ms.sourcegitcommit: c358bf79945b4f4eef5b19c60cad0bd866c175b3
ms.openlocfilehash: 1bf8a313898f9c12312beedb31238fb74e1a56a8
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-saving-user-settings-on-a-start-page"></a>Procedura dettagliata: Salvataggio delle impostazioni utente a una pagina iniziale
È possibile mantenere le impostazioni utente della pagina iniziale. Seguendo questa procedura dettagliata, è possibile creare un controllo per salvare un'impostazione nel Registro di sistema quando l'utente fa clic su un pulsante e recupera quindi che l'impostazione di ogni volta che viene caricata la pagina iniziale. Poiché il modello di progetto pagina iniziale include un controllo utente personalizzabile e il valore predefinito avviare pagina XAML chiama tale controllo, non è necessario modificare la pagina iniziale di se stesso.  
  
 L'archivio di impostazioni che viene creata un'istanza di questa procedura dettagliata è un'istanza di <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>interfaccia, che legge e scrive nel seguente percorso del Registro di sistema quando viene chiamato: HKCU\Software\Microsoft\VisualStudio\14.0\\*NomeRaccolta* </xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore>  
  
 Quando viene eseguito nell'istanza sperimentale di Visual Studio, l'archivio impostazioni legge e scrive in HKCU\Software\Microsoft\VisualStudio\14.0Exp\\*NomeRaccolta.*  
  
 Per ulteriori informazioni su come rendere persistenti le impostazioni, vedere [estensione impostazioni utente e le opzioni](../extensibility/extending-user-settings-and-options.md).  
  
## <a name="prerequisites"></a>Prerequisiti  
  
> [!NOTE]
>  Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
>   
>  È possibile scaricare il modello di progetto pagina iniziale utilizzando **Gestione estensioni**.  
  
## <a name="setting-up-the-project"></a>Impostazione del progetto  
  
#### <a name="to-configure-the-project-for-this-walkthrough"></a>Per configurare il progetto per questa procedura dettagliata  
  
1.  Creare un progetto pagina iniziale, come descritto in [la creazione di una pagina iniziale personalizzata](creating-a-custom-start-page.md). Denominare il progetto **SaveMySettings**.  
  
2.  In **Esplora**, aggiungere i riferimenti ad assembly seguenti al progetto StartPageControl:  
  
    -   EnvDTE  
  
    -   EnvDTE80  
  
    -   Interop  
  
    -   Microsoft.VisualStudio.Shell.Interop.11.0  
  
3.  Aprire MyControl.xaml.  
  
4.  Nel riquadro di XAML, nel primo livello <xref:System.Windows.Controls.UserControl>definizione dell'elemento, aggiungere la seguente dichiarazione di evento dopo le dichiarazioni dello spazio dei nomi.</xref:System.Windows.Controls.UserControl>  
  
    ```  
    Loaded="OnLoaded"  
    ```  
  
5.  Nel riquadro di progettazione, fare clic sull'area principale del controllo e quindi premere CANC.  
  
     Questa operazione rimuove il <xref:System.Windows.Controls.Border>elemento e tutti gli elementi e lascia solo il primo livello <xref:System.Windows.Controls.Grid>elemento.</xref:System.Windows.Controls.Grid> </xref:System.Windows.Controls.Border>  
  
6.  Dal **della casella degli strumenti**, trascinare un <xref:System.Windows.Controls.StackPanel>controllo alla griglia.</xref:System.Windows.Controls.StackPanel>  
  
7.  Trascinare un <xref:System.Windows.Controls.TextBlock>, <xref:System.Windows.Controls.TextBox>e un pulsante per <xref:System.Windows.Controls.StackPanel>.</xref:System.Windows.Controls.StackPanel> </xref:System.Windows.Controls.TextBox> </xref:System.Windows.Controls.TextBlock>  
  
8.  Aggiungere un **X:Name** di attributo per il <xref:System.Windows.Controls.TextBox>e un `Click` evento per il <xref:System.Windows.Controls.Button>, come illustrato nell'esempio seguente.</xref:System.Windows.Controls.Button> </xref:System.Windows.Controls.TextBox>  
  
    ```xml  
    <StackPanel Width="300" HorizontalAlignment="Center" VerticalAlignment="Center">  
        <TextBlock Width="140" FontSize="14">Enter your setting</TextBlock>  
        <TextBox x:Name="txtblk" Margin="0, 5, 0, 10" Width="140" />  
        <Button Click="Button_Click" Width="100">Save My Setting</Button>  
    </StackPanel>  
    ```  
  
## <a name="implementing-the-user-control"></a>Implementazione del controllo utente  
  
#### <a name="to-implement-the-user-control"></a>Per implementare il controllo utente  
  
1.  Nel riquadro di XAML, fare doppio clic su di `Click` attributo il <xref:System.Windows.Controls.Button>elemento e quindi fare clic su **passa al gestore eventi**.</xref:System.Windows.Controls.Button>  
  
     Questo consente di MyControl.xaml.cs e crea un gestore di stub per il `Button_Click` evento.  
  
2.  Aggiungere il codice seguente `using` istruzioni all'inizio del file.  
  
     [!code-cs[StartPageDTE&#11;](../extensibility/codesnippet/CSharp/walkthrough-saving-user-settings-on-a-start-page_1.cs)]  
  
3.  Aggiungere una privata `SettingsStore` proprietà, come illustrato nell'esempio seguente.  
  
    ```c#  
    private IVsWritableSettingsStore _settingsStore = null;  
    private IVsWritableSettingsStore SettingsStore  
    {  
        get  
        {  
            if (_settingsStore == null)  
            {  
                // Get a reference to the DTE from the DataContext.   
                var typeDescriptor = DataContext as ICustomTypeDescriptor;  
                var propertyCollection = typeDescriptor.GetProperties();  
                var dte = propertyCollection.Find("DTE", false).GetValue(  
                    DataContext) as DTE2;  
  
                // Get the settings manager from the DTE.   
                var serviceProvider = new ServiceProvider(  
                    (Microsoft.VisualStudio.OLE.Interop.IServiceProvider)dte);  
                var settingsManager = serviceProvider.GetService(  
                    typeof(SVsSettingsManager)) as IVsSettingsManager;  
  
                // Write the user settings to _settingsStore.  
                settingsManager.GetWritableSettingsStore(  
                    (uint)__VsSettingsScope.SettingsScope_UserSettings,  
                    out _settingsStore);  
            }  
            return _settingsStore;  
        }  
    }  
    ```  
  
     Questa proprietà ottiene innanzitutto un riferimento a di <xref:EnvDTE80.DTE2>interfaccia, che contiene il modello di oggetto di automazione dal <xref:System.Windows.FrameworkElement.DataContext%2A>del controllo utente e quindi viene utilizzato l'oggetto DTE per ottenere un'istanza del <xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.IVsSettingsManager> </xref:System.Windows.FrameworkElement.DataContext%2A> </xref:EnvDTE80.DTE2> Tale istanza viene quindi utilizzato per restituire le impostazioni utente correnti.  
  
4.  Compilare il `Button_Click` evento come indicato di seguito.  
  
    ```c#  
    private void Button_Click(object sender, RoutedEventArgs e)  
    {  
        int exists = 0;  
        SettingsStore.CollectionExists("MySettings", out exists);  
        if (exists != 1)  
        {  
            SettingsStore.CreateCollection("MySettings");  
        }  
        SettingsStore.SetString("MySettings", "MySetting", txtblk.Text);  
    }  
    ```  
  
     Scrive il contenuto della casella di testo a un campo "MySetting" in una raccolta di "MySettings" nel Registro di sistema. Se la raccolta non esiste, viene creato.  
  
5.  Aggiungere il seguente gestore per il `OnLoaded` eventi del controllo utente.  
  
    ```c#  
    private void OnLoaded(Object sender, RoutedEventArgs e)  
    {  
        string value;  
        SettingsStore.GetStringOrDefault(  
            "MySettings", "MySetting", "", out value);  
        txtblk.Text = value;  
    }  
    ```  
  
     Questo imposta il testo della casella di testo per il valore corrente di "MySetting".  
  
6.  Compilare il controllo utente.  
  
7.  In **Esplora**, aprire source.extension.vsixmanifest.  
  
8.  Nell'editor del manifesto, impostare **nome prodotto** a **Salva pagina di avvio impostazioni personali**.  
  
     Questo imposta il nome della pagina iniziale come verrà visualizzato nel **Personalizza pagina iniziale** nell'elenco di **opzioni** la finestra di dialogo.  
  
9. Compilare StartPage.  
  
## <a name="testing-the-control"></a>Test del controllo  
  
#### <a name="to-test-the-user-control"></a>Per testare il controllo utente  
  
1.  Premere F5.  
  
     Apre l'istanza sperimentale di Visual Studio.  
  
2.  Nell'istanza sperimentale, nel **strumenti** menu, fare clic su **opzioni**.  
  
3.  Nel **ambiente** nodo, fare clic su **avvio**, quindi il **Personalizza pagina iniziale** elenco, selezionare **[estensione installato] Salva My impostazioni pagina iniziale**.  
  
     Fare clic su **OK**.  
  
4.  Chiudere la pagina iniziale se è aperto, quindi sui **visualizzazione** menu, fare clic su **pagina iniziale**.  
  
5.  Nella pagina iniziale, fare clic su di **MyControl** scheda.  
  
6.  Nella casella di testo, digitare **Cat**, quindi fare clic su **salvare impostazione My**.  
  
7.  Chiudere la pagina iniziale e quindi aprirlo nuovamente.  
  
     La parola "Cat" deve essere visualizzato nella casella di testo.  
  
8.  Sostituire la parola "Cat" con la parola "Dog". Non fare clic sul pulsante.  
  
9. Chiudere la pagina iniziale e quindi aprirlo nuovamente.  
  
     La parola "Dog" deve essere visualizzata nella casella di testo, anche se l'impostazione non è stato salvato. Ciò accade perché Visual Studio mantiene le finestre degli strumenti in memoria, anche qualora siano chiusi, fino alla chiusura di Visual Studio stesso.  
  
10. Chiudere l'istanza sperimentale di Visual Studio.  
  
11. Premere F5 per aprire nuovamente l'istanza sperimentale.  
  
12. La parola "Cat" deve essere visualizzato nella casella di testo.  
  
## <a name="next-steps"></a>Passaggi successivi  
 È possibile modificare il controllo utente per salvare e recuperare un numero qualsiasi di impostazioni personalizzate utilizzando valori diversi da gestori eventi differenti per ottenere e impostare il `SettingsStore` proprietà. Come utilizzare un diverso `propertyName` parametro per ogni chiamata a <xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>, i valori non sovrascrivono tra loro nel Registro di sistema.</xref:Microsoft.VisualStudio.Shell.Interop.IVsWritableSettingsStore.SetString%2A>  
  
## <a name="see-also"></a>Vedere anche  
 <xref:EnvDTE80.DTE2?displayProperty=fullName></xref:EnvDTE80.DTE2?displayProperty=fullName>     
 [Aggiunta di comandi di Visual Studio a una pagina iniziale](../extensibility/adding-visual-studio-commands-to-a-start-page.md)
