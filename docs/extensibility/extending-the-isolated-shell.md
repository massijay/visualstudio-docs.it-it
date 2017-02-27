---
title: "Estensione Shell isolata | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Visual Studio shell, modalità isolata"
ms.assetid: 9a641d8f-211e-4486-a1b1-4a89fafe7ee8
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Estensione Shell isolata
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile estendere la shell di Visual Studio identificato tramite l'aggiunta di un package VS, un componente Managed Extensibility Framework \(MEF\) o un progetto VSIX generico per l'applicazione shell isolata.  
  
> [!NOTE]
>  I passaggi seguenti presuppongono l'esistenza di che è stata creata un'applicazione di base shell isolata utilizzando il modello di progetto Visual Studio Shell isolata. Per ulteriori informazioni su questo modello di progetto, vedere [Procedura dettagliata: Creazione di un'applicazione di base Shell isolata](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md).  
  
## Per il modello di progetto Package Visual Studio  
 Il modello di progetto Package Visual Studio può trovarsi in tre posizioni diverse all'interno di **Nuovo progetto** finestra di dialogo:  
  
1.  In **Visual Basic**, **estendibilità**. La lingua predefinita del progetto è Visual Basic.  
  
2.  In **Visual c\#**, **estendibilità**. È la lingua predefinita del progetto c\#.  
  
3.  In **altri tipi di progetto**, **estendibilità**. La lingua predefinita del progetto è C\+\+.  
  
## Aggiunta di un VSPackage  
 È possibile aggiungere un pacchetto dell'applicazione shell isolata. La procedura seguente viene illustrato come creare uno che aggiunge i comandi di menu.  
  
#### Per aggiungere un nuovo pacchetto  
  
1.  Aggiungere un progetto di Visual Studio Package denominato `MenuCommandsPackage`.  
  
2.  Nel **informazioni di base su VSPackage** pagina della procedura guidata, impostare **nome della società** per `Fabrikam` e **nome VSPackage** a `FabrikamMenuCommands`. Fare clic su **Avanti**.  
  
3.  Nella pagina successiva, selezionare **comando di Menu** e quindi scegliere **Avanti**.  
  
4.  Nella pagina successiva, impostare **nome comando** a `Fabrikam Command` e **ID di comando** a `cmdidFabrikamCommand`, quindi scegliere **successivo**.  
  
5.  Nel **Selezionare le opzioni di progetto di Test** pagina, deselezionare le opzioni di test e quindi scegliere il **Fine** pulsante.  
  
6.  Nel progetto ShellExtensionsVSIX, aprire il file source.extension.vsixmanifest.  
  
     Il **asset** sezione deve contenere una voce per il progetto VSShellStub.AboutBoxPackage.  
  
7.  Scegliere il pulsante **Nuovo**.  
  
8.  Nel **Aggiungi nuovo Asset** finestra, nel **tipo** elenco, selezionare **Microsoft.VisualStudio.VsPackage**.  
  
9. Nel **origine** elenco, verificare che **un progetto nella soluzione corrente** è selezionata. Nel **progetto** casella di riepilogo, selezionare **MenuCommandsPackage**.  
  
10. Salvare e chiudere il file.  
  
11. Ricompilare la soluzione e avviare il debug la shell isolata.  
  
12. Nella barra dei menu, scegliere **strumenti** menu, quindi **comando Fabrikam**.  
  
     Verrà visualizzata una finestra di messaggio.  
  
13. Arrestare il debug dell'applicazione.  
  
## Aggiunta di un componente MEF  
 La procedura seguente viene illustrato come aggiungere un componente MEF nell'applicazione di shell isolata.  
  
#### Per aggiungere un componente MEF  
  
1.  Nel **Aggiungi nuovo progetto** nella finestra di dialogo **Visual c\#**, **estendibilità**, utilizzare il **margine dell'Editor** modello per aggiungere un progetto. Assegnargli il nome `ShellEditorMargin`.  
  
2.  Nel progetto ShellExtensionsVSIX, aprire il file Source.extension.vsixmanifest nella visualizzazione progettazione, non la visualizzazione del codice.  
  
3.  Nel `Asset` quindi scegliere **Aggiungi contenuto**.  
  
4.  Nel **Aggiungi nuovo Asset** finestra, nel **tipo** elenco, selezionare **Microsoft.VisualStudio.MefComponent**.  
  
5.  Nel **origine** elenco, verificare che **un progetto nella soluzione corrente** è selezionata. Nel **progetto** casella di riepilogo, selezionare **ShellEditorMargin**.  
  
6.  Salvare e chiudere il file.  
  
7.  Ricompilare la soluzione e avviare il debug la shell isolata.  
  
8.  Aprire un file di testo.  
  
     Un margine verde che contiene le parole "Hello world\!" deve essere visualizzato nella parte inferiore della finestra di file di testo.  
  
9. Arrestare il debug dell'applicazione.  
  
## Aggiunta di un progetto VSIX generico  
  
#### Per aggiungere un progetto VSIX generico  
  
1.  Nel **Aggiungi nuovo progetto** nella finestra di dialogo **Visual c\#**, **estendibilità**, utilizzare il **VSIXProject** modello per aggiungere un progetto. Assegnargli il nome `EmptyVSIX`.  
  
2.  Nel progetto ShellExtensionsVSIX, aprire il file Source.extensions.vsixmanifest nella visualizzazione progettazione, non la visualizzazione del codice.  
  
3.  Nel `Assets` quindi scegliere **New**.  
  
4.  Nel **Aggiungi nuovo Asset** finestra, nel **tipo** elenco, selezionare il tipo di contenuto che si desidera aggiungere.  
  
5.  In **origine**, assicurarsi che il **un progetto nella soluzione corrente** opzione è selezionata. Nella casella di riepilogo, selezionare il nome del progetto VSIX.  
  
6.  Salvare e chiudere il file.  
  
7.  Se questo progetto include codice compilato, è necessario modificare il progetto in modo che l'assembly è incluso nell'output.  
  
    1.  Scaricare il progetto VSIX e aprire il file di progetto.  
  
    2.  Nel primo `<PropertyGroup>` bloccare, modificare il valore di `<CopyBuildOutputToOutputDirectory>` a `true`.  
  
    3.  Salvare e ricaricare il progetto.  
  
8.  Compilare ed eseguire la soluzione.  
  
## Vedere anche  
 [Procedura dettagliata: Creazione di un'applicazione di base Shell isolata](../extensibility/walkthrough-creating-a-basic-isolated-shell-application.md)