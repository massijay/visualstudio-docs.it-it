---
title: Creazione di un Editor di componenti di base e la registrazione di un tipo di File Editor | Documenti di Microsoft&quot;
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], legacy - walkthrough
ms.assetid: 24d2bffd-a35c-46db-8515-fd60b884b7fb
caps.latest.revision: 29
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
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: 7bde276b0d53793f57266c13c5ccf63583f7aacf
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-a-core-editor-and-registering-an-editor-file-type"></a>Procedura dettagliata: Creazione di un Editor di componenti di base e la registrazione di un tipo di File dell'Editor
Questa procedura dettagliata viene illustrato come creare un package VS che inizia il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale quando un file con estensione .myext viene caricato.  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
## <a name="locations-for-the-visual-studio-package-project-template"></a>Per il modello di progetto Package Visual Studio  
 Il modello di progetto di pacchetto di Visual Studio si trova in tre posizioni diverse nella finestra di dialogo **Nuovo progetto** :  
  
1.  Nella sezione relativa all'estendibilità di Visual Basic. Il linguaggio predefinito del progetto è Visual Basic.  
  
2.  Nella sezione relativa all'estendibilità di C#. Il linguaggio predefinito del progetto è C#.  
  
3.  Nella sezione relativa all'estendibilità di altri tipi di progetto. Il linguaggio predefinito del progetto è C++.  
  
### <a name="to-create-the-vspackage"></a>Per creare il package VS  
  
-   Avviare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e creare un [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] VSPackage denominato `MyPackage`, come descritto in [procedura dettagliata: creazione di un comando di Menu package VS](http://msdn.microsoft.com/en-us/d699c149-5d1e-47ff-94c7-e1222af02c32).  
  
### <a name="to-add-the-editor-factory"></a>Per aggiungere il factory editor  
  
1.  Fare doppio clic su di **MyPackage** , scegliere **Aggiungi** e quindi fare clic su **classe**.  
  
2.  Nel **Aggiungi nuovo elemento** finestra di dialogo verificare che il **classe** modello è selezionato, tipo `EditorFactory.cs` per il nome e quindi fare clic su **Aggiungi** per aggiungere la classe al progetto.  
  
     Il file EditorFactory.cs deve essere aperto automaticamente.  
  
3.  Fare riferimento agli assembly seguenti dal codice.  
  
    ```vb#  
    Imports System.Runtime.InteropServices  
    Imports Microsoft.VisualStudio  
    Imports Microsoft.VisualStudio.Shell  
    Imports Microsoft.VisualStudio.Shell.Interop  
    Imports Microsoft.VisualStudio.OLE.Interop  
    Imports Microsoft.VisualStudio.TextManager.Interop  
    Imports IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider  
    ```  
  
    ```c#  
    using System.Runtime.InteropServices;  
    using Microsoft.VisualStudio;  
    using Microsoft.VisualStudio.Shell;  
    using Microsoft.VisualStudio.Shell.Interop;  
    using Microsoft.VisualStudio.OLE.Interop;  
    using Microsoft.VisualStudio.TextManager.Interop;  
    using IOleServiceProvider = Microsoft.VisualStudio.OLE.Interop.IServiceProvider;  
  
    ```  
  
4.  Aggiungere un GUID per il `EditorFactory` classe aggiungendo il `Guid` attributo immediatamente prima della dichiarazione di classe.  
  
     È possibile generare un nuovo GUID utilizzando il programma guidgen.exe il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] comando prompt dei comandi oppure facendo clic su **Crea GUID** sul **strumenti** menu. Il GUID utilizzato qui è solo un esempio; non utilizzarlo nel progetto.  
  
    ```vb#  
    <Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")> _  
    ```  
  
    ```c#  
    [Guid("0eea3187-c5fa-48d4-aa72-b5eecd3b17b1")]   
    ```  
  
5.  Nella definizione della classe, aggiungere due variabili private per contenere il pacchetto padre e un provider di servizi.  
  
    ```vb#  
    Class EditorFactory  
        Private parentPackage As Package  
        Private serviceProvider As IOleServiceProvider  
    ```  
  
    ```c#  
    class EditorFactory  
    {  
        private Package parentPackage;  
        private IOleServiceProvider serviceProvider;  
    }  
  
    ```  
  
