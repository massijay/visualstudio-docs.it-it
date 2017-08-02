---
title: "Nuova generazione progetto: Dietro le quinte, parte 1 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "progetti [Visual Studio], finestra di dialogo Nuovo progetto"
  - "generazione di progetti [Visual Studio], nuovo progetto"
ms.assetid: 66778698-0258-467d-8b8b-c351744510eb
caps.latest.revision: 29
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 29
---
# Nuova generazione progetto: Dietro le quinte, parte 1
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Mai pensato di creare un nuovo tipo di progetto? Pensato che si verifica effettivamente quando si crea un nuovo progetto? Si analizzerà dietro le quinte e vedere cosa accade realmente.  
  
 Esistono diverse attività che coordina Visual Studio per l'utente:  
  
-   Visualizza una struttura ad albero di tutti i tipi di progetto disponibili.  
  
-   Visualizza un elenco di modelli di applicazione per ogni tipo di progetto e consente di sceglierne uno.  
  
-   Raccoglie informazioni di progetto per l'applicazione, ad esempio nome del progetto e il percorso.  
  
-   Passa le informazioni per la factory del progetto.  
  
-   Genera gli elementi di progetto e le cartelle nella soluzione corrente.  
  
## La finestra di dialogo Nuovo progetto  
 Tutto ha inizio quando si seleziona un tipo di progetto per un nuovo progetto. Per iniziare, fare clic su **Nuovo progetto** sul **File** menu. Il **Nuovo progetto** viene visualizzata la finestra di dialogo, aspetto qualcosa di simile al seguente:  
  
 ![Finestra di dialogo Nuovo progetto](~/extensibility/internals/media/newproject.gif "NewProject")  
  
 Diamo uno sguardo più da vicino. Il **i tipi di progetto** i vari tipi di progetto è possibile creare elenchi struttura ad albero. Quando si seleziona un tipo di progetto come **Windows Visual c\#**, verrà visualizzato un elenco di modelli di applicazione per iniziare.**Modelli visual Studio installati** vengono installati da Visual Studio e sono disponibili a tutti gli utenti del computer. È possibile aggiungere nuovi modelli creati o raccogliere per **modelli** e sono disponibili solo per l'utente.  
  
 Quando si seleziona un modello di **applicazione Windows**, una descrizione del tipo di applicazione viene visualizzata nella finestra di dialogo, in questo caso, **un progetto per la creazione di un'applicazione con un'interfaccia utente Windows**.  
  
 Nella parte inferiore del **Nuovo progetto** la finestra di dialogo, si vedrà più controlli che consentono di raccogliere ulteriori informazioni. I controlli visualizzati dipendono dal tipo di progetto, ma in genere includono un progetto **nome** casella di testo, un **percorso** casella di testo ed elementi correlati **Sfoglia** pulsante e un **Nome soluzione** casella di testo ed elementi correlati **Crea directory per soluzione** casella di controllo.  
  
## Popolare la finestra di dialogo Nuovo progetto  
 In cui viene il **Nuovo progetto** la finestra di dialogo Recupera le informazioni da? Esistono due meccanismi al lavoro in questo caso, uno di essi è deprecata. Il **Nuovo progetto** la finestra di dialogo combina e visualizza le informazioni ottenute da entrambi i meccanismi.  
  
 Il metodo \(obsoleto\) precedente utilizza voci del Registro di sistema e i file VSDIR. Questo meccanismo viene eseguito all'apertura di Visual Studio. Il metodo più recente utilizza i file. vstemplate. Questo meccanismo viene eseguito quando viene inizializzato Visual Studio, ad esempio, tramite l'esecuzione  
  
```  
devenv /setup  
```  
  
 o  
  
```  
devenv /installvstemplates  
```  
  
### Tipi di progetto  
 La posizione e i nomi di **i tipi di progetto** radice, ad esempio nodi, **Visual c\#** e **altri linguaggi**, è determinato dalle voci di registro di sistema. L'organizzazione dei nodi figlio, ad esempio **Database** e **Smart Device**, rispecchia la gerarchia delle cartelle che contengono i file. vstemplate corrispondenti. Esaminiamo i nodi radice prima.  
  
#### Nodi radice tipo di progetto  
 Quando [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] viene inizializzato, attraversa le sottochiavi della chiave del Registro di sistema del sistema HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\14.0\\NewProjectTemplates\\TemplateDirs per creare e denominare i nodi radice del **i tipi di progetto** struttura ad albero. Queste informazioni vengono memorizzate per un utilizzo successivo. Esaminare la chiave di \\\/1 TemplateDirs\\ {FAE04EC1\-301F\-11D3\-BF4B\-00C04F79EFBC il}. Ogni voce è un GUID di VSPackage. Il nome della sottochiave \(\/ 1\) viene ignorato, ma la sua presenza indica che si tratta di un **i tipi di progetto** nodo radice. Un nodo radice potrebbe essere a sua volta sottochiavi diverse che consentono di controllare l'aspetto nel **i tipi di progetto** struttura ad albero. Esaminiamo alcune di esse.  
  
