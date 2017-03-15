---
title: "GenerateApplicationManifest Task | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/msbuild/2003#GenerateApplicationManifest"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "MSBuild, GenerateApplicationManifest task"
  - "HostInBrowser property (MSBuild)"
  - "GenerateApplicationManifest task [MSBuild]"
ms.assetid: a494102b-0cb2-4755-8e2a-d2c0f39fac1d
caps.latest.revision: 24
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 24
---
# GenerateApplicationManifest Task
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Genera un manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] o un manifesto nativo.  Un manifesto nativo descrive un componente definendone un'identità univoca e identificando tutti gli assembly e i file che lo costituiscono.  Un manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] estende le caratteristiche del manifesto nativo, in quanto specifica il punto di ingresso e il livello di sicurezza dell'applicazione.  
  
## Parametri  
 Nella tabella riportata di seguito sono descritti i parametri dell'attività `GenerateApplicationManifest`.  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|`AssemblyName`|Parametro `String` facoltativo.<br /><br /> Specifica il campo `Name` relativo all'identità dell'assembly per il manifesto generato.  Se questo parametro non è specificato, il nome viene dedotto dal parametro `EntryPoint` o `InputManifest`.  Se non è possibile creare alcun nome, viene generato un errore.|  
|`AssemblyVersion`|Parametro `String` facoltativo.<br /><br /> Specifica il campo `Version` relativo all'identità dell'assembly per il manifesto generato.  Se questo parametro non è specificato, viene utilizzato il valore predefinito "1.0.0.0".|  
|`ClrVersion`|Parametro `String` facoltativo.<br /><br /> Specifica la versione minima di Common Language Runtime \(CLR\) richiesta dall'applicazione.  Il valore predefinito è la versione di CLR utilizzata dal sistema di compilazione.  Se viene generato un manifesto nativo, questo parametro verrà ignorato.|  
|`ConfigFile`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica l'elemento che contiene il file di configurazione dell'applicazione.  Se viene generato un manifesto nativo, questo parametro verrà ignorato.|  
|`Dependencies`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica un elenco di elementi che definisce l'insieme di assembly dipendenti per il manifesto generato.  Ciascun elemento può essere ulteriormente descritto dai relativi metadati per specificare lo stato di distribuzione aggiuntivo e il tipo di dipendenza.  Per ulteriori informazioni, vedere la sezione "Metadati degli elementi" riportata di seguito.|  
|`Description`|Parametro `String` facoltativo.<br /><br /> Specifica la descrizione per l'applicazione o il componente.|  
|`EntryPoint`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica un singolo elemento che indica il punto di ingresso per l'assembly del manifesto generato.<br /><br /> In un manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] questo parametro specifica l'assembly che viene avviato quando si esegue l'applicazione.|  
|`ErrorReportUrl`|Parametro [String](assetId:///String?qualifyHint=False&autoUpgrade=True) facoltativo.<br /><br /> Specifica l'URL della pagina Web visualizzata nelle finestre di dialogo durante i rapporti sugli errori nelle installazioni ClickOnce.|  
|`FileAssociations`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica un elenco di uno o più tipi di file associati al manifesto della distribuzione ClickOnce.<br /><br /> Le associazioni di file sono valide solo quando la destinazione è .NET Framework 3.5 o versioni successive.|  
|`Files`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Contiene i file da includere nel manifesto.  Specificare il percorso completo di ciascun file.|  
|`HostInBrowser`|Parametro [Boolean](assetId:///Boolean?qualifyHint=False&autoUpgrade=True) facoltativo.<br /><br /> Se `true`, l'applicazione è ospitata in un browser \(come accade alle applicazioni Web browser WPF\).|  
|`IconFile`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Indica il file icona dell'applicazione.  L'icona dell'applicazione viene espressa nel manifesto generato dell'applicazione e viene utilizzata per il menu Start e la finestra di dialogo Installazione applicazioni.  Se questo parametro non è specificato, viene utilizzata un'icona predefinita.  Se viene generato un manifesto nativo, questo parametro verrà ignorato.|  
|`InputManifest`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Indica un documento XML di input da utilizzare come base per il generatore del manifesto.  In questo modo è possibile applicare nel manifesto di output dati strutturati, ad esempio dati di sicurezza dell'applicazione o definizioni del manifesto personalizzate.  L'elemento radice del documento XML deve essere un nodo assembly nello spazio dei nomi asmv1.|  
|`IsolatedComReferences`|Parametro <xref:Microsoft.Build.Framework.ITaskItem>`[]` facoltativo.<br /><br /> Specifica i componenti COM da isolare nel manifesto generato.  Questo parametro supporta la capacità di isolare i componenti COM per la distribuzione di tipo COM senza registrazione.  È prevista la generazione automatica di un manifesto con definizioni di registrazione COM standard.  Per consentire tuttavia il corretto funzionamento del parametro, è necessario registrare i componenti COM nel computer di compilazione.|  
|`ManifestType`|Parametro `String` facoltativo.<br /><br /> Specifica il tipo di manifesto da generare.  Per il parametro è possibile specificare i seguenti valori:<br /><br /> -   `Native`<br />-   `ClickOnce`<br /><br /> Se questo parametro non è specificato, viene utilizzato il valore predefinito `ClickOnce`.|  
|`MaxTargetPath`|Parametro `String` facoltativo.<br /><br /> Specifica la lunghezza massima consentita di un percorso file nella distribuzione di un'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)].  Se viene specificato questo valore, la lunghezza di ciascun percorso di file nell'applicazione verrà confrontata con tale limite.  Per tutti gli elementi che superano il limite verrà visualizzato un avviso di compilazione.  Se il parametro non è specificato o è uguale a zero, non viene eseguita alcuna verifica.  Se viene generato un manifesto nativo, questo parametro verrà ignorato.|  
|`OSVersion`|Parametro `String` facoltativo.<br /><br /> Specifica la versione minima del sistema operativo richiesta dall'applicazione.  Ad esempio, con il valore "5.1.2600.0" viene indicato che il sistema operativo è Windows XP.  Se questo parametro non è specificato, viene utilizzato il valore "4.10.0.0", che corrisponde a Windows 98 Second Edition, la versione minima del sistema operativo supportata da .NET Framework.  Se viene generato un manifesto nativo, questo parametro verrà ignorato.|  
|`OutputManifest`|Parametro di output <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Specifica il nome del file del manifesto di output generato.  Se questo parametro non è specificato, il nome del file di output viene dedotto dall'identità del manifesto generato.|  
|`Platform`|Parametro `String` facoltativo.<br /><br /> Specifica la piattaforma di destinazione dell'applicazione.  Per il parametro è possibile specificare i seguenti valori:<br /><br /> -   `AnyCPU`<br />-   `x86`<br />-   `x64`<br />-   `Itanium`<br /><br /> Se questo parametro non è specificato, viene utilizzato il valore predefinito `AnyCPU`.|  
|`Product`|Parametro `String` facoltativo.<br /><br /> Specifica il nome dell'applicazione.  Se questo parametro non è specificato, il nome viene dedotto dall'identità del manifesto generato.  Tale nome viene utilizzato per il collegamento nel menu Start e fa parte del nome visualizzato nella finestra di dialogo Installazione applicazioni.|  
|`Publisher`|Parametro `String` facoltativo.<br /><br /> Specifica l'editore dell'applicazione.  Se questo parametro non è specificato, il nome viene dedotto dall'utente registrato o dall'identità del manifesto generato.  Tale nome viene utilizzato per la cartella nel menu Start e fa parte del nome visualizzato nella finestra di dialogo Installazione applicazioni.|  
|`RequiresMinimumFramework35SP1`|Parametro `Boolean` facoltativo.<br /><br /> Se true, per l'applicazione è richiesto .NET Framework 3.5 SP1 o una versione più recente.|  
|`TargetCulture`|Parametro `String` facoltativo.<br /><br /> Identifica le impostazioni cultura dell'applicazione e specifica il campo `Language` relativo all'identità dell'assembly per il manifesto generato.  Se questo parametro non è specificato, si presuppone che l'applicazione sia indipendente dalle impostazioni cultura.|  
|`TargetFrameworkMoniker`|Parametro assetId:///String?qualifyHint=False&autoUpgrade=True facoltativo.<br /><br /> Specifica il moniker della versione di .NET Framework di destinazione.|  
|`TargetFrameworkProfile`|Parametro assetId:///String?qualifyHint=False&autoUpgrade=True facoltativo.<br /><br /> Specifica il profilo del framework di destinazione.|  
|`TargetFrameworkSubset`|Parametro assetId:///String?qualifyHint=False&autoUpgrade=True facoltativo.<br /><br /> Specifica il nome del subset di .NET Framework da utilizzare come destinazione.|  
|`TargetFrameworkVersion`|Parametro assetId:///String?qualifyHint=False&autoUpgrade=True facoltativo.<br /><br /> Specifica la versione di .NET Framework di destinazione del progetto.|  
|`TrustInfoFile`|Parametro <xref:Microsoft.Build.Framework.ITaskItem> facoltativo.<br /><br /> Indica un documento XML che specifica la sicurezza dell'applicazione.  L'elemento radice del documento XML deve essere un nodo trustInfo nello spazio dei nomi asmv2.  Se viene generato un manifesto nativo, questo parametro verrà ignorato.|  
|`UseApplicationTrust`|Parametro assetId:///Boolean?qualifyHint=False&autoUpgrade=True facoltativo.<br /><br /> Se true, le proprietà `Product`, `Publisher` e `SupportUrl` vengono scritte nel manifesto dell'applicazione.|  
  
## Note  
 Oltre ai parametri sopra elencati, questa attività eredita i parametri dalla classe <xref:Microsoft.Build.Tasks.GenerateManifestBase>, che eredita dalla classe <xref:Microsoft.Build.Utilities.Task>.  Per un elenco dei parametri della classe Task, vedere [Task Base Class](../msbuild/task-base-class.md).  
  
 Per informazioni sulle modalità di utilizzo dell'attività `GenerateDeploymentManifest`, vedere [GenerateApplicationManifest Task](../msbuild/generateapplicationmanifest-task.md).  
  
 Ai parametri relativi a dipendenze e file possono essere aggiunti metadati specifici per descrivere lo stato di distribuzione aggiuntivo per ciascun elemento.  
  
## Metadati degli elementi  
  
|Nome dei metadati|Descrizione|  
|-----------------------|-----------------|  
|`DependencyType`|Indica se la dipendenza viene pubblicata e installata con l'applicazione o se è un prerequisito.  Questi metadati sono validi per tutte le dipendenze, ma non vengono utilizzati per i file.  Per questi metadati sono disponibili i seguenti valori:<br /><br /> -   `Install`<br />-   `Prerequisite`<br /><br /> Il valore predefinito è Install.|  
|`AssemblyType`|Indica se la dipendenza è un assembly gestito o nativo.  Questi metadati sono validi per tutte le dipendenze, ma non vengono utilizzati per i file.  Per questi metadati sono disponibili i seguenti valori:<br /><br /> -   `Managed`<br />-   `Native`<br />-   `Unspecified`<br /><br /> Il valore predefinito è `Unspecified`, con cui viene indicato che il generatore del manifesto determinerà automaticamente il tipo di assembly.|  
|`Group`|Indica il gruppo per il download di file aggiuntivi su richiesta.  Il nome del gruppo è definito dall'applicazione e può essere qualsiasi stringa.  Una stringa vuota, che rappresenta il valore predefinito, indica che il file non appartiene a un gruppo di download.  I file non inclusi in un gruppo fanno parte del download iniziale dell'applicazione.  I file di un gruppo vengono scaricati solo quando esplicitamente richiesti dall'applicazione che utilizza lo spazio dei nomi <xref:System.Deployment.Application>.<br /><br /> Questi metadati sono validi per tutti i file in cui `IsDataFile` è impostato su `false` e per tutte le dipendenze in cui `DependencyType` è impostato su `Install`.|  
|`TargetPath`|Specifica la modalità di definizione del percorso nel manifesto generato.  Questo attributo è valido per tutti i file.  Se non è specificato, viene utilizzata la specifica dell'elemento.  L'attributo è valido per tutti i file e le dipendenze in cui `DependencyType` è impostato su `Install`.|  
|`IsDataFile`|Valore di metadati `Boolean` che indica se il file è un file di dati.  La particolarità dei file di dati consiste nella possibilità di eseguirne la migrazione tra gli aggiornamenti dell'applicazione.  Questi metadati sono validi solo per i file.  Il valore predefinito è `False`.|  
  
## Esempio  
 Nell'esempio riportato di seguito vengono utilizzate l'attività `GenerateApplicationManifest` per generare un manifesto dell'applicazione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] e l'attività `GenerateDeploymentManifest` per generare un manifesto di distribuzione per un'applicazione con un unico assembly.  Viene quindi utilizzata l'attività `SignFile` per firmare i manifesti.  
  
 Nell'esempio viene illustrato lo scenario di generazione di manifesti più semplice, ovvero quello in cui i manifesti [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] vengono generati per un unico programma.  Il nome e l'identità predefiniti vengono dedotti dall'assembly per il manifesto.  
  
> [!NOTE]
>  Nell'esempio riportato di seguito tutti i file binari dell'applicazione esistono già. Questo consente di concentrare l'attenzione sugli aspetti relativi alla generazione del manifesto.  Il risultato finale è una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] completamente funzionante.  
  
> [!NOTE]
>  Per ulteriori informazioni sulla proprietà `Thumbprint` utilizzata nell'attività `SignFile` di questo esempio, vedere [SignFile Task](../msbuild/signfile-task.md).  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            EntryPoint="@(EntryPoint)">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            EntryPoint="@(ApplicationManifest)">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## Esempio  
 Nell'esempio riportato di seguito le attività `GenerateApplicationManifest` e `GenerateDeploymentManifest` vengono utilizzate per generare manifesti dell'applicazione e di distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per un'applicazione con un unico assembly, specificando il nome e l'identità di tali manifesti.  
  
 Questo esempio è simile al precedente, tranne per il fatto che il nome e l'identità dei manifesti vengono specificati in modo esplicito.  Il seguente esempio è inoltre configurato come applicazione online, non come applicazione installata.  
  
> [!NOTE]
>  Nell'esempio riportato di seguito tutti i file binari dell'applicazione esistono già. Questo consente di concentrare l'attenzione sugli aspetti relativi alla generazione del manifesto.  Il risultato finale è una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] completamente funzionante.  
  
> [!NOTE]
>  Per ulteriori informazioni sulla proprietà `Thumbprint` utilizzata nell'attività `SignFile` di questo esempio, vedere [SignFile Task](../msbuild/signfile-task.md).  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            EntryPoint="@(EntryPoint)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
                AssemblyName="SimpleWinApp.application"  
                AssemblyVersion="1.0.0.0"  
                EntryPoint="@(ApplicationManifest)"  
                Install="false"  
                OutputManifest="SimpleWinApp.application">  
                <Output  
                    ItemName="DeployManifest"  
                    TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## Esempio  
 Nell'esempio riportato di seguito le attività `GenerateApplicationManifest` e `GenerateDeploymentManifest` vengono utilizzate per generare manifesti dell'applicazione e di distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] per un'applicazione con più file e assembly.  
  
> [!NOTE]
>  Nell'esempio riportato di seguito tutti i file binari dell'applicazione esistono già. Questo consente di concentrare l'attenzione sugli aspetti relativi alla generazione del manifesto.  Il risultato finale è una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] completamente funzionante.  
  
> [!NOTE]
>  Per ulteriori informazioni sulla proprietà `Thumbprint` utilizzata nell'attività `SignFile` di questo esempio, vedere [SignFile Task](../msbuild/signfile-task.md).  
  
```  
<Project DefaultTargets="Build"  
    xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe" />  
    </ItemGroup>  
  
    <PropertyGroup>  
        <Thumbprint>  
             <!-- Insert generated thumbprint here -->  
        </Thumbprint>  
        <DeployUrl>  
            <!-- Insert the deployment URL here -->  
        </DeployUrl>  
        <SupportUrl>  
            <!-- Insert the support URL here -->  
        </SupportUrl>  
    </PropertyGroup>  
  
    <Target Name="Build">  
  
    <ItemGroup>  
        <EntryPoint Include="SimpleWinApp.exe"/>  
        <Dependency Include="ClassLibrary1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <Dependency Include="ClassLibrary2.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <Group>Secondary</Group>  
        </Dependency>  
        <Dependency Include="MyAddIn1.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Install</DependencyType>  
            <TargetPath>Addins\MyAddIn1.dll</TargetPath>  
        </Dependency>  
        <Dependency Include="ClassLibrary3.dll">  
            <AssemblyType>Managed</AssemblyType>  
            <DependencyType>Prerequisite</DependencyType>  
        </Dependency>  
  
        <File Include="Text1.txt">  
            <TargetPath>Text\Text1.txt</TargetPath>  
            <Group>Text</Group>  
        </File>  
        <File Include="DataFile1.xml ">  
            <TargetPath>Data\DataFile1.xml</TargetPath>  
            <IsDataFile>true</IsDataFile>  
        </File>  
  
        <IconFile Include="Heart.ico"/>  
        <ConfigFile Include="app.config">  
            <TargetPath>SimpleWinApp.exe.config</TargetPath>  
        </ConfigFile>  
        <BaseManifest Include="app.manifest"/>  
    </ItemGroup>  
  
    <Target Name="Build">  
  
        <GenerateApplicationManifest  
            AssemblyName="SimpleWinApp.exe"  
            AssemblyVersion="1.0.0.0"  
            ConfigFile="@(ConfigFile)"  
            Dependencies="@(Dependency)"  
            Description="TestApp"  
            EntryPoint="@(EntryPoint)"  
            Files="@(File)"  
            IconFile="@(IconFile)"  
            InputManifest="@(BaseManifest)"  
            OutputManifest="SimpleWinApp.exe.manifest">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
        <GenerateDeploymentManifest  
            AssemblyName="SimpleWinApp.application"  
            AssemblyVersion="1.0.0.0"  
            DeploymentUrl="$(DeployToUrl)"  
            Description="TestDeploy"  
            EntryPoint="@(ApplicationManifest)"  
            Install="true"  
            OutputManifest="SimpleWinApp.application"  
            Product="SimpleWinApp"  
            Publisher="Microsoft"  
            SupportUrl="$(SupportUrl)"  
            UpdateEnabled="true"  
            UpdateInterval="3"  
            UpdateMode="Background"  
            UpdateUnit="weeks">  
            <Output  
                ItemName="DeployManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateDeploymentManifest>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(ApplicationManifest)"/>  
  
        <SignFile  
            CertificateThumbprint="$(Thumbprint)"  
            SigningTarget="@(DeployManifest)"/>  
  
    </Target>  
</Project>  
```  
  
## Esempio  
 Nell'esempio riportato di seguito l'attività `GenerateApplicationManifest` viene utilizzata per generare un manifesto nativo per l'applicazione Test.exe, facendo riferimento al file Alpha.dll del componente nativo e al file Bravo.dll di un componente COM isolato.  
  
 Il risultato finale è il file Test.exe.manifest, che rende distribuibile l'applicazione XCOPY grazie alla funzionalità COM senza registrazione.  
  
> [!NOTE]
>  Nell'esempio riportato di seguito tutti i file binari dell'applicazione esistono già. Questo consente di concentrare l'attenzione sugli aspetti relativi alla generazione del manifesto.  Il risultato finale è una distribuzione [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] completamente funzionante.  
  
```  
<Project DefaultTargets="Build" xmlns="http://schemas.microsoft.com/developer/msbuild/2003">  
  
    <ItemGroup>  
        <File Include="Test.exe" />  
        <Dependency Include="Alpha.dll">  
            <AssemblyType>Native</AssemblyType>  
            <DependencyType>Install</DependencyType>  
        </Dependency>  
        <ComComponent Include="Bravo.dll" />  
    </ItemGroup>  
  
    <Target Name="Build">  
        <GenerateApplicationManifest  
            AssemblyName="Test.exe"  
            AssemblyVersion="1.0.0.0"  
            Dependencies="@(Dependency)"  
            Files="@(File)"  
            IsolatedComReferences="@(ComComponent)"  
            ManifestType="Native">  
            <Output  
                ItemName="ApplicationManifest"  
                TaskParameter="OutputManifest"/>  
        </GenerateApplicationManifest>  
  
    </Target>  
</Project>  
```  
  
## Vedere anche  
 [Tasks](../msbuild/msbuild-tasks.md)   
 [GenerateDeploymentManifest Task](../msbuild/generatedeploymentmanifest-task.md)   
 [SignFile Task](../msbuild/signfile-task.md)   
 [Task Reference](../msbuild/msbuild-task-reference.md)