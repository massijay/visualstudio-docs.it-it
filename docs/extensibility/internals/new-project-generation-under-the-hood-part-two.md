---
title: 'Nuova generazione del progetto: Dietro le quinte, parte 2 | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- projects [Visual Studio], new project dialog
- projects [Visual Studio], new project generation
ms.assetid: 73ce91d8-0ab1-4a1f-bf12-4d3c49c01e13
caps.latest.revision: 14
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
ms.sourcegitcommit: 5581224b17a7b42f65b69f741f984a144d78fc26
ms.openlocfilehash: 859eeac9c2fd322dcf231e9c70fe83b92b099111
ms.lasthandoff: 04/04/2017

---
# <a name="new-project-generation-under-the-hood-part-two"></a>Nuova generazione del progetto: Dietro le quinte, parte 2
In [nuova generazione progetto: in parte integrante, parte 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md) abbiamo visto come **nuovo progetto** inserite nella finestra di dialogo. Si supponga di aver selezionato un **applicazione Windows di Visual c#**, compilati il **nome** e **percorso** caselle di testo e si fa clic su OK.  
  
## <a name="generating-the-solution-files"></a>Generazione dei file di soluzione  
 Scelta di un modello di applicazione indirizza [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] per decomprimere e aprire il file con estensione vstemplate corrispondente e per avviare un modello per interpretare i comandi XML in questo file. Questi comandi creano progetti ed elementi di progetto nella soluzione nuova o esistente.  
  
 Il modello decomprime il file di origine, denominato modelli di elementi, dalla stessa cartella con estensione zip che contiene il file. vstemplate. Il modello consente di copiare questi file al nuovo progetto, di conseguenza la personalizzazione. Per una panoramica dei modelli di progetto e di elemento, vedere [NIB: modelli di Visual Studio](http://msdn.microsoft.com/en-us/141fccaa-d68f-4155-822b-27f35dd94041).  
  
### <a name="template-parameter-replacement"></a>Sostituzione dei parametri di modello  
 Quando il modello di copia di un modello di elemento a un nuovo progetto, eventuali parametri di modello vengono sostituite con le stringhe per personalizzare il file. Un parametro di modello è un token speciale che è preceduto e seguito da un segno di dollaro, ad esempio, $ $date.  
  
 Esaminiamo un modello di elemento di progetto tipico. Estrarre ed esaminare Program.cs nella cartella 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip Programmi\Microsoft Visual Studio.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace $safeprojectname$  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Se si crea un nuovo progetto applicazione Windows denominato "semplice", il modello sostituisce il `$safeprojectname$` parametro con il nome del progetto.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Windows.Forms;  
  
namespace Simple  
{  
    static class Program  
    {  
        // source code deleted here for brevity  
    }  
}  
```  
  
 Per un elenco completo dei parametri di modello, vedere [parametri di modello](../../ide/template-parameters.md).  
  
## <a name="a-look-inside-a-vstemplate-file"></a>Un aspetto all'interno di una. File VSTemplate  
 Il formato è un file. vstemplate di base  
  
```  
<VSTemplate Version="2.0.0"     xmlns="http://schemas.microsoft.com/developer/vstemplate/2005"     Type="Project">  
    <TemplateData>  
    </TemplateData>  
    <TemplateContent>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 È stato esaminato il \<TemplateData > sezione la [nuova generazione di progetto: in parte integrante, parte 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md). I tag in questa sezione consentono di controllare l'aspetto del **nuovo progetto** la finestra di dialogo.  
  
 I tag di \<TemplateContent > sezione la generazione di nuovi progetti ed elementi di progetto di controllo. Ecco il \<TemplateContent > sezione dal file nella cartella \Programmi\Microsoft Visual Studio 8\Common7\IDE\ProjectTemplates\CSharp\Windows\1033\WindowsApplication.zip cswindowsapplication.vstemplate.  
  
```  
<TemplateContent>  
  <Project File="WindowsApplication.csproj" ReplaceParameters="true">  
    <ProjectItem ReplaceParameters="true"  
      TargetFileName="Properties\AssemblyInfo.cs">  
      AssemblyInfo.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Resources.resx">  
      Resources.resx  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Resources.Designer.cs">  
      Resources.Designer.cs  
    </ProjectItem>  
    <ProjectItem TargetFileName="Properties\Settings.settings">  
      Settings.settings  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true"       TargetFileName="Properties\Settings.Designer.cs">  
      Settings.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true" OpenInEditor="true">  
      Form1.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Form1.Designer.cs  
    </ProjectItem>  
    <ProjectItem ReplaceParameters="true">  
      Program.cs  
    </ProjectItem>  
  </Project>  
</TemplateContent>  
```  
  
 Il \<progetto > tag controlla la generazione di un progetto e \<ProjectItem > tag controlla la generazione di un elemento di progetto. Se il parametro ReplaceParameters è true, il modello verrà personalizzare tutti i parametri di modello nel file di progetto o dell'elemento. In questo caso, tutti gli elementi di progetto personalizzati, ad eccezione di Settings. Settings.  
  
 Il parametro TargetFileName specifica il nome e percorso relativo del file di progetto risultante o dell'elemento. Ciò consente di creare una struttura di cartelle per il progetto. Se non si specifica questo argomento, l'elemento del progetto avrà lo stesso nome di modello di elemento di progetto.  
  
 La struttura di cartelle dell'applicazione Windows risulta è simile al seguente:  
  
 ![SimpleSolution](~/docs/extensibility/internals/media/simplesolution.png "SimpleSolution")  
  
 Il primo e unico \<progetto > tag in legge il modello:  
  
```  
<Project File="WindowsApplication.csproj" ReplaceParameters="true">  
```  
  
 Questo indica il modello di progetto per creare il file di progetto Simple.csproj copiando e personalizzazione di windowsapplication.csproj di elemento di modello.  
  
### <a name="designers-and-references"></a>Finestre di progettazione e riferimenti  
 È possibile visualizzare in Esplora soluzioni, che la cartella di proprietà è presente e che contiene i file previsti. Ma cosa succede progetto fa riferimento e dipendenze di file di progettazione, ad esempio Resources.Designer.cs per Resources. resx e Form1. Designer.cs a Form1. cs?  Questi vengono impostati nel file Simple.csproj quando viene generato.  
  
 Ecco il \<ItemGroup > da Simple.csproj che crea i riferimenti al progetto:  
  
```  
<ItemGroup>  
    <Reference Include="System" />  
    <Reference Include="System.Data" />  
    <Reference Include="System.Deployment" />  
    <Reference Include="System.Drawing" />  
    <Reference Include="System.Windows.Forms" />  
    <Reference Include="System.Xml" />  
</ItemGroup>  
```  
  
 È possibile visualizzare sono i riferimenti al sei progetto che vengono visualizzati in Esplora soluzioni. Ecco una sezione da un altro \<ItemGroup >. Numero di righe di codice sia stata eliminata per maggiore chiarezza. In questa sezione viene Settings.Designer.cs dipende Settings:  
  
```  
<ItemGroup>  
    <Compile Include="Properties\Settings.Designer.cs">  
        <DependentUpon>Settings.settings</DependentUpon>  
    </Compile>  
</ItemGroup>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Generazione di un nuovo progetto: dietro le quinte, parte 1](../../extensibility/internals/new-project-generation-under-the-hood-part-one.md)  
 [MSBuild](../../msbuild/msbuild.md)