##### \(Predefinito\)  
 Questo è l'ID risorsa della stringa localizzata che i nomi del nodo radice. La risorsa di stringa si trova nella DLL selezionata dal GUID VSPackage satellite.  
  
 Nell'esempio, è il GUID VSPackage  
  
 {FAE04EC1\-301F\-11D3\-BF4B\-00C04F79EFBC IL}  
  
 e l'ID di risorsa \(valore predefinito\) del nodo radice \(\/ 1\) è 2345 \#  
  
 Se si esamina la sottochiave SatelliteDll cercare il GUID della chiave di pacchetti nelle vicinanze, è possibile trovare il percorso dell'assembly che contiene la stringa di risorsa:  
  
 \< percorso di installazione di visual Studio \> \\VC\#\\VCSPackages\\1033\\csprojui.dll  
  
 Per verificarlo, aprire Esplora File e trascinare csprojui.dll nella directory di Visual Studio... La tabella di stringhe viene illustrato che risorse 2345 \# contiene la didascalia **Visual c\#**.  
  
##### SortPriority  
 Determina la posizione del nodo radice di **i tipi di progetto** struttura ad albero.  
  
 REG\_DWORD SortPriority 0x00000014 \(20\)  
  
 Minore è il numero di priorità, maggiore è la posizione nell'albero.  
  
##### DeveloperActivity  
 Se questa sottochiave è presente, la posizione del nodo radice è controllata nella finestra di dialogo Impostazioni per gli sviluppatori. Di seguito è riportato un esempio:  
  
 REG\_SZ DeveloperActivity VC \#  
  
 indica che in Visual c\# è un nodo radice se Visual Studio è impostato per [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)] lo sviluppo. In caso contrario, sia un nodo figlio del **altri linguaggi**.  
  
##### Cartella  
 Se questa sottochiave è presente, il nodo radice diventa un nodo figlio della cartella specificata. Viene visualizzato un elenco di possibili cartelle sotto la chiave  
  
 HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\11.0\\NewProjectTemplates\\PseudoFolders  
  
 Ad esempio, la voce di progetti di Database ha una chiave di cartella corrispondente alla voce di altri tipi di progetto in PseudoFolders. Quindi, nel **i tipi di progetto** albero **progetti di Database** sarà un nodo figlio del **altri tipi di progetto**.  
  
#### I nodi figlio di tipo di progetto e i file .vstdir  
 La posizione dei nodi figlio di **i tipi di progetto** albero segue la gerarchia delle cartelle nelle cartelle ProjectTemplates. Per modelli di macchina \(**Modelli Visual Studio installati**\), il percorso tipico è \\Programmi\\Microsoft Visual Studio 14.0\\Common7\\IDE\\ProjectTemplates\\ e per i modelli utente \(**modelli**\), il percorso tipico è Documents\\Visual Studio 14.0\\Templates\\ProjectTemplates\\. Le gerarchie di cartelle da questi due percorsi vengono unite per creare il **i tipi di progetto** struttura ad albero.  
  
 Per Visual Studio con c\# le impostazioni dello sviluppatore, il **i tipi di progetto** albero simile al seguente:  
  
 ![Tipi di progetto](~/extensibility/internals/media/projecttypes.png "ProjectTypes")  
  
 Nella cartella ProjectTemplates corrispondente è simile al seguente:  
  
 ![Modelli di progetto](~/extensibility/internals/media/projecttemplates.png "ProjectTemplates")  
  
 Quando il **Nuovo progetto** si apre la finestra di dialogo, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] attraversa la cartella ProjectTemplates e ricrea la struttura di **i tipi di progetto** struttura ad albero con alcune modifiche:  
  
-   Il nodo radice di **i tipi di progetto** struttura ad albero è determinata dal modello di applicazione.  
  
-   Il nome del nodo può essere localizzato e può contenere caratteri speciali.  
  
-   L'ordinamento può essere modificato.  
  
##### Individuare il nodo radice per un tipo di progetto  
 Quando Visual Studio consente di scorrere le cartelle ProjectTemplates, apre tutti i file con estensione zip ed estrae i file. vstemplate. Un file. vstemplate utilizza XML per descrivere un modello di applicazione. Per altre informazioni, vedere [Nuova generazione progetto: Dietro le quinte, parte 2](../Topic/New%20Project%20Generation:%20Under%20the%20Hood,%20Part%20Two.md).  
  
 Il tag \< ProjectType \> determina il tipo di progetto per l'applicazione. Ad esempio, il file \\CSharp\\SmartDevice\\WindowsCE\\1033\\WindowsCE\-EmptyProject.zip contiene un file EmptyProject.vstemplate con questo tag:  
  
