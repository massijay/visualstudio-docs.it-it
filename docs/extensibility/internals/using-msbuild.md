---
title: "Utilizzo di MSBuild | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Package VS, la compilazione con MSBuild"
  - "MSBuild, estendibilità"
  - "pacchetti, la compilazione con MSBuild"
ms.assetid: 9d38c388-1f64-430e-8f6c-e88bc99a4260
caps.latest.revision: 20
caps.handback.revision: 20
ms.author: "gregvanl"
manager: "ghogen"
---
# Utilizzo di MSBuild
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

MSBuild fornisce un formato XML ben definito ed estendibile per la creazione di file di progetto che descrivono gli elementi di progetto per essere compilato, attività di compilazione e le configurazioni di compilazione.  
  
 Per un esempio end\-to\-end di un sistema di progetto linguaggio basato su MSBuild, vedere Approfondimenti esempio IronPython nel[Esempi di VSSDK](../../misc/vssdk-samples.md).  
  
## Considerazioni generali MSBuild  
 File di progetto MSBuild, ad esempio, [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] con estensione csproj e [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] file VBPROJ, contengono dati che viene utilizzati in fase di compilazione, ma possono anche contenere dati che viene utilizzati in fase di progettazione. Dati in fase di compilazione vengono archiviati utilizzando le primitive di MSBuild, tra cui [Item Element \(MSBuild\)](../../msbuild/item-element-msbuild.md) e [Property Element \(MSBuild\)](../../msbuild/property-element-msbuild.md). In fase di progettazione dati, ovvero dati specifici per il tipo di progetto e degli eventuali sottotipi di progetto correlate, vengono archiviati in XML libere riservate per il servizio.  
  
 MSBuild non dispone del supporto nativo per gli oggetti di configurazione, ma fornire attributi condizionali per specificare i dati specifici della configurazione. Ad esempio:  
  
```  
<OutputDir Condition="'$(Configuration)'=="release'">Bin\MyReleaseConfig</OutputDir>  
```  
  
 Per ulteriori informazioni sugli attributi condizionali, vedere [Conditional Constructs](../../msbuild/msbuild-conditional-constructs.md).  
  
### Estensione di MSBuild per il tipo di progetto  
 Interfacce di MSBuild e API sono soggetti a modifiche nelle versioni future di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]. Pertanto, è consigliabile utilizzare le classi di framework \(MPF\) pacchetto gestito in quanto forniscono schermatura dalle modifiche.  
  
 Il Framework di pacchetto gestiti per i progetti \(MPFProj\) fornisce le classi di supporto per la creazione e gestione di nuovo sistema di progetto. È possibile trovare l'origine istruzioni di compilazione e di codice in [MPF per i progetti di Visual Studio 2013 \-](http://mpfproj12.codeplex.com/).  
  
 Le classi MPF specifici del progetto sono i seguenti:  
  
|Classe|Implementazione|  
|------------|---------------------|  
|`Microsoft.VisualStudio.Package.ProjectNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProject3><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IPersistFileFormat><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolutionEvents>|  
|`Microsoft.VisualStudio.Package.ProjectFactory`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory>|  
|`Microsoft.VisualStudio.Package.HierarchyNode`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy>|  
|`Microsoft.VisualStudio.Package.ProjectConfig`|<xref:Microsoft.VisualStudio.Shell.Interop.IVsCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsBuildableProjectCfg><br /><br /> <xref:Microsoft.VisualStudio.Shell.Interop.IVsDebuggableProjectCfg>|  
|`Microsoft.VisualStudio.Package.SettingsPage`|<xref:Microsoft.VisualStudio.OLE.Interop.IPropertyPageSite>|  
  
 `Microsoft.VisualStudio.Package.ProjectElement` classe è un wrapper per gli elementi di MSBuild.  
  
#### Visual Studio di generatori di File singolo. Attività MSBuild  
 Singolo file generatori sono accessibili in fase di progettazione solo, ma le attività MSBuild possono essere utilizzate in fase di progettazione e in fase di compilazione. Per ottenere la massima flessibilità, pertanto, utilizzare le attività MSBuild per trasformare e generare il codice. Per altre informazioni, vedere [Strumenti personalizzati](../../extensibility/internals/custom-tools.md).  
  
## Vedere anche  
 [MSBuild Reference](../../msbuild/msbuild-reference.md)   
 [MSBuild](http://msdn.microsoft.com/it-it/7c49aba1-ee6c-47d8-9de1-6f29a906e20b)   
 [Strumenti personalizzati](../../extensibility/internals/custom-tools.md)