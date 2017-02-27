---
title: "Standard and Custom Toolset Configurations | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSBuild, custom toolset configurations"
  - "MSBuild, msbuild.exe.config"
ms.assetid: 15a048c8-5ad3-448e-b6e9-e3c5d7147ed2
caps.latest.revision: 31
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 31
---
# Standard and Custom Toolset Configurations
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un Set di strumenti di MSBuild contiene riferimenti alle attività, target e strumenti che è possibile utilizzare per compilare un progetto di applicazione.  MSBuild include un Set di strumenti standard, ma è anche possibile creare Set di strumenti personalizzati.  Per informazioni su come specificare un Set di strumenti, vedere [Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md).  
  
## Configurazioni standard del set di strumenti  
 MSBuild 12.0 include i Set di strumenti descritti di seguito:  
  
|ToolsVersion|Percorso del Set di strumenti \(come specificato nella proprietà di compilazione di MSBuildBinPath o MSBuildToolsPath\)|  
|------------------|-----------------------------------------------------------------------------------------------------------------------------|  
|2.0|*Windows installation path*\\Microsoft.Net\\Framework\\v2.0.50727\\|  
|3.5|*Windows installation path*\\Microsoft.NET\\Framework\\v3.5\\|  
|4.0|*Windows installation path*\\Microsoft.NET\\Framework\\v4.0.30319\\|  
|12.0|*%ProgramFiles%*\\ MSBuild \\12.0\\bin|  
  
 Il valore `ToolsVersion` determina quale Set di strumenti è utilizzato da un progetto generato da Visual Studio.  In [!INCLUDE[vs_dev12](../data-tools/includes/vs_dev12_md.md)] il valore predefinito è "12.0" \(indipendentemente dalla versione specificata nel file di progetto\), ma è possibile sostituire tale attributo utilizzando l'opzione **\/toolsversion** nel prompt dei comandi.  Per informazioni su questo attributo e altre modalità per specificare `ToolsVersion`, vedere [Overriding ToolsVersion Settings](../msbuild/overriding-toolsversion-settings.md).  
  
 Se `ToolsVersion` non viene specificato, la chiave del Registro di sistema HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\\<Version Number\>\\DefaultToolsVersion definisce la `ToolsVersion`, che è sempre 2.0.  
  
 Le chiavi del Registro di sistema seguenti specificano il percorso di installazione di MSBuild.exe.  
  
|Chiave del Registro di sistema|Nome della chiave|Valore della chiave della stringa|  
|------------------------------------|-----------------------|---------------------------------------|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\2.0\\|MSBuildToolsPath|Percorso di installazione di .NET Framework 2.0|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\ MSBuild\\ToolsVersions\\3.5\\|MSBuildToolsPath|Percorso di installazione di .NET Framework 3.5|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\ MSBuild\\ToolsVersions\\4.0\\|MSBuildToolsPath|Percorso di installazione di .NET Framework 4|  
|\\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\ MSBuild\\ToolsVersions\\12.0\\|MSBuildToolsPath|Percorso di installazione di MSBuild|  
  
### I subset di strumenti  
 Se la chiave del Registro di sistema nella tabella precedente contiene una sottochiave, questa verrà utilizzata da MSBuild per determinare il percorso di un sub\-toolset che può sovrascrivere il percorso nel toolset padre.  Ad esempio la seguente sottochiave:  
  
 \\HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\MSBuild\\ToolsVersions\\12.0\\12.0  
  
 Se le proprietà vengono definite sia nel toolset di base che nel sub\-toolset specificato, vengono utilizzate le proprietà definite nel sub\-toolset.  Ad esempio, il set di strumenti di MSBuild 4.0 definisce `SDK40ToolsPath` per indicare l'SDK 7.0A , ma il set di strumenti 4.0\\11.0 di MSBuild definisce la stessa proprietà per indicare l'SDK 8.0A.  Se `VisualStudioVersion` non è impostata, `SDK40ToolsPath` indica la 7.0A, ma se `VisualStudioVersion` è impostata su 11.0, la proprietà indica invece la 8.0A.  
  
 La proprietà di compilazione `VisualStudioVersion` indica se i sottonodi un sub\-toolset diventano attivi.  Ad esempio, il valore `VisualStudioVersion` "12.0" indica il sub\-toolset MSBuild 12.0.  Per ulteriori informazioni, vedere la sezione Sub\-toolsets in [Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md).  
  
> [!NOTE]
>  Si consiglia di evitare di modificare tali impostazioni.  È possibile tuttavia aggiungere impostazioni personali e stabilire definizioni personalizzate di toolset per l'intero computer, come descritto nella sezione successiva.  
  
