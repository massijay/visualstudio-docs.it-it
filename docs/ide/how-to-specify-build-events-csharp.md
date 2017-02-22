---
title: "Procedura: specificare eventi di compilazione (C#) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "compilazione (eventi) [Visual Studio]"
  - "compilazioni [Visual Studio], eventi"
  - "eventi [Visual Studio], compilazioni"
  - "eventi post-compilazione"
  - "eventi pre-compilazione"
ms.assetid: b4ce1ad9-5215-4b6f-b6a2-798b249aa335
caps.latest.revision: 19
caps.handback.revision: 19
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Procedura: specificare eventi di compilazione (C#)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile utilizzare gli eventi di compilazione per specificare i comandi da eseguire prima dell'inizio o al termine della compilazione.  Gli eventi di compilazione vengono eseguiti solo se la generazione raggiunge correttamente quei punti nel processo di compilazione.  
  
 Quando un progetto viene compilato, gli eventi di pre\-compilazione vengono aggiunti a un file denominato PreBuildEvent.bat mentre gli eventi di post\-compilazione vengono aggiunti a un file denominato PostBuildEvent.bat.  Per garantire il controllo degli errori, aggiungere i comandi di controllo degli errori alle istruzioni di compilazione.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
## Come specificare gli eventi di pre\-compilazione e post\-compilazione  
  
#### Per specificare un evento di compilazione  
  
1.  In **Esplora soluzioni** selezionare il progetto per il quale si desidera specificare l'evento di compilazione.  
  
2.  Scegliere **Proprietà** dal menu **Progetto**.  
  
3.  Fare clic sulla scheda **Eventi di compilazione**.  
  
4.  Nella casella **Riga di comando eventi pre\-compilazione** specificare la sintassi per l'evento di compilazione.  
  
    > [!NOTE]
    >  Gli eventi pre\-compilazione non vengono eseguiti se il progetto è aggiornato e non viene attivata la compilazione.  
  
5.  Nella casella **Riga di comando eventi post\-compilazione** specificare la sintassi per l'evento di compilazione.  
  
    > [!NOTE]
    >  Aggiungere un'istruzione `call` prima di tutti i comandi di post\-compilazione che eseguono file BAT.  Ad esempio, `call C:\MyFile.bat` o `call C:\MyFile.bat call C:\MyFile2.bat`.  
  
6.  Nella casella **Esegui evento post\-compilazione** specificare in quali condizioni eseguire l'evento di post\-compilazione.  
  
    > [!NOTE]
    >  Per aggiungere una sintassi più lunga o per selezionare macro di compilazione dalla [Finestra di dialogo Riga di comando eventi pre\-compilazione\/post\-compilazione](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md), fare clic sul pulsante con i puntini di sospensione \(**…**\) per visualizzare una casella di testo.  
  
     La sintassi dell'evento di compilazione può includere qualsiasi comando valido a un prompt dei comandi oin un file bat.  Il nome di un file batch deve essere preceduto da `call` per essere certi che verranno eseguiti tutti i comandi successivi.  
  
     **Nota** Se l'evento di pre\-compilazione o post\-compilazione non viene completato correttamente, è possibile terminare la compilazione impostando l'azione evento in modo che si chiuda con un codice diverso da zero \(0\), che indica un'azione riuscita.  
  
## Esempio: come modificare le informazioni del manifesto utilizzando un evento di post\-compilazione  
 La procedura descritta di seguito illustra come impostare la versione minima del sistema operativo nel manifesto dell'applicazione utilizzando un comando exe chiamato da un evento di post\-compilazione \(il file exe.manifest nella directory del progetto\).  La versione minima del sistema operativo è un numero costituito da quattro parti, ad esempio 4.10.0.0.  Per eseguire questa operazione, il comando modificherà la sezione `<dependentOS>` del manifesto:  
  
```  
<dependentOS>  
   <osVersionInfo>  
      <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
   </osVersionInfo>  
</dependentOS>  
```  
  
#### Per creare un comando exe per la modifica del manifesto dell'applicazione  
  
1.  Creare un'applicazione console per il comando.  Scegliere **Nuovo** dal menu **File**, quindi selezionare **Progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Visual C\#**, selezionare **Windows** e fare clic sul modello **Applicazione console**.  Assegnare il nome `ChangeOSVersionCS` al progetto.  
  
3.  In Program.cs, aggiungere la riga seguente all'altra istruzione `using` nella parte superiore del file:  
  
    ```  
    using System.Xml;  
    ```  
  
4.  Nello spazio dei nomi `ChangeOSVersionCS` sostituire l'implementazione della classe `Program` con il seguente codice:  
  
    ```  
    class Program  
    {  
       /// <summary>  
       /// This function will set the minimum operating system version for a ClickOnce application.  
       /// </summary>  
       /// <param name="args">  
       /// Command Line Arguments:  
       /// 0 - Path to application manifest (.exe.manifest).  
       /// 1 - Version of OS  
       ///</param>  
       static void Main(string[] args)  
       {  
          string applicationManifestPath = args[0];  
          Console.WriteLine("Application Manifest Path: " + applicationManifestPath);  
  
          // Get version name.  
          Version osVersion = null;  
          if (args.Length >=2 ){  
             osVersion = new Version(args[1]);  
          }else{  
             throw new ArgumentException("OS Version not specified.");  
          }  
          Console.WriteLine("Desired OS Version: " + osVersion.ToString());  
  
          XmlDocument document;  
          XmlNamespaceManager namespaceManager;  
          namespaceManager = new XmlNamespaceManager(new NameTable());  
          namespaceManager.AddNamespace("asmv1", "urn:schemas-microsoft-com:asm.v1");  
          namespaceManager.AddNamespace("asmv2", "urn:schemas-microsoft-com:asm.v2");  
  
          document = new XmlDocument();  
          document.Load(applicationManifestPath);  
  
          string baseXPath;  
          baseXPath = "/asmv1:assembly/asmv2:dependency/asmv2:dependentOS/asmv2:osVersionInfo/asmv2:os";  
  
          // Change minimum required operating system version.  
          XmlNode node;  
          node = document.SelectSingleNode(baseXPath, namespaceManager);  
          node.Attributes["majorVersion"].Value = osVersion.Major.ToString();  
          node.Attributes["minorVersion"].Value = osVersion.Minor.ToString();  
          node.Attributes["buildNumber"].Value = osVersion.Build.ToString();  
          node.Attributes["servicePackMajor"].Value = osVersion.Revision.ToString();  
  
          document.Save(applicationManifestPath);  
       }  
    }  
    ```  
  
     Il comando accetta due argomenti: il percorso del manifesto dell'applicazione, la cartella in cui viene creato il manifesto durante il processo di compilazione, che in genere corrisponde a Projectname.publish, e la nuova versione del sistema operativo.  
  
5.  Compilare il progetto.  Scegliere **Compila soluzione** dal menu **Compila**.  
  
6.  Copiare il file exe in una directory, ad esempio `C:\TEMP\ChangeOSVersionVB.exe`.  
  
 Quindi, richiamare questo comando in un evento di post\-compilazione per modificare il manifesto dell'applicazione.  
  
#### Per richiamare un evento di post\-compilazione e modificare il manifesto dell'applicazione  
  
1.  Creare un'applicazione Windows per il progetto da pubblicare.  Scegliere **Nuovo** dal menu **File**, quindi selezionare **Progetto**.  
  
2.  Nella finestra di dialogo **Nuovo progetto** espandere il nodo **Visual C\#**, selezionare **Windows** e fare clic sul modello **Applicazione Windows Form**.  Assegnare il nome `CSWinApp` al progetto.  
  
3.  Con il progetto selezionato in **Esplora soluzioni**, scegliere **Proprietà** dal menu **Progetto**.  
  
4.  In Progettazione progetti passare alla pagina **Pubblica** e impostare **Posizione pubblicazione** su `C:\TEMP\`.  
  
5.  Pubblicare il progetto facendo clic su **Pubblica**.  
  
     Il file manifesto verrà compilato e collocato in `C:\TEMP\CSWinApp_1_0_0_0\CSWinApp.exe.manifest`.  Per visualizzare il manifesto, fare clic con il pulsante destro del mouse sul file e scegliere **Apri con**, quindi fare clic su **Seleziona il programma in un elenco** e selezionare **Blocco note**.  
  
     Cercare l'elemento `<osVersionInfo>` nel file.  Ad esempio, la versione potrebbe essere la seguente:  
  
    ```  
    <os majorVersion="4" minorVersion="10" buildNumber="0" servicePackMajor="0" />  
    ```  
  
6.  In Progettazione progetti fare clic sulla scheda **Eventi di compilazione** e quindi sul pulsante **Modifica post\-compilazione**.  
  
7.  Nella casella **Riga di comando eventi post\-compilazione** immettere il seguente comando:  
  
     `C:\TEMP\ChangeOSVersionCS.exe "$(TargetPath).manifest" 5.1.2600.0`  
  
     Al momento della compilazione del progetto, questo comando imposterà la versione minima del sistema operativo nel manifesto dell'applicazione su 5.1.2600.0.  
  
     La macro `$(TargetPath)` indica il percorso completo dell'eseguibile in fase di creazione, pertanto `$(TargetPath)`.manifest specificherà il manifesto dell'applicazione creato nella directory bin.  Con la pubblicazione, questo manifesto verrà copiato nel percorso di pubblicazione impostato in precedenza.  
  
8.  Pubblicare nuovamente il progetto.  Accedere alla pagina **Pubblica** e fare clic su **Pubblica**.  
  
     Visualizzare nuovamente il manifesto.  Per visualizzare il manifesto, passare alla directory di pubblicazione, fare clic con il pulsante destro del mouse sul file e scegliere **Apri con**, quindi fare clic su **Selezionare il programma in un elenco** e selezionare **Blocco note**.  
  
     La versione dovrebbe risultare come segue:  
  
    ```  
    <os majorVersion="5" minorVersion="1" buildNumber="2600" servicePackMajor="0" />  
    ```  
  
## Vedere anche  
 [Pagina Eventi di compilazione, Progettazione progetti \(C\#\)](../ide/reference/build-events-page-project-designer-csharp.md)   
 [Finestra di dialogo Riga di comando eventi pre\-compilazione\/post\-compilazione](../ide/reference/pre-build-event-post-build-event-command-line-dialog-box.md)   
 [Procedura: specificare gli eventi di compilazione \(Visual Basic\)](../Topic/How%20to:%20Specify%20Build%20Events%20\(Visual%20Basic\).md)   
 [Compilazione di applicazioni in Visual Studio](../ide/compiling-and-building-in-visual-studio.md)