6.  Aggiungere un costruttore di classe pubblica che accetta un parametro di tipo <xref:Microsoft.VisualStudio.Shell.Package>:</xref:Microsoft.VisualStudio.Shell.Package>  
  
    ```vb#  
    Public Sub New(ByVal parentPackage As Package)  
        Me.parentPackage = parentPackage  
    End Sub  
    ```  
  
    ```c#  
    public EditorFactory(Package parentPackage)  
    {  
        this.parentPackage = parentPackage;  
    }  
    ```  
  
7.  Modificare il `EditorFactory` classe dichiarazione da cui derivare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>  
  
    ```vb#  
    Class EditorFactory Implements IVsEditorFacto  
    ```  
  
    ```c#  
    class EditorFactory : IVsEditorFactory  
  
    ```  
  
8.  Fare doppio clic su <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>, fare clic su **implementa interfaccia**, quindi fare clic su **implementa interfaccia in modo esplicito**.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>  
  
     Aggiunge i quattro metodi che devono essere implementati nel <xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.IVsEditorFactory>  
  
9. Sostituire il contenuto del metodo `IVsEditorFactory.Close` con il codice riportato di seguito.  
  
    ```vb#  
    Return VSConstants.S_OK  
    ```  
  
    ```c#  
    return VSConstants.S_OK;  
    ```  
  
10. Sostituire il contenuto di `IVsEditorFactory.SetSite` con il codice seguente.  
  
    ```vb#  
    Me.serviceProvider = psp  
    Return VSConstants.S_OK  
    ```  
  
    ```c#  
    this.serviceProvider = psp;  
    return VSConstants.S_OK;  
    ```  
  
11. Sostituire il contenuto del metodo `IVsEditorFactory.MapLogicalView` con il codice riportato di seguito.  
  
    ```vb#  
    Dim retval As Integer = VSConstants.E_NOTIMPL  
    pbstrPhysicalView = Nothing ' We support only one view.  
    If rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer)OrElse _  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary) Then  
        retval = VSConstants.S_OK  
    End If  
    Return retval  
    ```  
  
    ```c#  
    int retval = VSConstants.E_NOTIMPL;  
    pbstrPhysicalView = null;   // We support only one view.  
    if (rguidLogicalView.Equals(VSConstants.LOGVIEWID_Designer) ||  
    rguidLogicalView.Equals(VSConstants.LOGVIEWID_Primary))  
    {  
        retval = VSConstants.S_OK;  
    }  
    return retval;  
    ```  
  