## Definizioni di set di strumenti personalizzati  
 Se un set di strumenti standard non soddisfa i requisiti di compilazione, è possibile creare un set di strumenti personalizzato.  Ad esempio, è possibile utilizzare uno scenario di lavoro di compilazione in cui è necessario disporre di un sistema separato per compilare progetti [!INCLUDE[vcprvc](../code-quality/includes/vcprvc_md.md)].  Utilizzando un Set di strumenti personalizzato, è possibile assegnare valori personalizzati all'attributo `ToolsVersion` quando si creano progetti o MSBuild.exe viene eseguito.  In questo modo, è possibile utilizzare la proprietà `$(MSBuildToolsPath)` per importare il file .targets da tale directory, nonché definirne delle proprietà personalizzate del toolset che possono essere utilizzate per qualsiasi progetto che utilizza il tale toolset.  
  
 Specificare un Set di strumenti personalizzato nel file di configurazione per MSBuild.exe \(o per il tool personalizzato che ospita il motore MSBuild, se è ciò che si vuole utilizzare \).  Ad esempio, il file di configurazione per MSBuild.exe potrebbe includere la seguente definizione di Set di strumenti se si desidera eseguire l'override del comportamento predefinito di ToolsVersion 12,0.  
  
```  
<msbuildToolsets default="12.0">  
   <toolset toolsVersion="12.0">  
      <property name="MSBuildToolsPath"   
        value="C:\SpecialPath" />  
   </toolset>  
</msbuildToolsets>  
```  
  
 `<msbuildToolsets>` deve essere definito nel file di configurazione, come segue.  
  
```  
<configSections>  
   <section name="msbuildToolsets"         
       Type="Microsoft.Build.BuildEngine.ToolsetConfigurationSection,   
       Microsoft.Build.Engine, Version=12.0.0.0, Culture=neutral,   
       PublicKeyToken=b03f5f7f11d50a3a"  
   </section>  
</configSections>  
```  
  
> [!NOTE]
>  Per essere letto correttamente, `<configSections>` deve essere la prima sottosezione nella sezione `<configuration>`.  
  
 `ToolsetConfigurationSection` è una sezione di configurazione personalizzata che può essere utilizzata da qualsiasi host MSBuild per la configurazione personalizzata.  Se si utilizza un set di strumenti personalizzato, per inizializzare il motore di compilazione un host deve solo fornire le voci del file di configurazione.  Definendo le voci nel Registro di sistema, è possibile specificare i Set di strumenti per l'intero computer che si applicano a MSBuild.exe, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e a tutti gli host di MSBuild.  
  
> [!NOTE]
>  Se un file di configurazione definisce le impostazioni per un `ToolsVersion` già definito nel Registro di sistema, le due definizioni non vengono unite.  La definizione nel file di configurazione ha la precedenza e le impostazioni nel Registro di sistema per `ToolsVersion` vengono ignorate.  
  
 Le proprietà seguenti sono specifiche per il valore di `ToolsVersion` utilizzato nei progetti:  
  
-   **$\(MSBuildBinPath\)** è impostato sul valore `ToolsPath` specificato nel Registro di sistema o nel file di configurazione in cui `ToolsVersion` è definito.  L'impostazione `$(MSBuildToolsPath)` nel Registro di sistema o nel file di configurazione specifica il percorso delle attività principali e dei target.  Nel file di progetto, esegue il mapping alla proprietà $\(MSBuildBinPath\) e anche alla proprietà $\(MSBuildToolsPath\).  
  
-   `$(MSBuildToolsPath)` è una proprietà riservata che viene fornita dalla proprietà MSBuildToolsPath specificata nel file di configurazione. Questa proprietà sostituisce `$(MSBuildBinPath)`.  Tuttavia,`$(MSBuildBinPath)` passa avanti per compatibilità. Set di strumenti personalizzati devono definire `$(MSBuildToolsPath)` o `$(MSBuildBinPath)` ma non entrambi, a meno che entrambi abbiano lo stesso valore.  
  
 È possibile anche aggiungere al file di configurazione proprietà personalizzate, proprietà specifiche per ToolsVersion, utilizzando la stessa sintassi che si utilizza per aggiungere la proprietà MSBuildToolsPath.  Per rendere disponibili queste proprietà personalizzate ai file di progetto, utilizzare lo stesso nome per il nome del valore specificato nel file di configurazione.  È possibile definire toolset ma non i sub\-toolset nel file di configurazione.  
  
## Vedere anche  
 [Toolset \(ToolsVersion\)](../msbuild/msbuild-toolset-toolsversion.md)