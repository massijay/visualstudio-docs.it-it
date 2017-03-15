---
title: "La migrazione di un servizio di linguaggio Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "servizi di linguaggio, la migrazione"
ms.assetid: e0f666a0-92a7-4f9c-ba79-d05b13fb7f11
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# La migrazione di un servizio di linguaggio Legacy
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

È possibile eseguire la migrazione di un servizio di linguaggio legacy a una versione successiva di Visual Studio l'aggiornamento del progetto e aggiunta al progetto un file source.extension.vsixmanifest. Il servizio di linguaggio stesso continuerà a funzionare come in precedenza, poiché l'editor di Visual Studio consente di adattare il.  
  
 Servizi di linguaggio legacy vengono implementati come parte di un package VS, ma il modo più recente per implementare le funzionalità del servizio del linguaggio è l'utilizzo delle estensioni MEF. Per ulteriori informazioni sulla nuova modalità per implementare un servizio di linguaggio, vedere [Editor e le estensioni del servizio di linguaggio](../../extensibility/editor-and-language-service-extensions.md).  
  
> [!NOTE]
>  Si consiglia di iniziare a utilizzare il nuovo editor API appena possibile. Verrà migliorare le prestazioni del servizio di linguaggio e consentono di sfruttare nuove funzionalità dell'editor.  
  
## La migrazione di una soluzione di servizio di linguaggio di Visual Studio 2008 a una versione successiva  
 La procedura seguente viene illustrato come adattare un esempio di Visual Studio 2008 denominato RegExLanguageService. È possibile trovare in questo esempio in un'installazione di Visual Studio 2008 SDK, il *il percorso di installazione di Visual Studio SDK*\\VisualStudioIntegration\\Samples\\IDE\\CSharp\\Example.RegExLanguageService\\ cartella.  
  
> [!IMPORTANT]
>  Se il servizio di linguaggio non definisce i colori, è necessario impostare esplicitamente <xref:Microsoft.VisualStudio.Shell.ProvideLanguageServiceAttribute.RequestStockColors%2A> a `true` su VSPackage:  
  
```  
[Microsoft.VisualStudio.Shell.ProvideLanguageService(typeof(YourLanguageService), YourLanguageServiceName, 0, RequestStockColors = true)]  
```  
  
#### Per eseguire la migrazione di un servizio di linguaggio di Visual Studio 2008 a una versione successiva  
  
1.  Installare le versioni più recenti di Visual Studio e Visual Studio SDK. Per ulteriori informazioni sui modi per installare il SDK, vedere [L'installazione di Visual Studio SDK](../../extensibility/installing-the-visual-studio-sdk.md).  
  
2.  Modificare il file RegExLangServ.csproj \(senza caricamento in Visual Studio.  
  
     Nel `Import` nodo che fa riferimento al file Microsoft.VsSDK.targets, sostituire il valore con il testo seguente.  
  
    ```  
    $(MSBuildExtensionsPath)\Microsoft\VisualStudio\v14.0\VSSDK\Microsoft.VsSDK.targets  
    ```  
  
3.  Salvare il file e chiuderlo.  
  
4.  Aprire la soluzione RegExLangServ.sln.  
  
5.  Il **aggiornamento unidirezionale** verrà visualizzata la finestra. Fare clic su **OK**.  
  
6.  Aggiornare le proprietà del progetto. Aprire il **le proprietà del progetto** selezionando il nodo del progetto nel **Esplora**, il pulsante destro su e selezionando **proprietà**.  
  
    -   Nel **applicazione** modificare **framework di destinazione** a **4.6.1**.  
  
    -   Nel **Debug** nella scheda il **Avvia programma esterno** digitare **\< percorso di installazione di Visual Studio \> \\Common7\\IDE\\devenv.exe.**.  
  
         Nel **argomenti della riga di comando** digitare \/**\/rootsuffix Exp**.  
  
7.  Aggiornare i riferimenti seguenti:  
  
    -   Rimuovere il riferimento a Microsoft.VisualStudio.Shell.9.0.dll, quindi aggiungere i riferimenti a Microsoft.VisualStudio.Shell.14.0.dll e Microsoft.VisualStudio.Shell.Immutable.11.0.dll.  
  
    -   Rimuovere il riferimento a Microsoft.VisualStudio.Package.LanguageService.9.0.dll, quindi aggiungere un riferimento a Microsoft.VisualStudio.Package.LanguageService.14.0.dll.  
  
    -   Aggiungere un riferimento a Microsoft.VisualStudio.Shell.Interop.10.0.dll.  
  
8.  Aprire il file VsPkg.cs e modificare il valore di `DefaultRegistryRoot` attributo  
  
    ```  
    "Software\\Microsoft\\VisualStudio\\14.0Exp"  
    ```  
  
9. L'esempio originale non registra il servizio di linguaggio, pertanto è necessario aggiungere l'attributo seguente a VsPkg.cs.  
  
    ```  
    [ProvideLanguageService(typeof(RegularExpressionLanguageService), "RegularExpressionLanguage", 0, RequestStockColors=true)]  
    ```  
  
10. È necessario aggiungere un file source.extension.vsixmanifest.  
  
    -   Copiare questo file da un'estensione esistente alla directory del progetto. \(Per ottenere questo file consiste nel creare un progetto VSIX \(in **File**, fare clic su **New**, quindi fare clic su **progetto**. In Visual Basic o c\# scegliere **estendibilità**, quindi selezionare **progetto VSIX**.\)  
  
    -   Aggiungere il file al progetto.  
  
    -   Il file **proprietà**, impostare **operazione di compilazione** a **Nessuna**.  
  
    -   Aprire il file con il **Editor di manifesto VSIX**.  
  
    -   Modificare i campi seguenti:  
  
    -   **ID**: RegExLangServ  
  
    -   **Nome prodotto**: RegExLangServ  
  
    -   **Descrizione**: un servizio di linguaggio di espressione regolare.  
  
    -   In **asset**, fare clic su **New**, selezionare il **tipo** a **Microsoft.VisualStudio.VsPackage**, impostare il **origine** a **un progetto nella soluzione corrente**, e quindi impostare il **progetto** a **RegExLangServ**.  
  
    -   Salvare e chiudere il file.  
  
11. Compilare la soluzione. I file compilati vengono distribuiti a **%USERPROFILE%\\AppData\\Local\\Microsoft\\VisualStudio\\14.0Exp\\Extensions\\MSIT\\ RegExLangServ\\**.  
  
12. Avviare il debug. Aprire una seconda istanza di Visual Studio.  
  
## Vedere anche  
 [Estensibilità del servizio di linguaggio legacy](../../extensibility/internals/legacy-language-service-extensibility.md)