12. Sostituire il contenuto del metodo `IVsEditorFactory.CreateEditorInstance` con il codice riportato di seguito.  
  
    ```vb#  
    Dim retval As Integer = VSConstants.E_FAIL          
  
    ' Initialize these to empty to start with   
    ppunkDocView = IntPtr.Zero  
    ppunkDocData = IntPtr.Zero  
    pbstrEditorCaption = ""  
    pguidCmdUI = Guid.Empty  
    pgrfCDW = 0  
  
    If (grfCreateDoc And (VSConstants.CEF_OPENFILE Or _  
    VSConstants.CEF_SILENT)) = 0 Then  
        Throw New ArgumentException("Only Open or Silent is valid")  
    End If  
    If punkDocDataExisting <> IntPtr.Zero Then  
        Return VSConstants.VS_E_INCOMPATIBLEDOCDATA  
    End If  
  
    ' Instantiate a text buffer of type VsTextBuffer.   
    ' Note: we only need an IUnknown (object) interface for   
    ' this invocation.   
    Dim clsidTextBuffer As Guid = GetType(VsTextBufferClass).GUID  
    Dim iidTextBuffer As Guid = VSConstants.IID_IUnknown  
    Dim pTextBuffer As Object = pTextBuffer = _  
    parentPackage.CreateInstance(clsidTextBuffer, iidTextBuffer, _  
    GetType(Object))  
  
    If Not pTextBuffer Is Nothing Then  
        ' "Site" the text buffer with the service provider we were   
        ' provided.   
        Dim textBufferSite As IObjectWithSite = TryCast(pTextBuffer, _  
        IObjectWithSite)  
        If Not textBufferSite Is Nothing Then  
            textBufferSite.SetSite(Me.serviceProvider)  
        End If  
  
        ' Instantiate a code window of type IVsCodeWindow.   
        Dim clsidCodeWindow As Guid = GetType(VsCodeWindowClass).GUID  
        Dim iidCodeWindow As Guid = GetType(IVsCodeWindow).GUID  
        Dim pCodeWindow As IVsCodeWindow = _  
        CType(Me.parentPackage.CreateInstance(clsidCodeWindow, _  
        iidCodeWindow, GetType(IVsCodeWindow)), IVsCodeWindow)  
        If Not pCodeWindow Is Nothing Then  
            ' Give the text buffer to the code window.   
            ' We are giving up ownership of the text buffer!   
            pCodeWindow.SetBuffer(CType(pTextBuffer, IVsTextLines))  
  
            ' Now tell the caller about all this new stuff   
            ' that has been created.   
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow)  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer)  
  
            ' Specify the command UI to use so keypresses are   
            ' automatically dealt with.   
            pguidCmdUI = VSConstants.GUID_TextEditorFactory  
  
            ' This caption is appended to the filename and   
            ' lets us know our invocation of the core editor   
            ' is up and running.   
            pbstrEditorCaption = " [MyPackage]"  
  
            retval = VSConstants.S_OK  
        End If  
    End If  
    Return retval  
    ```  
  
    ```c#  
    int retval = VSConstants.E_FAIL;  
  
    // Initialize these to empty to start with  
    ppunkDocView       = IntPtr.Zero;  
    ppunkDocData       = IntPtr.Zero;  
    pbstrEditorCaption = "";  
    pguidCmdUI         = Guid.Empty;   
    pgrfCDW            = 0;  
  
    if ((grfCreateDoc & (VSConstants.CEF_OPENFILE |   
          VSConstants.CEF_SILENT)) == 0)  
    {   
        throw new ArgumentException("Only Open or Silent is valid");  
    }  
    if (punkDocDataExisting != IntPtr.Zero)  
    {  
        return VSConstants.VS_E_INCOMPATIBLEDOCDATA;  
    }  
  
    // Instantiate a text buffer of type VsTextBuffer.  
    // Note: we only need an IUnknown (object) interface for   
    // this invocation.  
    Guid clsidTextBuffer = typeof(VsTextBufferClass).GUID;  
    Guid iidTextBuffer   = VSConstants.IID_IUnknown;  
    object pTextBuffer   = pTextBuffer = parentPackage.CreateInstance(  
          ref clsidTextBuffer,  
          ref iidTextBuffer,  
          typeof(object));  
  
    if (pTextBuffer != null)  
    {  
        // "Site" the text buffer with the service provider we were  
        // provided.  
        IObjectWithSite textBufferSite = pTextBuffer as IObjectWithSite;  
        if (textBufferSite != null)  
        {  
            textBufferSite.SetSite(this.serviceProvider);  
        }  
  
        // Instantiate a code window of type IVsCodeWindow.  
        Guid clsidCodeWindow = typeof(VsCodeWindowClass).GUID;  
        Guid iidCodeWindow   = typeof(IVsCodeWindow).GUID;  
        IVsCodeWindow pCodeWindow =  
        (IVsCodeWindow)this.parentPackage.CreateInstance(   
              ref clsidCodeWindow,  
              ref iidCodeWindow,  
              typeof(IVsCodeWindow));  
        if (pCodeWindow != null)  
        {  
            // Give the text buffer to the code window.  
            // We are giving up ownership of the text buffer!  
            pCodeWindow.SetBuffer((IVsTextLines)pTextBuffer);  
  
            // Now tell the caller about all this new stuff   
            // that has been created.  
            ppunkDocView = Marshal.GetIUnknownForObject(pCodeWindow);  
            ppunkDocData = Marshal.GetIUnknownForObject(pTextBuffer);  
  
            // Specify the command UI to use so keypresses are   
            // automatically dealt with.  
            pguidCmdUI = VSConstants.GUID_TextEditorFactory;  
  
            // This caption is appended to the filename and  
            // lets us know our invocation of the core editor   
            // is up and running.  
            pbstrEditorCaption = " [MyPackage]";  
  
            retval = VSConstants.S_OK;  
        }   
    }   
    return retval;   
    ```  
  
13. Compilare il progetto e assicurarsi che non siano presenti errori.  
  
### <a name="to-register-the-editor-factory"></a>Per registrare la factory editor  
  
1.  In **Esplora**, doppio clic sul file resources. resx per aprire la tabella di stringhe, in cui la voce **String1 è** selezionato.  
  
2.  Modificare il nome dell'identificatore di `IDS_EDITORNAME` e il testo **MyPackage Editor.** Questa stringa verrà visualizzata come nome dell'editor.  
  
