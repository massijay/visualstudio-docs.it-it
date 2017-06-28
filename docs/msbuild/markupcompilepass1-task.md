---
title: "Attività MarkupCompilePass1 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- converting XAML to binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], parameters
- converting XAML projects to compiled binary format [WPF MSBuild]
- MarkupCompilePass1 task [WPF MSBuild], converting XAML to binary format
ms.assetid: 693d6945-fd6f-4698-8f64-9dfcb71052d3
caps.latest.revision: 8
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
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
translationtype: Human Translation
ms.sourcegitcommit: 79460291e91f0659df0a4241e17616e55187a0e2
ms.openlocfilehash: d4cb33cd46ab45c580e70ce7e590960ed4fd75a9
ms.lasthandoff: 02/22/2017

---
# <a name="markupcompilepass1-task"></a>Attività MarkupCompilePass1
L'attività <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> converte i file di progetto [!INCLUDE[TLA#tla_xaml](../msbuild/includes/tlasharptla_xaml_md.md)] non localizzabili in formato binario compilato.  
  
## <a name="task-parameters"></a>Parametri dell'attività  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AllGeneratedFiles`|Parametro di output facoltativo **ITaskItem[]**.<br /><br /> Contiene un elenco completo dei file generati dall'attività <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>.|  
|`AlwaysCompileMarkupFilesInSeparateDomain`|Parametro **Boolean** facoltativo.<br /><br /> Specifica se eseguire l'attività in un <xref:System.AppDomain> separato. Se questo parametro restituisce **false**, l'attività verrà eseguita nello stesso <xref:System.AppDomain> di [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] e in modo più rapido. Se questo parametro restituisce **true**, l'attività verrà eseguita in un secondo <xref:System.AppDomain> isolato da [!INCLUDE[TLA2#tla_msbuild](../msbuild/includes/tla2sharptla_msbuild_md.md)] e in modo più lento.|  
|`ApplicationMarkup`|Parametro **ITaskItem[]** facoltativo.<br /><br /> Specifica il nome del file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] di definizione dell'applicazione.|  
|`AssembliesGeneratedDuringBuild`|Parametro **String[]** facoltativo.<br /><br /> Specifica i riferimenti ad assembly che vengono modificati durante il processo di compilazione. Ad esempio, una soluzione [!INCLUDE[TLA#tla_visualstu2005](../msbuild/includes/tlasharptla_visualstu2005_md.md)] può contenere un progetto che fa riferimento all'output compilato di un altro progetto. In questo caso, l'output compilato del secondo progetto può essere aggiunto al parametro **AssembliesGeneratedDuringBuild**.<br /><br /> Nota: il parametro **AssembliesGeneratedDuringBuild** deve contenere riferimenti all'insieme completo di assembly generati da una soluzione di compilazione.|  
|`AssemblyName`|Parametro **string** obbligatorio.<br /><br /> Specifica il nome breve dell'assembly generato per un progetto. Ad esempio, se un progetto sta generando un eseguibile [!INCLUDE[TLA#tla_mswin](../code-quality/includes/tlasharptla_mswin_md.md)] il cui nome è **WinExeAssembly.exe**, il parametro **AssemblyName** presenterà il valore **WinExeAssembly**.|  
|`AssemblyPublicKeyToken`|Parametro **String** facoltativo.<br /><br /> Specifica il token di chiave pubblica per l'assembly.|  
|`AssemblyVersion`|Parametro **String** facoltativo.<br /><br /> Specifica il numero di versione dell'assembly.|  
|`ContentFiles`|Parametro **ITaskItem[]** facoltativo.<br /><br /> Specifica l'elenco dei file di contenuto separati.|  
|`DefineConstants`|Parametro **String** facoltativo.<br /><br /> Specifica che viene mantenuto il valore corrente di **DefineConstants**, con effetti sulla generazione dell'assembly di destinazione. L'eventuale modifica di questo parametro può comportare la modifica anche dell'API pubblica nell'assembly di destinazione, con possibili effetti sulla compilazione dei file [!INCLUDE[TLA2#tla_titlexaml](../msbuild/includes/tla2sharptla_titlexaml_md.md)] che fanno riferimento ai tipi locali.|  
|`ExtraBuildControlFiles`|Parametro **ITaskItem[]** facoltativo.<br /><br /> Specifica un elenco di file che controllano l'attivazione di una ricompilazione durante la riesecuzione dell'attività <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1>. La ricompilazione viene attivata in caso di modifica di uno di questi file.|  
|`GeneratedBamlFiles`|Parametro di output facoltativo **ITaskItem[]**.<br /><br /> Contiene l'elenco dei file generati in formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`GeneratedCodeFiles`|Parametro di output facoltativo **ITaskItem[]**.<br /><br /> Contiene l'elenco dei file di codice gestito generati.|  
|`GeneratedLocalizationFiles`|Parametro di output facoltativo **ITaskItem[]**.<br /><br /> Contiene l'elenco dei file di localizzazione generati per ogni file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] localizzabile.|  
|`HostInBrowser`|Parametro **String** facoltativo.<br /><br /> Specifica se l'assembly generato è un'applicazione browser [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)]. Le opzioni valide sono **true** e **false**. Se **true**, verrà generato codice per supportare l'hosting del browser.|  
|`KnownReferencePaths`|Parametro **String[]** facoltativo.<br /><br /> Specifica i riferimenti ad assembly che non vengono modificati durante il processo di compilazione. Include assembly che si trovano in [!INCLUDE[TLA#tla_gac](../msbuild/includes/tlasharptla_gac_md.md)], in una directory di installazione di [!INCLUDE[TLA#tla_netframewk](../misc/includes/tlasharptla_netframewk_md.md)] e così via.|  
|`Language`|Parametro **String** obbligatorio.<br /><br /> Specifica il linguaggio gestito supportato dal compilatore. Le opzioni valide sono **C#**, **VB**, **JScript** e **C++**.|  
|`LanguageSourceExtension`|Parametro **String** facoltativo.<br /><br /> Specifica l'estensione aggiunta all'estensione del file di codice gestito generato:<br /><br /> `<Filename>.g<LanguageSourceExtension>`<br /><br /> Se il parametro **LanguageSourceExtension** non è impostato con un valore specifico, verrà usata l'estensione del nome file di origine predefinita per un linguaggio: **vb** per [!INCLUDE[TLA#tla_visualb](../msbuild/includes/tlasharptla_visualb_md.md)], **csharp** per [!INCLUDE[TLA#tla_cshrp](../data-tools/includes/tlasharptla_cshrp_md.md)].|  
|`LocalizationDirectivesToLocFile`|Parametro **String** facoltativo.<br /><br /> Specifica come generare informazioni di localizzazione per ogni file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] di origine. Le opzioni valide sono **None**, **CommentsOnly** e **All**.|  
|`OutputPath`|Parametro **String** obbligatorio.<br /><br /> Specifica la directory in cui vengono generati i file di codice gestito e i file in formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`OutputType`|Parametro **String** obbligatorio.<br /><br /> Specifica il tipo di assembly generato da un progetto. Le opzioni valide sono **winexe**, **exe**, **library** e **netmodule**.|  
|`PageMarkup`|Parametro **ITaskItem[]** facoltativo.<br /><br /> Specifica un elenco di file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] da elaborare.|  
|`References`|Parametro **ITaskItem[]** facoltativo.<br /><br /> Specifica l'elenco dei riferimenti dai file agli assembly contenenti i tipi usati nei file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)].|  
|`RequirePass2ForMainAssembly`|Parametro di output **Boolean** facoltativo.<br /><br /> Indica se il progetto contiene file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] non localizzabili che fanno riferimento ai tipi locali incorporati nell'assembly principale.|  
|`RequirePass2ForSatelliteAssembly`|Parametro di output **Boolean** facoltativo.<br /><br /> Indica se il progetto contiene file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] localizzabili che fanno riferimento ai tipi locali incorporati nell'assembly principale.|  
|`RootNamespace`|Parametro **String** facoltativo.<br /><br /> Specifica lo spazio dei nomi radice per le classi all'interno del progetto. **RootNamespace** viene usato anche come spazio dei nomi predefinito di un file di codice gestito generato quando il file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] non include l'attributo `x:Class`.|  
|`SourceCodeFiles`|Parametro **ITaskItem[]** facoltativo.<br /><br /> Specifica l'elenco dei file di codice per il progetto corrente. L'elenco non include file di codice gestito generati specifici del linguaggio.|  
|`UICulture`|Parametro **String** facoltativo.<br /><br /> Specifica l'assembly satellite per le impostazioni cultura dell'interfaccia utente in cui vengono incorporati i file in formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] generati. Se **UICulture** non è impostato, i file in formato binario [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] generati verranno incorporati nell'assembly principale.|  
|`XAMLDebuggingInformation`|Parametro **Boolean** facoltativo.<br /><br /> Se **true**, le informazioni diagnostiche verranno generate e incluse nel file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] compilato per agevolare il debug.|  
  
