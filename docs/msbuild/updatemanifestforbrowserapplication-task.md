---
title: "UpdateManifestForBrowserApplication Task | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "UpdateManifestForBrowserApplication task [WPF MSBuild]"
  - "adding the <hostInBrowser /> element to the application manifest [WPF MSBuild]"
  - "building XBAP projects [WPF MSBuild]"
  - "UpdateManifestForBrowserApplication task [WPF MSBuild], parameters"
ms.assetid: 653339f7-654b-4d64-a26a-5c9f27036895
caps.latest.revision: 8
caps.handback.revision: 8
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# UpdateManifestForBrowserApplication Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'attività <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> viene eseguita per aggiungere l'elemento  **\<hostInBrowser \/\>** al manifesto dell'applicazione \(*nomeprogetto*.exe.manifest\) quando viene compilato un progetto [!INCLUDE[TLA#tla_xbap](../msbuild/includes/tlasharptla_xbap_md.md)].  
  
## Parametri dell'attività  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`ApplicationManifest`|Parametro **ITaskItem \[\]** obbligatorio.<br /><br /> Specifica il percorso e il nome del file manifesto dell'applicazione a cui si desidera aggiungere l'elemento `<hostInBrowser />`.|  
|`HostInBrowser`|Parametro **Boolean** obbligatorio.<br /><br /> Specifica se modificare il manifesto dell'applicazione per includere l'elemento **\< hostInBrowser \/ \>**.  Se **true**, un nuovo elemento `<`**hostInBrowser \/ \>** viene incluso nell'elemento **\< entryPoint \/ \>**.  Si noti che l'inclusione degli elementi è cumulativa: se un elemento **\< hostInBrowser \/ \>** esiste già, non verrà rimosso o sovrascritto.  Al contrario, viene creato un ulteriore elemento **\< hostInBrowser \/ \>**.  Se **false**, il manifesto dell'applicazione non viene modificato.|  
  
## Note  
 [!INCLUDE[TLA2#tla_xbap#plural](../msbuild/includes/tla2sharptla_xbapsharpplural_md.md)] vengono eseguiti tramite la distribuzione di [!INCLUDE[TLA#tla_clickonce](../msbuild/includes/tlasharptla_clickonce_md.md)] e pertanto devono essere pubblicati con manifesti di supporto dell'applicazione e della distribuzione.  [!INCLUDE[TLA#tla_msbuild](../msbuild/includes/tlasharptla_msbuild_md.md)] usa l'attività [GenerateApplicationManifest](http://msdn2.microsoft.com/library/6wc2ccdc.aspx) per generare un manifesto dell'applicazione.  
  
 Per configurare un'applicazione da ospitare in un browser, è necessario aggiungere un ulteriore elemento  **\< hostInBrowser \/ \>** al manifesto dell'applicazione, come illustrato nell'esempio riportato di seguito:  
  
```  
<!--MyXBAPApplication.exe.manifest-->  
<?xml version="1.0" encoding="utf-8"?>  
<asmv1:assembly ... >  
    <asmv1:assemblyIdentity ... />  
    <application />  
    <entryPoint>  
      ...  
      <hostInBrowser xmlns="urn:schemas-microsoft-com:asm.v3" />  
    </entryPoint>  
  ...  
/>  
```  
  
 L'attività <xref:Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication> viene eseguita quando viene compilato un progetto [!INCLUDE[TLA2#tla_xbap](../msbuild/includes/tla2sharptla_xbap_md.md)] per aggiungere l'elemento `<hostInBrowser />`.  
  
## Esempio  
 Nell'esempio seguente viene illustrato come verificare che l'elemento `<hostInBrowser />` sia incluso in un file manifesto dell'applicazione.  
  
```  
<Project xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  <UsingTask   
    TaskName="Microsoft.Build.Tasks.Windows.UpdateManifestForBrowserApplication"  
    AssemblyFile="C:\Program Files\Reference Assemblies\Microsoft\Framework\v3.0\PresentationBuildTasks.dll" />  
  <Target Name="UpdateManifestForBrowserApplicationTask">  
    <UpdateManifestForBrowserApplication  
      ApplicationManifest="MyXBAPApplication.exe.manifest"  
      HostInBrowser="true" />  
  </Target>  
</Project>  
```  
  
## Vedere anche  
 [WPF MSBuild Reference](../msbuild/wpf-msbuild-reference.md)   
 [Task Reference](../msbuild/wpf-msbuild-task-reference.md)   
 [MSBuild Reference](../msbuild/msbuild-reference.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)   
 [Compilazione di un'applicazione WPF \(WPF\)](../Topic/Building%20a%20WPF%20Application%20\(WPF\).md)   
 [Panoramica delle applicazioni browser XAML di WPF](../Topic/WPF%20XAML%20Browser%20Applications%20Overview.md)