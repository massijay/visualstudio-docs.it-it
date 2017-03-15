---
title: 'Procedura dettagliata: Creazione di un SDK mediante C++ | Documenti di Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 36ea793b-3832-41a1-b906-69e680ad5e1d
caps.latest.revision: 32
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
ms.sourcegitcommit: d4458cb2cf0f3f198b2931beec15f8eead446ba6
ms.openlocfilehash: 3baf914755f0cdd4e0aa0a6c1405126faeec0364
ms.lasthandoff: 02/22/2017

---
# <a name="walkthrough-creating-an-sdk-using-c"></a>Procedura dettagliata: Creazione di un SDK mediante C++
Questa procedura dettagliata viene illustrato come creare una libreria C++ nativa matematiche SDK, pacchetto come un Visual Studio Extension (VSIX), il SDK e utilizzarlo per creare un'applicazione. La procedura dettagliata è suddivisa in questi passaggi:  
  
-   [Per creare la native e le librerie di Runtime di Windows](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createClassLibrary)  
  
-   [Per creare il progetto di estensione NativeMathVSIX](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createVSIX)  
  
-   [Per creare un'applicazione di esempio che utilizza la libreria di classi](../extensibility/walkthrough-creating-an-sdk-using-cpp.md#createSample)  
  
## <a name="prerequisites"></a>Prerequisiti  
 Per seguire questa procedura dettagliata, è necessario installare Visual Studio SDK. Per ulteriori informazioni, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
##  <a name="a-namecreateclasslibrarya-to-create-the-native-and-windows-runtime-libraries"></a><a name="createClassLibrary"></a>Per creare la native e le librerie di Runtime di Windows  
  
1.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
2.  Nell'elenco dei modelli espandere **Visual C++**, **Windows Store**, quindi selezionare il **DLL (applicazioni Windows Store)** modello. Nel **nome** specificare `NativeMath`, quindi scegliere il **OK** pulsante.  
  
3.  Aggiornare NativeMath.h affinché corrisponda al codice seguente.  
  
     [!code-cpp[CreatingAnSDKUsingCpp n.&1;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_1.h)]  
  
4.  Aggiornamento NativeMath.cpp corrisponde questo codice:  
  
     [!code-cpp[CreatingAnSDKUsingCpp n.&2;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_2.cpp)]  
  
5.  In **Esplora**, aprire il menu di scelta rapida per **soluzione 'NativeMath'**, quindi scegliere **Aggiungi**, **nuovo progetto**.  
  
6.  Nell'elenco dei modelli espandere **Visual C++**, quindi selezionare il **componente Windows Runtime** modello. Nel **nome** specificare `NativeMathWRT`, quindi scegliere il **OK** pulsante.  
  
7.  Aggiornamento Class1 corrisponde questo codice:  
  
     [!code-cpp[CreatingAnSDKUsingCpp n.&3;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_3.h)]  
  
8.  Aggiornamento Class1 corrisponde questo codice:  
  
     [!code-cpp[CreatingAnSDKUsingCpp n.&4;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_4.cpp)]  
  
9. Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
##  <a name="a-namecreatevsixa-to-create-the-nativemathvsix-extension-project"></a><a name="createVSIX"></a>Per creare il progetto di estensione NativeMathVSIX  
  
1.  In **Esplora**, aprire il menu di scelta rapida per **soluzione 'NativeMath'**, quindi scegliere **Aggiungi**, **nuovo progetto**.  
  
2.  Nell'elenco dei modelli espandere **Visual c#**, **estendibilità**, quindi selezionare **pacchetto VSIX**. Nel **nome** specificare **NativeMathVSIX**, quindi scegliere il **OK** pulsante.  
  
3.  Quando viene visualizzata la finestra di progettazione del manifesto VSIX, chiuderla.  
  
4.  In **Esplora**, aprire il menu di scelta rapida per **source.extension.vsixmanifest**, quindi scegliere **Visualizza codice**.  
  
5.  Utilizzare il seguente codice XML per sostituire il codice XML esistente.  
  
    [!code-xml[6 CreatingAnSDKUsingCpp](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_6.xml)]

6.  In **Esplora**, aprire il menu di scelta rapida per il **NativeMathVSIX** del progetto, quindi fare clic **Aggiungi**, **nuovo elemento**.  
  
7.  Nell'elenco di **elementi Visual c#**, espandere **dati**, quindi selezionare **File XML**. Nel **nome** specificare `SDKManifest.xml`, quindi scegliere il **OK** pulsante.  
  
8.  Utilizzare questo codice XML per sostituire il contenuto del file:  
  
     [!code-xml[CreatingAnSDKUsingCpp n.&5;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_5.xml)]  
  
9. In **Esplora**, nel **NativeMathVSIX** progetto, creare questa struttura di cartelle:  
  
    ```  
  
    \DesignTime  
          \CommonConfiguration  
                \Neutral  
                      \Include  
          \Debug  
                \x86  
    \Redist  
          \Debug  
                \x86  
    \References  
          \CommonConfiguration  
                \Neutral  
    ```  
  
10. In **Esplora**, aprire il menu di scelta rapida per **soluzione 'NativeMath'**, quindi scegliere **Apri cartella in Esplora File**.  
  
11. In **Esplora File**, \NativeMath\NativeMath.h, copiare e quindi in **Esplora**, nel **NativeMathVSIX** del progetto, incollarlo nella cartella \DesignTime\CommonConfiguration\Neutral\Include\.  
  
     Copiare \Debug\NativeMath\NativeMath.lib e quindi incollarlo nella cartella \DesignTime\Debug\x86\.  
  
     Copiare \Debug\NativeMath\NativeMath.dll e incollarlo nella cartella \Redist\Debug\x86\.  
  
     Copiare DebugNativeMathWRTNativeMathWRT.dll e incollarlo nella cartella RedistDebugx86.  
  
     Copiare DebugNativeMathWRTNativeMathWRT.winmd e incollarlo nella cartella ReferencesCommonConfigurationNeutral.  
  
     Copiare DebugNativeMathWRTNativeMathWRT.pri e incollarlo nella cartella ReferencesCommonConfigurationNeutral.  
  
12. Nella cartella \DesignTime\Debug\x86\, creare un file di testo denominato NativeMathSDK.props e quindi incollarvi il contenuto seguente:  
  
    [!code-xml[CreatingAnSDKUsingCpp&#7;](../extensibility/codesnippet/XML/walkthrough-creating-an-sdk-using-cpp_7.xml)]  
  
13. Nella barra dei menu, scegliere **visualizzazione**, **altre finestre**, **finestra proprietà** (tastiera: premere il tasto F4).  
  
14. In **Esplora**, selezionare il **NativeMathWRT.winmd** file. Nel **proprietà** finestra, modifica il **operazione di compilazione** proprietà **contenuto**e quindi modificare il **Includi in VSIX** proprietà **True**.  
  
     Ripetere questo processo per il **SimpleMath.pri** file.  
  
     Ripetere questo processo per il **NativeMath.Lib** file.  
  
     Ripetere questo processo per il **NativeMathSDK.props** file.  
  
15. In **Esplora**, selezionare il **NativeMath.h** file. Nel **proprietà** finestra, modifica il **Includi in VSIX** proprietà **True**.  
  
     Ripetere questo processo per il **NativeMath.dll** file.  
  
     Ripetere questo processo per il **NativeMathWRT.dll** file.  
  
     Ripetere questo processo per il **SDKManifest.xml** file.  
  
16. Nella barra dei menu scegliere **Compilazione**, **Compila soluzione**.  
  
17. In **Esplora**, aprire il menu di scelta rapida per il **NativeMathVSIX** del progetto, quindi fare clic **Apri cartella in Esplora File**.  
  
18. In **Esplora File**, passare alla cartella \bin\Debug\ e quindi eseguire NativeMathVSIX.vsix per iniziare l'installazione.  
  
19. Scegliere il **installare** pulsante, attendere il completamento dell'installazione e quindi riavviare Visual Studio.  
  
##  <a name="a-namecreatesamplea-to-create-a-sample-app-that-uses-the-class-library"></a><a name="createSample"></a>Per creare un'applicazione di esempio che utilizza la libreria di classi  
  
1.  Nella barra dei menu scegliere **File**, **Nuovo**, **Progetto**.  
  
2.  Nell'elenco dei modelli espandere **Visual C++**, **Windows Store**, quindi selezionare **applicazione vuota**. Nel **nome** specificare **NativeMathSDKSample**, quindi scegliere il **OK** pulsante.  
  
3.  In **Esplora**, aprire il menu di scelta rapida per il **NativeMathSDKSample** del progetto, quindi fare clic **Aggiungi**, **riferimento**.  
  
4.  Nel **proprietà comuni**, **Framework e riferimenti** pagina delle proprietà, nell'elenco dei tipi di riferimento, espandere **Windows**, quindi selezionare **estensioni**. Nel riquadro dei dettagli, selezionare il **nativo Math SDK** estensione, quindi scegliere il **Aggiungi nuovo riferimento** pulsante.  
  
5.  Nel **Aggiungi riferimento** la finestra di dialogo, selezionare il **nativo Math SDK** casella di controllo e quindi scegliere il **OK** pulsante.  
  
6.  Visualizzare le proprietà del progetto per NativeMathSDKSample.  
  
     Le proprietà definite in NativeMathSDK.props sono state applicate quando è stato aggiunto il riferimento. È possibile verificarlo esaminando il **directory di VC + +** proprietà del progetto **le proprietà di configurazione**.  
  
7.  In **Esplora**, aprire MainPage. XAML e quindi utilizzare il seguente codice XAML per sostituire il contenuto:  
  
     [!code-xml[CreatingAnSDKUsingCppDemoApp n.&1;](../extensibility/codesnippet/Xaml/walkthrough-creating-an-sdk-using-cpp_8.xaml)]  
  
8.  Aggiornamento Mainpage.xaml.h corrisponde questo codice:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp n.&2;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_9.h)]  
  
9. Aggiornamento MainPage.xaml.cpp corrisponde questo codice:  
  
     [!code-cpp[CreatingAnSDKUsingCppDemoApp n.&3;](../extensibility/codesnippet/CPP/walkthrough-creating-an-sdk-using-cpp_10.cpp)]  
  
10. Premere il tasto F5 per eseguire l'app.  
  
11. Nell'app, immettere i due numeri, selezionare un'operazione e quindi scegliere il ** = ** pulsante.  
  
     Viene visualizzato il risultato corretto.  
  
 Questa procedura dettagliata viene illustrato come creare e utilizzare un SDK di estensione per chiamare un [!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] libreria e non -[!INCLUDE[wrt](../extensibility/includes/wrt_md.md)] libreria.  
  
## <a name="next-steps"></a>Passaggi successivi  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura dettagliata: Creazione di un SDK tramite c# o Visual Basic](../extensibility/walkthrough-creating-an-sdk-using-csharp-or-visual-basic.md)   
 [Creazione di un Software Development Kit](../extensibility/creating-a-software-development-kit.md)
