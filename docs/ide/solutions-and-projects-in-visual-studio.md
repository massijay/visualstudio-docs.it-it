---
title: "Soluzioni e progetti in Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.savedeferredsaveprojectonclose"
  - "vs.untrustedtemplateopeningdocuments"
  - "Project Properties.FullPath"
  - "vs.addnewsolutionitem"
  - "vs.environment.projects"
  - "vs.openproject"
  - "vs.getopenfilename"
  - "vs.addnewitem"
  - "vs.encoding"
  - "vs.addexistingitem"
  - "Project Properties.URL"
  - "VS.SolutionExplorer"
  - "Project Properties.FileName"
  - "SolutionProperties.Name"
  - "VS.SaveChangesDlg"
  - "vs.newproject"
  - "VS.SolutionExplorer.Selection"
  - "SolutionProperties.Path"
  - "vs.getdirectoryname"
  - "vs.addexistingsolutionitem"
  - "SolutionProperties.Description"
  - "vs.environment.solutions"
  - "vs.saveordiscarddeferredsaveproject"
  - "VS.SolutionExplorer.Solutions"
helpviewer_keywords: 
  - "vs.solutionpropertypages"
  - "vs.solutionpropertypages.startupproject"
  - "vs.solutionpropertypages.configurationsettings"
  - "elementi di soluzione cartella in Esplora soluzioni"
  - "elementi di soluzione condiviso"
  - "soluzioni [Visual Studio]"
  - "elementi di progetto [Visual Studio], informazioni sugli elementi di progetto"
  - "aree di lavoro"
  - "progettazione di soluzioni [Visual Studio]"
  - "progetti [Visual Studio]"
  - "soluzioni [Visual Studio], progetti e"
  - "vs.solutionpropertypages.projectdependencies"
  - "applicazioni [Visual Studio]"
  - "configurazione di progetti [Visual Studio]"
  - "file esterni"
ms.assetid: aeaf56cb-c2dd-47f6-b012-23b84b7a7254
caps.latest.revision: 35
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 35
---
# <a name="solutions-and-projects-in-visual-studio"></a>Soluzioni e progetti in Visual Studio
Quando si crea un’app, un’applicazione, un sito Web, uno script, un plug-in e così via in Visual Studio, si comincia con un *progetto*. In senso logico, un progetto contiene di tutti i file di codice sorgente, le icone, le immagini, i file di dati e qualsiasi altro elemento che verrà compilato in un programma eseguibile o in un sito Web in caso contrario, o necessario per eseguire la compilazione.  Un progetto contiene anche tutte le impostazioni del compilatore e altri file di configurazione che potrebbero essere necessari per i vari servizi o componenti con cui il programma comunicherà.

> [!NOTE]
>  Non è necessario usare progetti e soluzioni. È possibile semplicemente aprire i file in Visual Studio e iniziare a modificare il codice. Per altre informazioni, vedere [Open Any Folder with Visual Studio](https://blogs.msdn.microsoft.com/visualstudio/2016/04/12/open-any-folder-with-visual-studio-15-preview/) (Aprire una cartella con Visual Studio).


 In senso letterale, un progetto è un file XML (*.vbproj, \*.csproj, \*.vcxproj) che definisce una gerarchia di cartelle virtuali insieme ai percorsi di tutti gli elementi in essa contenuti e a tutte le impostazioni di compilazione. In Visual Studio, il file di progetto viene utilizzato da Esplora soluzioni per visualizzare il contenuto e le impostazioni del progetto. Quando si compila il progetto, il motore MSBuild utilizza il file di progetto per creare il file eseguibile. È inoltre possibile personalizzare progetti per produrre altri tipi di output.  

 Un progetto è contenuto, in senso logico e all’interno di un file system, in una *soluzione*che può contenere uno o più progetti, insieme alle informazioni di compilazione, alle impostazioni di finestra di Visual Studio ed eventuali file misti che non sono associati ad alcun progetto. In senso letterale, la soluzione è un file di testo con un formato univoco specifico. In genere, non è destinato a essere modificato manualmente.  

 Una soluzione dispone un file con estensione suo associata che archivia le impostazioni, le preferenze e le informazioni di configurazione per ogni utente che ha lavorato al progetto.  

 Nel diagramma seguente viene illustrata la relazione tra progetti e soluzioni e gli elementi in essi contenuti dal punto di vista logico.  

 ![Progetti e soluzioni di Visual Studio](../ide/media/vs2015_project_diagram.png "vs2015_project_diagram")  

 È inoltre possibile creare modelli di progetto e modelli di elemento personalizzati. Per altre informazioni, vedere [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md).  

## <a name="creating-new-projects"></a>Creazione di nuovi progetti  
 Il modo più semplice per creare un nuovo progetto consiste nell’iniziare con un modello di progetto predefinito costituito da un set di file di codice generati in precedenza, file di configurazione, risorse e impostazioni che consentono di iniziare la creazione di un particolare tipo di applicazione o sito Web in un determinato linguaggio di programmazione. Questi modelli sono quelli visualizzati nella finestra di dialogo **Nuovo progetto** quando si sceglie **File &#124; Nuovo &#124; Progetto** o **File &#124; Nuovo &#124; Sito Web** dal menu principale e quindi si inizia a navigare. Per altre informazioni, vedere [Creazione di soluzioni e progetti](../ide/creating-solutions-and-projects.md) e  [Creazione di progetti da modelli](http://msdn.microsoft.com/en-us/7c36d86a-6b79-4480-8228-0f925f1204b2).  

## <a name="managing-projects-in-solution-explorer"></a>Gestione di progetti in Esplora soluzioni  
 Dopo aver creato un nuovo progetto, viene utilizzato **Esplora soluzioni** per visualizzare e gestire progetti e soluzioni e i relativi articoli associati. Nella figura seguente viene illustrato Esplora Server con una soluzione C# contenente due progetti.  

 ![Esplora soluzioni](../ide/media/vs2015_solution_explorer.png "vs2015_solution_explorer")  

## <a name="in-this-section"></a>Contenuto della sezione  

-   [Creazione di soluzioni e progetti](../ide/creating-solutions-and-projects.md)  

-   [Aggiunta e rimozione di elementi di progetto](../ide/adding-and-removing-project-items.md)  

-   [Gestione delle proprietà di progetti e soluzioni](../ide/managing-project-and-solution-properties.md)  

-   [Gestione dei riferimenti in un progetto](../ide/managing-references-in-a-project.md)  

-   [Proprietà dell'applicazione](../ide/application-properties.md)  

-   [Gestione delle firme di assembly e manifesti](../ide/managing-assembly-and-manifest-signing.md)  

-   [Procedura: Specificare l'icona di un'applicazione (Visual Basic, C#)](../ide/how-to-specify-an-application-icon-visual-basic-csharp.md)  

-   [Sviluppo per una versione specifica di .NET Framework](../ide/targeting-a-specific-dotnet-framework-version.md)  

-   [Creazione di modelli di progetti e di elementi](../ide/creating-project-and-item-templates.md)  

## <a name="see-also"></a>Vedere anche  
 [IDE di Visual Studio](../ide/visual-studio-ide.md)



<!--HONumber=Feb17_HO4-->