```  
<ProjectType>CSharp</ProjectType>  
```  
  
 Il tag \< ProjectType \> e non la sottocartella della cartella ProjectTemplates, determina il nodo radice di un'applicazione nel **i tipi di progetto** struttura ad albero. Nell'esempio, le applicazioni di Windows CE appariranno sotto la **Visual c\#** nodo radice, e anche se fosse necessario spostare la cartella WindowsCE nella cartella VisualBasic, applicazioni di Windows CE ancora appariranno sotto la **Visual c\#** nodo radice.  
  
##### La localizzazione del nome di nodo  
 Quando Visual Studio consente di scorrere le cartelle ProjectTemplates, esamina tutti i file .vstdir che trova. Un file .vstdir è un file XML che controlla l'aspetto del tipo di progetto nel **Nuovo progetto** la finestra di dialogo. Nel file .vstdir, utilizzare il tag \< LocalizedName \> al nome di **i tipi di progetto** nodo.  
  
 Ad esempio, il file \\CSharp\\Database\\TemplateIndex.vstdir contiene questo tag:  
  
```  
<LocalizedName Package="{462b036f-7349-4835-9e21-bec60e989b9c}" ID="4598"/>  
```  
  
 Questo parametro determina l'ID di risorsa e DLL satellite della stringa localizzata che denomina in questo caso, il nodo radice, **Database**. Il nome localizzato può contenere caratteri speciali che non sono disponibili per i nomi delle cartelle, ad esempio **.NET**.  
  
 Se non è presente alcun tag \< LocalizedName \>, il tipo di progetto viene denominato dalla cartella stessa, **SmartPhone2003**.  
  
##### Ricerca l'ordinamento per un tipo di progetto  
 Per determinare l'ordinamento del tipo di progetto, i file .vstdir utilizzano il tag \< SortOrder \>.  
  
 Ad esempio, il file \\CSharp\\Windows\\Windows.vstdir contiene questo tag:  
  
```  
<SortOrder>5</SortOrder>  
```  
  
 Il file \\CSharp\\Database\\TemplateIndex.vstdir dispone di un tag con un valore maggiore:  
  
```  
<SortOrder>5000</SortOrder>  
```  
  
 Più basso il numero in \< SortOrder \> tag, maggiore è la posizione nella struttura ad albero, in modo che il **Windows** nodo compare superiore il **Database** nodo nel **i tipi di progetto** albero.  
  
 Se per un tipo di progetto non viene specificato alcun tag \< SortOrder \>, viene visualizzato in ordine alfabetico seguenti eventuali tipi di progetto che contengono specifiche \< SortOrder \>.  
  
 Si noti che non siano presenti file .vstdir nella cartella documenti \(**modelli**\) le cartelle. Nomi dei tipi di progetto applicazione di utente non sono localizzati e visualizzate in ordine alfabetico.  
  
#### Una rapida panoramica  
 Modifichiamo il **Nuovo progetto** finestra di dialogo e creare un nuovo modello di progetto utente.  
  
1.  Aggiungere una sottocartella del nodo progetto personalizzato alla cartella \\Programmi\\Microsoft Visual Studio 14.0\\Common7\\IDE\\ProjectTemplates\\CSharp.  
  
2.  Creare un file MyProject.vstdir nella cartella di nodo progetto personalizzato utilizzando qualsiasi editor di testo.  
  
3.  Aggiungere le righe seguenti al file .vstdir:  
  
    ```  
    <TemplateDir Version="1.0.0">  
        <SortOrder>6</SortOrder>  
    </TemplateDir>  
    ```  
  
4.  Salvare e chiudere il file .vstdir.  
  
5.  Creare un file MyProject.vstemplate nella cartella di nodo progetto personalizzato utilizzando qualsiasi editor di testo.  
  
6.  Aggiungere le righe del file. vstemplate:  
  
    ```  
    <VSTemplate Version="2.0.0" Type="Project" xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
        <TemplateData>  
            <ProjectType>CSharp</ProjectType>  
        </TemplateData>  
    </VSTemplate>  
    ```  
  
7.  Salvare il file the.vstemplate e chiudere l'editor.  
  
8.  Inviare il file. vstemplate per una nuova cartella compressa MyProjectNode\\MyProject.zip.  
  
9. Nella finestra di comando di Visual Studio, digitare:  
  
    ```  
    devenv /installvstemplates  
    ```  
  
 Aprire Visual Studio.  
  
1.  Aprire il **Nuovo progetto** finestra di dialogo casella ed espandere il **Visual c\#** nodo del progetto.  
  
 ![MyProjectNode](~/extensibility/internals/media/myprojectnode.png "MyProjectNode")  
  
 **Nodo progetto personalizzato** viene visualizzato come nodo figlio di Visual c\# sotto il nodo di Windows.  
  
## Vedere anche  
 [Nuova generazione progetto: Dietro le quinte, parte 2](../Topic/New%20Project%20Generation:%20Under%20the%20Hood,%20Part%20Two.md)