3.  Aprire il file VSPackage.resx e aggiungere una nuova stringa, impostare il nome su **101** e il valore su `IDS_EDITORNAME`. In questo modo il pacchetto con un ID di risorsa per accedere alla stringa che appena creato.  
  
    > [!NOTE]
    >  Se il file VSPackage.resx contiene un'altra stringa di `name` attributo impostato su **101**, sostituire un altro valore univoco, numeric, qui e nei passaggi seguenti.  
  
4.  In **Esplora**, aprire il file MyPackagePackage.cs.  
  
     Questo è il file del pacchetto principale.  
  
5.  Aggiungere i seguenti attributi utente subito prima di `Guid` attributo.  
  
    ```vb#  
    <ProvideEditorFactoryAttribute(GetType(EditorFactory), 101)> _  
    <ProvideEditorExtensionAttribute(GetType(EditorFactory), _  
          ".myext", 32, NameResourceID:=101 )> _  
    ```  
  
    ```c#  
    [ProvideEditorFactory(typeof(EditorFactory), 101)]  
    [ProvideEditorExtension(typeof(EditorFactory),   
          ".myext", 32, NameResourceID = 101)]   
    ```  
  
     Il <xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>attributo associa l'estensione del file .myext del factory editor in modo che ogni volta che un file di estensione viene caricata, viene richiamata il factory editor.</xref:Microsoft.VisualStudio.Shell.ProvideEditorExtensionAttribute>  
  
6.  Aggiungere una variabile privata per il `MyPackage` , appena prima del costruttore, di classe e assegnarle il tipo `EditorFactory`.  
  
    ```vb#  
    Private editorFactory As EditorFactory  
    ```  
  
    ```c#  
    private EditorFactory editorFactory;  
    ```  
  
7.  Trovare il `Initialize` (metodo) (potrebbe essere necessario aprire il `Package Members` area nascosta) e aggiungere il codice seguente dopo la chiamata a `base.Initialize()`.  
  
    ```vb#  
    'Create our editor factory and register it.   
    Me.editorFactory = New EditorFactory(Me)  
    MyBase.RegisterEditorFactory(Me.editorFactory)  
    ```  
  
    ```c#  
    // Create our editor factory and register it.  
    this.editorFactory = new EditorFactory(this);  
    base.RegisterEditorFactory(this.editorFactory);  
  
    ```  
  
8.  Compilare il programma e assicurarsi che non ci siano errori.  
  
     Questo passaggio registra la factory editor nell'hive del Registro di sistema sperimentale per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Se viene chiesto di sostituire il file Resource. h, fare clic su **OK**.  
  
9. Creare un file di esempio denominato TextFile1.myext.  
  
10. Premere **F5** per aprire un'istanza sperimentale di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].  
  
11. Nell'istanza sperimentale [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]via il **File** dal menu **aprire** e quindi fare clic su **File**.  
  
12. Trovare TextFile1.myext e quindi fare clic su **aprire**.  
  
     Il file deve ora essere caricato.  
  
## <a name="robust-programming"></a>Programmazione efficiente  
 Il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale gestisce un'ampia gamma di tipi di file basato su testo e funziona in stretto contatto con i servizi per linguaggi per fornire un set completo di funzionalità quali l'evidenziazione della sintassi, corrispondenza parentesi graffe e gli elenchi di completamento delle parole e il membro completamento IntelliSense. Se si lavora con i file di testo, è possibile utilizzare l'editor di componenti di base insieme a un servizio di linguaggio personalizzato che supporta i tipi di file specifico.  
  
 Un VSPackage può richiamare il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] editor principale, fornendo una factory editor. Questa factory editor viene utilizzata ogni volta che viene caricato un file che è associato. Se il file fa parte di un progetto, l'editor di componenti di base viene richiamato automaticamente a meno che non viene sottoposto a override per il pacchetto Visual Studio. Tuttavia, se il file viene caricato all'esterno di un progetto, quindi l'editor di componenti di base deve essere esplicitamente richiamato dal pacchetto Visual Studio.  
  
 Per ulteriori informazioni sull'editor di componenti di base, vedere [all'interno di Editor principale](../extensibility/inside-the-core-editor.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Nell'Editor di componenti di base](../extensibility/inside-the-core-editor.md)   
 [Creazione di Editor di componenti di base tramite l'API Legacy](../extensibility/instantiating-the-core-editor-by-using-the-legacy-api.md)