## <a name="remarks"></a>Note  
 L'attività <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> in genere compila [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] in formato binario e genera file di codice. Se un file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] contiene riferimenti a tipi definiti nello stesso progetto, la relativa compilazione in formato binario verrà rinviata da **MarkupCompilePass1** a un secondo passaggio di compilazione del markup (**MarkupCompilePass2**). La compilazione di tali file deve essere rinviata poiché è necessario attendere la compilazione dei tipi definiti localmente a cui si fa riferimento. Tuttavia, se un file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] presenta un attributo `x:Class`, <xref:Microsoft.Build.Tasks.Windows.MarkupCompilePass1> genererà il relativo file di codice specifico del linguaggio.  
  
 Un file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] è localizzabile se contiene elementi che usano l'attributo `x:Uid`:  
  
```xml  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    x:Uid="Page1Uid"  
    >  
  ...  
</Page>  
```  
  
 Un file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] fa riferimento a un tipo definito localmente quando dichiara uno spazio dei nomi [!INCLUDE[TLA#tla_xml](../msbuild/includes/tlasharptla_xml_md.md)] che usa il valore `clr-namespace` per fare riferimento a uno spazio dei nomi nel progetto corrente:  
  
```xml  
<Page x:Class="WPFMSBuildSample.Page1"  
    xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
    xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
    xmlns:localNamespace="clr-namespace:WPFMSBuildSample"  
    >  
    <Grid>  
      <Grid.Resources>  
        <localNameSpace:LocalType x:Key="localType" />  
      </Grid.Resources>  
      ...  
    </Grid>  
</Page>  
```  
  
 Se un file [!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] è localizzabile o fa riferimento a un tipo definito localmente, sarà necessario un secondo passaggio di compilazione del markup, che richiede l'esecuzione di [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md) e di [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).  
  
## <a name="example"></a>Esempio  
 L'esempio seguente mostra come convertire tre file `Page`[!INCLUDE[TLA2#tla_xaml](../msbuild/includes/tla2sharptla_xaml_md.md)] in file di formato binario. `Page1` contiene un riferimento a un tipo, `Class1`, che si trova nello spazio dei nomi radice del progetto e pertanto non viene convertito nei file di formato binario in questo passaggio di compilazione del markup. Viene invece eseguito [GenerateTemporaryTargetAssembly](../msbuild/generatetemporarytargetassembly-task.md), seguito da [MarkupCompilePass2](../msbuild/markupcompilepass2-task.md).  
  
```xml  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.MarkupCompilePass1"   
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="MarkupCompilePass1Task">  
    <MarkupCompilePass1   
      AssemblyName="WPFMSBuildSample"  
      Language="C#"  
      OutputType="WinExe"  
      OutputPath="obj\Debug\"  
      ApplicationMarkup="App.xaml"  
      PageMarkup="Page1.xaml;Page2.xaml;Page3.xaml"  
      SourceCodeFiles="Class1.cs"  
      References="c:\windows\Microsoft.net\Framework\v2.0.50727\System.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationCore.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\PresentationFramework.dll;C:\Program Files\Reference Assemblies\Microsoft\WinFx\v3.0\WindowsBase.dll" />  
  </Target>  
</Project>  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento su MSBuild WPF](../msbuild/wpf-msbuild-reference.md)   
 [Riferimento alle attività](../msbuild/wpf-msbuild-task-reference.md)   
 [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)   
 [Riferimento alle attività](../msbuild/msbuild-task-reference.md)   
 [Compilazione di un'applicazione WPF (WPF)](http://msdn.microsoft.com/Library/a58696fd-bdad-4b55-9759-136dfdf8b91c)   
 [Panoramica delle applicazioni browser XAML di WPF](http://msdn.microsoft.com/Library/3a7a86a8-75d5-4898-96b9-73da151e5e16)