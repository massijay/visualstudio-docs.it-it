---
title: Utilizzare Managed Package Framework per un tipo di progetto (c#) | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio SDK], creating with MPF
- MPF projects
- managed package framework, creating projects
ms.assetid: 926de536-eead-415b-9451-f1ddc8c44630
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
ms.sourcegitcommit: d5bc147592bfc36247c35f23ac2885055d096af3
ms.openlocfilehash: 1d70a70b942b3722ed61e1e8a2f2e54d96b916e4
ms.lasthandoff: 02/22/2017

---
# <a name="using-the-managed-package-framework-to-implement-a-project-type-c"></a>Utilizzando il Framework di pacchetto gestito per implementare un tipo di progetto (c#)
Il Framework di pacchetto gestito (MPF) fornisce le classi c# è possibile utilizzare o ereditare da per implementare i propri tipi di progetto. Il MPF implementa molte delle interfacce di che Visual Studio prevede un tipo di progetto per fornire, lasciando comunque la possibilità di concentrarsi su come implementare le indicazioni del tipo di progetto.  
  
## <a name="using-the-mpf-project-source-code"></a>Utilizzando il codice sorgente del progetto MPF  
 Il Framework di pacchetto gestiti per i progetti (MPFProj) fornisce le classi di supporto per la creazione e gestione di nuovo sistema di progetto. A differenza delle altre classi di MPF, le classi del progetto non sono inclusi negli assembly forniti con Visual Studio. Al contrario, le classi del progetto vengono fornite come codice sorgente in [MPF per progetti 2013](http://mpfproj12.codeplex.com).  
  
 Per aggiungere il progetto alla soluzione VSPackage, procedere come segue:  
  
1.  Scaricare i file MPFProj *MPFProjectDir*.  
  
2.  Nel *MPFProjectDir*\Dev10\Src\CSharp\ProjectBase.file, modificare il blocco seguente:  
  
```  
<!-- Provide a default value for $(ProjectBasePath) -->  
  <PropertyGroup>  
    <ProjectBasePath >MPFProjDir\Dev10\Src\CSharp</ProjectBasePath>  
  </PropertyGroup>  
```  
  
1.  Creare un progetto VSPackage.  
  
2.  Scaricare il progetto di VSPackage.  
  
3.  Modificare il file. csproj VSPackage aggiungendo il seguente blocco prima l'altro `<Import>` blocchi:  
  
```  
<Import Project="MPFProjectDir\Dev10\Src\CSharp\ProjectBase.files" />  
  <PropertyGroup>  
    <!--To specify a different registry root to register your package, uncomment the TargetRegistryRoot tag and specify a registry root in it.  
    <TargetRegistryRoot></TargetRegistryRoot>-->  
    <RegisterOutputPackage>true</RegisterOutputPackage>  
    <RegisterWithCodebase>true</RegisterWithCodebase>  
  </PropertyGroup>  
```  
  
1.  Salvare il progetto.  
  
2.  Chiudere e riaprire la soluzione VSPackage.  
  
3.  Chiudere e riaprire il progetto di VSPackage. Verrà visualizzata una nuova directory denominata ProjectBase.  
  
4.  Aggiungere il seguente riferimento al progetto VSPackage:  
  
     Microsoft.Build.Tasks.4.0  
  
5.  Compilare il progetto.  
  
## <a name="hierarchy-classes"></a>Gerarchia classi  
 Nella tabella seguente sono riepilogate le classi di MPFProj che supportano le gerarchie di progetto. Per ulteriori informazioni, vedere [gerarchie e selezione](../../extensibility/internals/hierarchies-and-selection.md).  
  
|Nome classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|  
|`Microsoft.VisualStudio.Package.ProjectNode`|  
|`Microsoft.VisualStudio.Package.ProjectContainerNode`|  
|`Microsoft.VisualStudio.Package.FileNode`|  
|`Microsoft.VisualStudio.Package.FolderNode`|  
|`Microsoft.VisualStudio.Package.ReferenceContainerNode`|  
|`Microsoft.VisualStudio.Package.ReferenceNode`|  
|`Microsoft.VisualStudio.Package.ProjectReferenceNode`|  
|`Microsoft.VisualStudio.Package.ComReferenceNode`|  
|`Microsoft.VisualStudio.Package.AssemblyReferenceNode`|  
|`Microsoft.VisualStudio.Package.BuildDependency`|  
  
## <a name="document-handling-classes"></a>Classi di gestione documenti  
 Nella tabella seguente sono elencate le classi di MPF che supportano la gestione dei documenti. Per ulteriori informazioni, vedere [di apertura e salvataggio di elementi di progetto](../../extensibility/internals/opening-and-saving-project-items.md).  
  
|Nome classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.DocumentManager`|  
|`Microsoft.VisualStudio.Package.FileDocumentManager`|  
  
## <a name="configuration-and-output-classes"></a>Configurazione e classi di Output  
 Nella tabella seguente sono elencate le classi in MPF che consentono di tipi di progetto supporta più configurazioni, ad esempio il debug e rilascio e raccolte di output del progetto. Per ulteriori informazioni, vedere [la gestione delle opzioni di configurazione](../../extensibility/internals/managing-configuration-options.md).  
  
|Nome classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.ConfigProvider`|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|  
|`Microsoft.VisualStudio.Package.BuildableProjectConfig`|  
|`Microsoft.VisualStudio.Package.OutputGroup`|  
|`Microsoft.VisualStudio.Package.ProjectElement`|  
  
## <a name="automation-support-classes"></a>Classi di supporto di automazione  
 Nella tabella seguente sono elencate le classi di MPF che supportano l'automazione in modo che gli utenti del tipo di progetto possono scrivere componenti aggiuntivi.  
  
|Nome classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.Automation.OAProject`|  
|`Microsoft.VisualStudio.Package.Automation.OANavigableProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItems`|  
|`Microsoft.VisualStudio.Package.Automation.OAProjectItem`|  
|`Microsoft.VisualStudio.Package.Automation.OANestedProjectItem`|  
  
## <a name="properties-classes"></a>Classi di proprietà  
 La tabella seguente elenca le classi di MPF che consentono di tipi di progetto aggiungono le proprietà che gli utenti possono esplorare e modificare in un visualizzatore proprietà.  
  
|Nome classe|  
|----------------|  
|`Microsoft.VisualStudio.Package.LocalizableProperties`|  
|`Microsoft.VisualStudio.Package.NodeProperties`|  
|`Microsoft.VisualStudio.Package.FileNodeProperties`|  
|`Microsoft.VisualStudio.Package.ProjectNodeProperties`|  
|`Microsoft.VisualStudio.Package.FolderNodeProperties`|  
|`Microsoft.VisualStudio.Package.ReferenceNodeProperties`|
