---
title: ID dei carichi di lavoro e dei componenti di Visual Studio Professional 2017 | Microsoft Docs
description: Usare gli ID dei carichi di lavoro e dei componenti per installare Visual Studio tramite la riga di comando o per specificarli come dipendenza in un manifesto VSIX
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 03/07/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.prod: visual-studio-dev15
ms.service: 
ms.technology:
- vs-ide-install
- vs-ide-sdk
ms.assetid: 5719032b-2c2e-416e-a281-a4573ec74e38
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: 8163a0e1230712734936b7548bef1753ee0c1d2a
ms.openlocfilehash: 1f2da4c8c70c36b3a521ac094c0bf9658897a9c0
ms.lasthandoff: 03/07/2017

---

# <a name="visual-studio-professional-2017-component-directory"></a>Elenco dei componenti di Visual Studio Professional 2017

Le tabelle in questa pagina elencano gli ID che è possibile usare per installare Visual Studio tramite la riga di comando o che è possibile specificare come dipendenza in un manifesto VSIX. Si noti che verranno aggiunti ulteriori componenti con il rilascio di aggiornamenti di Visual Studio.

Tenere presenti anche le note seguenti relative alla pagina:

* Esiste una sezione a parte per ogni carico di lavoro, seguita dall'ID del carico di lavoro e da una tabella dei componenti disponibili per il carico di lavoro.
* Per impostazione predefinita, i componenti di tipo **Obbligatorio** verranno installati quando si installa il carico di lavoro. È anche possibile scegliere di installare i componenti di tipo **Consigliato** e **Facoltativo**.
* È stata inoltre aggiunta una sezione con l'elenco dei componenti aggiuntivi non affiliati ad alcun carico di lavoro.

Quando si impostano le dipendenze nel manifesto VSIX, è necessario specificare solo gli ID dei componenti. Usare le tabelle in questa pagina per determinare le dipendenze minime dei componenti. In alcuni scenari, ciò potrebbe portare alla specifica di un solo componente da un carico di lavoro. In altri scenari è possibile che vengano specificati più componenti da un singolo carico di lavoro o più componenti da più carichi di lavoro. Per altre informazioni, vedere la pagina [Procedura: Eseguire la migrazione di progetti di estendibilità in Visual Studio 2017](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2017.md).

Per altre informazioni su come usare questi ID, vedere la pagina [Usare i parametri della riga di comando per installare Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Per un elenco di ID di componenti e carichi di lavoro per altri prodotti, vedere la pagina [ID dei carichi di lavoro e dei componenti di Visual Studio 2017](workload-and-component-ids.md).

## <a name="visual-studio-core-editor-included-with-visual-studio-professional-2017"></a>Editor principale di Visual Studio (incluso in Visual Studio Professional 2017)

**ID:** Microsoft.VisualStudio.Workload.CoreEditor

**Descrizione:** shell di base di Visual Studio, che include un editor di codice con riconoscimento della sintassi, il controllo del codice sorgente e la gestione degli elementi di lavoro.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Tipo di dipendenza
--- | --- | ---
Microsoft.VisualStudio.Component.CoreEditor | Editor principale di Visual Studio | Obbligatorio


## <a name="azure-development"></a>Sviluppo di Azure

**ID:** Microsoft.VisualStudio.Workload.Azure

**Descrizione:** Azure SDK, strumenti e progetti per lo sviluppo di app cloud e la creazione di risorse.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Tipo di dipendenza
--- | --- | ---
Microsoft.Component.MSBuild | MSBuild | Obbligatorio
Microsoft.Component.NetFX.Core.Runtime | Runtime di .NET Core | Obbligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | Obbligatorio
Microsoft.Net.Core.Component.SDK | Strumenti di sviluppo per .NET Core 1.0.1 | Obbligatorio
Microsoft.NetCore.ComponentGroup.Web | Strumenti di sviluppo per .NET Core 1.0 - 1.1 | Obbligatorio
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | Obbligatorio
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | Obbligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | Obbligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | Obbligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.Azure.Prerequisites | Prerequisiti per lo sviluppo per Azure | Obbligatorio
Component.WebSocket | WebSocket4Net | Consigliato
Microsoft.Component.Azure.DataLake.Tools | Strumenti di Azure Data Lake | Consigliato
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | Consigliato
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | Consigliato
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | Consigliato
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | Consigliato
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Consigliato
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | Consigliato
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | Consigliato
Microsoft.VisualStudio.Component.Azure.MobileAppsSdk | Azure Mobile Apps SDK | Consigliato
Microsoft.VisualStudio.Component.Azure.ResourceManager.Tools | Strumenti di base di Azure Resource Manager | Consigliato
Microsoft.VisualStudio.Component.Azure.ServiceFabric.Tools | Strumenti di Service Fabric | Consigliato
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | Consigliato
Microsoft.VisualStudio.Component.Azure.Waverton | Strumenti di base di Servizi cloud di Azure | Consigliato
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura | Consigliato
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Consigliato
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | Consigliato
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | Consigliato
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | Consigliato
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | Consigliato
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | Consigliato
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | Consigliato
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | Consigliato
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | Consigliato
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | Consigliato
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Consigliato
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Consigliato
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | Consigliato
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | Consigliato
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | Consigliato
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | Consigliato
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | Consigliato
Microsoft.VisualStudio.ComponentGroup.Azure.CloudServices | Strumenti di Servizi cloud di Azure | Consigliato
Microsoft.VisualStudio.ComponentGroup.Azure.ResourceManager.Tools | Strumenti di Azure Resource Manager | Consigliato
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | Facoltativo
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | Facoltativo
Microsoft.VisualStudio.Component.Azure.Storage.AzCopy | AzCopy di Archiviazione di Azure | Facoltativo
Microsoft.VisualStudio.Component.PowerShell.Tools | PowerShell Tools | Facoltativo
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Facoltativo


## <a name="data-storage-and-processing"></a>Archiviazione ed elaborazione dei dati

**ID:** Microsoft.VisualStudio.Workload.Data

**Descrizione:** consente di connettere, sviluppare e testare soluzioni dati con SQL Server, Azure Data Lake, Hadoop o Azure ML.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Tipo di dipendenza
--- | --- | ---
Component.Redgate.ReadyRoll | Redgate ReadyRoll | Consigliato
Component.Redgate.SQLPrompt.VsPackage | Redgate SQL Prompt | Consigliato
Component.Redgate.SQLSearch.VSExtension | Redgate SQL Search | Consigliato
Component.WebSocket | WebSocket4Net | Consigliato
Microsoft.Component.Azure.DataLake.Tools | Strumenti di Azure Data Lake | Consigliato
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | Consigliato
Microsoft.Component.MSBuild | MSBuild | Consigliato
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | Consigliato
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | Consigliato
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | Consigliato
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Consigliato
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | Consigliato
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | Consigliato
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Consigliato
Microsoft.VisualStudio.Component.Azure.AuthoringTools | Strumenti di creazione di Azure | Consigliato
Microsoft.VisualStudio.Component.Azure.ClientLibs | Librerie di Azure per .NET | Consigliato
Microsoft.VisualStudio.Component.Azure.Compute.Emulator | Emulatore di calcolo di Azure | Consigliato
Microsoft.VisualStudio.Component.Azure.Storage.Emulator | Emulatore di archiviazione di Azure | Consigliato
Microsoft.VisualStudio.Component.Azure.Waverton | Strumenti di base di Servizi cloud di Azure | Consigliato
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | Consigliato
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | Consigliato
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Consigliato
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | Consigliato
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | Consigliato
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | Consigliato
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | Consigliato
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | Consigliato
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | Consigliato
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | Consigliato
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | Consigliato
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | Consigliato
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | Consigliato
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | Consigliato
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | Consigliato
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Consigliato
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Consigliato
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | Consigliato
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | Consigliato
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | Consigliato
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | Consigliato
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | Consigliato
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | Consigliato
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | Facoltativo


## <a name="net-desktop-development"></a>Sviluppo per desktop .NET

**ID:** Microsoft.VisualStudio.Workload.ManagedDesktop

**Descrizione:** consente di compilare applicazioni WPF, Windows Form e console con .NET Framework.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Tipo di dipendenza
--- | --- | ---
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | Obbligatorio
Microsoft.Component.MSBuild | MSBuild | Obbligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | Obbligatorio
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debugger JIT | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Strumenti per sviluppo di applicazioni desktop .NET | Obbligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | Obbligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | Obbligatorio
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | Obbligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | Obbligatorio
Microsoft.ComponentGroup.Blend | Blend per Visual Studio | Consigliato
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | Consigliato
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | Consigliato
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | Consigliato
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura | Consigliato
Microsoft.VisualStudio.Component.EntityFramework | Strumenti di Entity Framework 6 | Consigliato
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Consigliato
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | Consigliato
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | Facoltativo
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | Facoltativo
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | Facoltativo
Microsoft.Net.Core.Component.SDK | Strumenti di sviluppo per .NET Core 1.0.1 | Facoltativo
Microsoft.NetCore.ComponentGroup.DevelopmentTools | Strumenti di sviluppo per .NET Core 1.0 - 1.1 | Facoltativo
Microsoft.VisualStudio.Component.CodeClone | Clone di codice | Facoltativo
Microsoft.VisualStudio.Component.CodeMap | Mappa codice | Facoltativo
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Convalida delle dipendenze in tempo reale | Facoltativo
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | Facoltativo
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | Facoltativo
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Facoltativo
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | Facoltativo
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | Facoltativo
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Facoltativo
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Facoltativo
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | Facoltativo
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Strumenti per architettura e analisi | Facoltativo


## <a name="game-development-with-unity"></a>Sviluppo di giochi con Unity

**ID:** Microsoft.VisualStudio.Workload.ManagedGame

**Descrizione:** consente di creare giochi 2D e 3D con Unity, un potente ambiente di sviluppo multipiattaforma.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Tipo di dipendenza
--- | --- | ---
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | Obbligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | Obbligatorio
Microsoft.VisualStudio.Component.Unity | Visual Studio Tools per Unity | Obbligatorio
Component.UnityEngine | Editor Unity | Consigliato


## <a name="linux-development-with-c"></a>Sviluppo di applicazioni Linux con C++

**ID:** Microsoft.VisualStudio.Workload.NativeCrossPlat

**Descrizione:** consente di creare ed eseguire il debug di applicazioni eseguite in un ambiente Linux.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Tipo di dipendenza
--- | --- | ---
Component.MDD.Linux | Visual C++ for Linux Development | Obbligatorio
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base di Visual Studio C++ | Obbligatorio
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | Obbligatorio


## <a name="desktop-development-with-c"></a>Sviluppo di applicazioni desktop con C++

**ID:** Microsoft.VisualStudio.Workload.NativeDesktop

**Descrizione:** consente di compilare applicazioni di Windows classiche usando tutta la potenza del set di strumenti Microsoft C++ e ATL, oltre a funzionalità facoltative quali MFC e C++/CLI.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Tipo di dipendenza
--- | --- | ---
Microsoft.Component.MSBuild | MSBuild | Obbligatorio
Microsoft.VisualStudio.Component.ClassDesigner | Progettazione classi | Obbligatorio
Microsoft.VisualStudio.Component.CodeMap | Mappa codice | Obbligatorio
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debugger JIT | Obbligatorio
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | Obbligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Obbligatorio
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | Obbligatorio
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base di Visual Studio C++ | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Native | Strumenti per architettura per C++ | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Core | Funzionalità desktop di base di Visual C++ | Obbligatorio
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | Consigliato
Microsoft.VisualStudio.Component.Graphics.Win81 | Graphics Tools Windows 8.1 SDK | Consigliato
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | Consigliato
Microsoft.VisualStudio.Component.VC.CMake.Project | Strumenti Visual C++ per CMake | Consigliato
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Strumenti di profilatura C++ | Consigliato
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Set di strumenti VC++ 2017 versione 141 (x86, x64) | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | Consigliato
Component.Incredibuild | IncrediBuild | Facoltativo
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | Facoltativo
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Facoltativo
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Facoltativo
Microsoft.VisualStudio.Component.VC.140 | Set di strumenti VC++ 2015.3 versione 140 (x86, x64) | Facoltativo
Microsoft.VisualStudio.Component.VC.ATL | Supporto per ATL in C++ | Facoltativo
Microsoft.VisualStudio.Component.VC.ATLMFC | Supporto di MFC e ATL (x86 e x64) | Facoltativo
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (sperimentale) | Facoltativo
Microsoft.VisualStudio.Component.VC.CLI.Support | Supporto C++/CLI | Facoltativo
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduli di libreria standard | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | Facoltativo
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | Facoltativo
Microsoft.VisualStudio.Component.WinXP | Supporto Windows XP per C++ | Facoltativo
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK e UCRT SDK | Facoltativo
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.WinXP | Supporto Windows XP per C++ | Facoltativo


## <a name="game-development-with-c"></a>Sviluppo di giochi con C++

**ID:** Microsoft.VisualStudio.Workload.NativeGame

**Descrizione:** consente di sfruttare tutte le funzionalità di C++ per compilare giochi professionali basati su DirectX, Unreal o Cocos2d.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Tipo di dipendenza
--- | --- | ---
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | Obbligatorio
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | Consigliato
Microsoft.VisualStudio.Component.Graphics.Win81 | Graphics Tools Windows 8.1 SDK | Consigliato
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | Consigliato
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base di Visual Studio C++ | Consigliato
Microsoft.VisualStudio.Component.VC.DiagnosticTools | Strumenti di profilatura C++ | Consigliato
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Set di strumenti VC++ 2017 versione 141 (x86, x64) | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | Consigliato
Component.Cocos | Cocos | Facoltativo
Component.Incredibuild | IncrediBuild | Facoltativo
Component.Unreal | Programma di installazione di Unreal Engine | Facoltativo
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | Facoltativo
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | Facoltativo
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | Facoltativo
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | Facoltativo
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Facoltativo
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Facoltativo
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | Facoltativo
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | Facoltativo
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | Facoltativo
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | Facoltativo
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | Facoltativo
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | Facoltativo
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | Facoltativo
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK e UCRT SDK | Facoltativo


## <a name="mobile-development-with-c"></a>Sviluppo di app per dispositivi mobili con C++

**ID:** Microsoft.VisualStudio.Workload.NativeMobile

**Descrizione:** consente di compilare applicazioni multipiattaforma per iOS, Android o Windows con C++.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Tipo di dipendenza
--- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base di Visual Studio C++ | Obbligatorio
Component.Android.NDK.R13B | Android NDK (R13B) | Consigliato
Component.Android.SDK19 | Programma di installazione di Android SDK (livelli API 19 e 21) | Consigliato
Component.Android.SDK22 | Programma di installazione di Android SDK (livello API 22) | Consigliato
Component.Ant | Apache Ant (1.9.3) | Consigliato
Component.MDD.Android | Strumenti di sviluppo per app Android in C++ | Consigliato
Component.Android.Emulator | Emulatore di Visual Studio per Android | Facoltativo
Component.Android.NDK.R11C | Android NDK (R11C) | Facoltativo
Component.Android.NDK.R11C_3264 | Android NDK (R11C) (32 bit) | Facoltativo
Component.Android.NDK.R12B | Android NDK (R12B) | Facoltativo
Component.Android.NDK.R12B_3264 | Android NDK (R12B) (a&32; bit) | Facoltativo
Component.Android.NDK.R13B_3264 | Android NDK (R13B) (a&32; bit) | Facoltativo
Component.Android.SDK23 | Programma di installazione di Android SDK (livello API 23) | Facoltativo
Component.Google.Android.Emulator.API23.V2 | Emulatore Google Android (API livello 23) | Facoltativo
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | Facoltativo
Component.Incredibuild | IncrediBuild | Facoltativo
Component.JavaJDK | Java SE Development Kit (8.0.920.14) | Facoltativo
Component.MDD.IOS | Strumenti di sviluppo per app iOS in C++ | Facoltativo


## <a name="net-core-cross-platform-development"></a>Sviluppo multipiattaforma .NET Core

**ID:** Microsoft.VisualStudio.Workload.NetCoreTools

**Descrizione:** consente di creare applicazioni multipiattaforma con .NET Core, ASP.NET Core, HTML, JavaScript e CSS

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Tipo di dipendenza
--- | --- | ---
Component.WebSocket | WebSocket4Net | Obbligatorio
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | Obbligatorio
Microsoft.Component.MSBuild | MSBuild | Obbligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | Obbligatorio
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | Obbligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | Obbligatorio
Microsoft.Net.Core.Component.SDK | Strumenti di sviluppo per .NET Core 1.0.1 | Obbligatorio
Microsoft.NetCore.ComponentGroup.Web | Strumenti di sviluppo per .NET Core 1.0 - 1.1 | Obbligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Obbligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | Obbligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | Obbligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | Obbligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | Obbligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | Obbligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Obbligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Obbligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | Obbligatorio
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | Obbligatorio
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | Obbligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | Obbligatorio
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | Obbligatorio
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | Obbligatorio
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | Consigliato


## <a name="mobile-development-with-net"></a>Sviluppo di applicazioni per dispositivi mobili con .NET

**ID:** Microsoft.VisualStudio.Workload.NetCrossPlat

**Descrizione:** consente di compilare applicazioni multipiattaforma per iOS, Android o Windows con Xamarin.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Tipo di dipendenza
--- | --- | ---
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | Obbligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | Obbligatorio
Component.Android.NDK.R13B | Android NDK (R13B) | Consigliato
Component.Android.SDK23 | Programma di installazione di Android SDK (livello API 23) | Consigliato
Component.Google.Android.Emulator.API23.V2 | Emulatore Google Android (API livello 23) | Consigliato
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | Consigliato
Component.JavaJDK | Java SE Development Kit (8.0.920.14) | Consigliato
Component.Xamarin | Xamarin | Consigliato
Component.Xamarin.Inspector | Xamarin Workbooks | Consigliato
Component.Xamarin.Profiler | Xamarin Profiler | Consigliato
Component.Xamarin.RemotedSimulator | Xamarin Remoted Simulator | Consigliato
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | Consigliato
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | Consigliato
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | Consigliato
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | Consigliato
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | Consigliato
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | Facoltativo
Microsoft.Component.NetFX.Native | .NET Native | Facoltativo
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Facoltativo
Microsoft.VisualStudio.Component.CodeClone | Clone di codice | Facoltativo
Microsoft.VisualStudio.Component.CodeMap | Mappa codice | Facoltativo
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Convalida delle dipendenze in tempo reale | Facoltativo
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura | Facoltativo
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | Facoltativo
Microsoft.VisualStudio.Component.Graphics | Editor di immagini e modelli 3D | Facoltativo
Microsoft.VisualStudio.Component.Phone.Emulator | Emulatore Windows 10 Mobile (Anniversary Edition) | Facoltativo
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | Facoltativo
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | Facoltativo
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Facoltativo
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | Facoltativo
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Strumenti per architettura e analisi | Facoltativo
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Strumenti della piattaforma UWP (Universal Windows Platform) per Xamarin (2.0) | Facoltativo


## <a name="aspnet-and-web-development"></a>Sviluppo ASP.NET e Web

**ID:** Microsoft.VisualStudio.Workload.NetWeb

**Descrizione:** consente di creare applicazioni Web con ASP.NET, ASP.NET Core, HTML, JavaScript e CSS.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Tipo di dipendenza
--- | --- | ---
Component.WebSocket | WebSocket4Net | Obbligatorio
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | Obbligatorio
Microsoft.Component.MSBuild | MSBuild | Obbligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | Obbligatorio
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | Obbligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | Obbligatorio
Microsoft.Net.Core.Component.SDK | Strumenti di sviluppo per .NET Core 1.0.1 | Obbligatorio
Microsoft.NetCore.ComponentGroup.Web | Strumenti di sviluppo per .NET Core 1.0 - 1.1 | Obbligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Obbligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | Obbligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | Obbligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | Obbligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | Obbligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | Obbligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Obbligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Obbligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | Obbligatorio
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | Obbligatorio
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | Obbligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | Obbligatorio
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | Obbligatorio
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | Obbligatorio
Microsoft.Net.Component.4.5.1.TargetingPack | .NET Framework 4.5.1 Targeting Pack | Consigliato
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | Consigliato
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | Consigliato
Microsoft.Net.ComponentGroup.TargetingPacks.Common | Strumenti di sviluppo per .NET Framework 4 - 4.6 | Consigliato
Microsoft.VisualStudio.Component.CloudExplorer | Cloud Explorer | Consigliato
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura | Consigliato
Microsoft.VisualStudio.Component.DockerTools | Strumenti di sviluppo contenitori | Consigliato
Microsoft.VisualStudio.Component.EntityFramework | Strumenti di Entity Framework 6 | Consigliato
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Consigliato
Microsoft.VisualStudio.Component.LiveUnitTesting | Live Unit Testing | Consigliato
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Consigliato
Microsoft.Net.Component.4.6.2.SDK | .NET Framework 4.6.2 SDK | Facoltativo
Microsoft.Net.Component.4.6.2.TargetingPack | .NET Framework 4.6.2 Targeting Pack | Facoltativo
Microsoft.Net.ComponentGroup.4.6.2.DeveloperTools | Strumenti di sviluppo per .NET Framework 4.6.2 | Facoltativo
Microsoft.VisualStudio.Component.ClassDesigner | Progettazione classi | Facoltativo
Microsoft.VisualStudio.Component.CodeClone | Clone di codice | Facoltativo
Microsoft.VisualStudio.Component.CodeMap | Mappa codice | Facoltativo
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Convalida delle dipendenze in tempo reale | Facoltativo
Microsoft.VisualStudio.Component.FSharp | Supporto per il linguaggio F# | Facoltativo
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | Facoltativo
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Strumenti per architettura e analisi | Facoltativo
Microsoft.VisualStudio.Web.Mvc4.ComponentGroup | ASP.NET MVC 4 | Facoltativo


## <a name="nodejs-development"></a>Sviluppo Node.js

**ID:** Microsoft.VisualStudio.Workload.Node

**Descrizione:** consente di compilare applicazioni di rete scalabili con Node.js, un runtime JavaScript basato su eventi asincroni.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Tipo di dipendenza
--- | --- | ---
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | Obbligatorio
Microsoft.VisualStudio.Component.Node.Tools | Supporto per Node.js | Obbligatorio
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | Obbligatorio
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | Obbligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | Consigliato
Microsoft.VisualStudio.Component.Git | GIT per Windows | Consigliato
Component.WebSocket | WebSocket4Net | Facoltativo
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Facoltativo
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura | Facoltativo
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | Facoltativo
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | Facoltativo
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base di Visual Studio C++ | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Set di strumenti VC++ 2017 versione 141 (x86, x64) | Facoltativo


## <a name="officesharepoint-development"></a>Sviluppo per Office/SharePoint

**ID:** Microsoft.VisualStudio.Workload.Office

**Descrizione:** consente di creare componenti aggiuntivi per Office e SharePoint, soluzioni SharePoint e componenti aggiuntivi VSTO usando C#, VB e JavaScript.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Tipo di dipendenza
--- | --- | ---
Component.WebSocket | WebSocket4Net | Obbligatorio
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | Obbligatorio
Microsoft.Component.MSBuild | MSBuild | Obbligatorio
Microsoft.Net.Component.4.5.2.TargetingPack | .NET Framework 4.5.2 Targeting Pack | Obbligatorio
Microsoft.Net.Component.4.5.TargetingPack | .NET Framework 4.5 Targeting Pack | Obbligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Obbligatorio
Microsoft.Net.Component.4.TargetingPack | .NET Framework 4 Targeting Pack | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | Obbligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Obbligatorio
Microsoft.VisualStudio.Component.Common.Azure.Tools | Strumenti di connettività e pubblicazione | Obbligatorio
Microsoft.VisualStudio.Component.Debugger.JustInTime | Debugger JIT | Obbligatorio
Microsoft.VisualStudio.Component.IISExpress | IIS Express  | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Core | Componenti di base Carico di lavoro desktop gestito | Obbligatorio
Microsoft.VisualStudio.Component.ManagedDesktop.Prerequisites | Strumenti per sviluppo di applicazioni desktop .NET | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | Obbligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | Obbligatorio
Microsoft.VisualStudio.Component.Sharepoint.Tools | Office Developer Tools per Visual Studio | Obbligatorio
Microsoft.VisualStudio.Component.SQL.ADAL | Runtime di SQL ADAL | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CMDUtils | SQL Server Command Line Utilities | Obbligatorio
Microsoft.VisualStudio.Component.SQL.DataSources | Origini dati per supporto SQL Server | Obbligatorio
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | Obbligatorio
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Obbligatorio
Microsoft.VisualStudio.Component.SQL.SSDT | SQL Server Data Tools | Obbligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | Obbligatorio
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | Obbligatorio
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | Obbligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | Obbligatorio
Microsoft.VisualStudio.Component.Wcf.Tooling | Windows Communication Foundation | Obbligatorio
Microsoft.VisualStudio.Component.Web | Strumenti di sviluppo ASP.NET e Web | Obbligatorio
Microsoft.VisualStudio.Component.WebDeploy | Distribuzione Web | Obbligatorio
Microsoft.VisualStudio.Component.Workflow | Windows Workflow Foundation | Obbligatorio
Microsoft.VisualStudio.Component.TeamOffice | Visual Studio Tools per Office (VSTO) | Consigliato
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Facoltativo


## <a name="universal-windows-platform-development"></a>Sviluppo della piattaforma UWP (Universal Windows Platform)

**ID:** Microsoft.VisualStudio.Workload.Universal

**Descrizione:** consente di creare applicazioni per la piattaforma UWP (Universal Windows Platform) con C#, VB, JavaScript o facoltativamente C++.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Tipo di dipendenza
--- | --- | ---
Component.WebSocket | WebSocket4Net | Obbligatorio
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | Obbligatorio
Microsoft.Component.NetFX.Native | .NET Native | Obbligatorio
Microsoft.ComponentGroup.Blend | Blend per Visual Studio | Obbligatorio
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Obbligatorio
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura | Obbligatorio
Microsoft.VisualStudio.Component.Graphics | Editor di immagini e modelli 3D | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | Obbligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | Obbligatorio
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | Obbligatorio
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | Obbligatorio
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | Obbligatorio
Microsoft.VisualStudio.Component.UWP.Support | Strumenti della piattaforma UWP (Universal Windows Platform) (2.0) | Obbligatorio
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | Obbligatorio
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Strumenti della piattaforma UWP (Universal Windows Platform) per Cordova (2.0) | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.UWP.Xamarin | Strumenti della piattaforma UWP (Universal Windows Platform) per Xamarin (2.0) | Obbligatorio
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Consigliato
Microsoft.Component.VC.Runtime.OSSupport | Runtime di Visual C++ per la piattaforma UWP | Facoltativo
Microsoft.VisualStudio.Component.CodeClone | Clone di codice | Facoltativo
Microsoft.VisualStudio.Component.CodeMap | Mappa codice | Facoltativo
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Convalida delle dipendenze in tempo reale | Facoltativo
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | Facoltativo
Microsoft.VisualStudio.Component.Graphics.Tools | Debugger grafica e profiler GPU per DirectX | Facoltativo
Microsoft.VisualStudio.Component.Graphics.Win81 | Graphics Tools Windows 8.1 SDK | Facoltativo
Microsoft.VisualStudio.Component.Phone.Emulator | Emulatore Windows 10 Mobile (Anniversary Edition) | Facoltativo
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | Facoltativo
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Facoltativo
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base di Visual Studio C++ | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.ARM | Compilatori e librerie di Visual C++ per ARM | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Set di strumenti VC++ 2017 versione 141 (x86, x64) | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | Facoltativo
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Strumenti per architettura e analisi | Facoltativo
Microsoft.VisualStudio.ComponentGroup.UWP.VC | Strumenti della piattaforma UWP (Universal Windows Platform) per C++ | Facoltativo


## <a name="visual-studio-extension-development"></a>Sviluppo di estensioni di Visual Studio

**ID:** Microsoft.VisualStudio.Workload.VisualStudioExtension

**Descrizione:** consente di creare componenti aggiuntivi ed estensioni per Visual Studio, inclusi nuovi comandi, analizzatori del codice e finestre degli strumenti.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Tipo di dipendenza
--- | --- | ---
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | Obbligatorio
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | Obbligatorio
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | Obbligatorio
Microsoft.Net.ComponentGroup.DevelopmentPrerequisites | Strumenti di sviluppo per .NET Framework 4.6.1 | Obbligatorio
Microsoft.VisualStudio.Component.NuGet | Gestione pacchetti NuGet | Obbligatorio
Microsoft.VisualStudio.Component.PortableLibrary | Targeting Pack per libreria portabile .NET | Obbligatorio
Microsoft.VisualStudio.ComponentGroup.VisualStudioExtension.Prerequisites | Prerequisiti per lo sviluppo di estensioni di Visual Studio | Obbligatorio
Microsoft.VisualStudio.Component.CodeClone | Clone di codice | Consigliato
Microsoft.VisualStudio.Component.CodeMap | Mappa codice | Consigliato
Microsoft.VisualStudio.Component.DependencyValidation.Enterprise | Convalida delle dipendenze in tempo reale | Consigliato
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura | Consigliato
Microsoft.VisualStudio.Component.GraphDocument | Editor DGML | Consigliato
Microsoft.VisualStudio.Component.IntelliTrace.FrontEnd | IntelliTrace | Consigliato
Microsoft.VisualStudio.Component.SQL.LocalDB.Runtime | LocalDB per SQL Server Express 2016 | Consigliato
Microsoft.VisualStudio.Component.SQL.NCLI | SQL Server Native Client | Consigliato
Microsoft.VisualStudio.ComponentGroup.ArchitectureTools.Managed | Strumenti per architettura e analisi | Consigliato
Component.Dotfuscator | PreEmptive Protection - Dotfuscator | Facoltativo
Microsoft.Component.MSBuild | MSBuild | Facoltativo
Microsoft.Component.VC.Runtime.OSSupport | Runtime di Visual C++ per la piattaforma UWP | Facoltativo
Microsoft.Net.Component.4.6.TargetingPack | .NET Framework 4.6 Targeting Pack | Facoltativo
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Facoltativo
Microsoft.VisualStudio.Component.ClassDesigner | Progettazione classi | Facoltativo
Microsoft.VisualStudio.Component.DslTools | Modeling SDK | Facoltativo
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | Facoltativo
Microsoft.VisualStudio.Component.Roslyn.LanguageServices | C# e Visual Basic | Facoltativo
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | Facoltativo
Microsoft.VisualStudio.Component.TextTemplating | Trasformazione modelli di testo | Facoltativo
Microsoft.VisualStudio.Component.VC.ATL | Supporto per ATL in C++ | Facoltativo
Microsoft.VisualStudio.Component.VC.ATLMFC | Supporto di MFC e ATL (x86 e x64) | Facoltativo
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base di Visual Studio C++ | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Set di strumenti VC++ 2017 versione 141 (x86, x64) | Facoltativo
Microsoft.VisualStudio.Component.VSSDK | Visual Studio SDK | Facoltativo


## <a name="mobile-development-with-javascript"></a>Sviluppo di app per dispositivi mobili con JavaScript

**ID:** Microsoft.VisualStudio.Workload.WebCrossPlat

**Descrizione:** consente di creare app Android, iOS e della piattaforma UWP con Strumenti per Apache Cordova.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Tipo di dipendenza
--- | --- | ---
Component.CordovaToolset.6.3.1 | Set di strumenti di Cordova 6.3.1 | Obbligatorio
Component.WebSocket | WebSocket4Net | Obbligatorio
Microsoft.VisualStudio.Component.Cordova | Sviluppo di app per dispositivi mobili con funzionalità di base di JavaScript | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.Diagnostics | Diagnostica di JavaScript | Obbligatorio
Microsoft.VisualStudio.Component.JavaScript.TypeScript | Supporto per linguaggi JavaScript e TypeScript | Obbligatorio
Microsoft.VisualStudio.Component.TypeScript.2.1 | TypeScript 2.1 SDK | Obbligatorio
Component.Android.SDK23 | Programma di installazione di Android SDK (livello API 23) | Facoltativo
Component.Google.Android.Emulator.API23.V2 | Emulatore Google Android (API livello 23) | Facoltativo
Component.HAXM | Intel Hardware Accelerated Execution Manager (HAXM) | Facoltativo
Component.JavaJDK | Java SE Development Kit (8.0.920.14) | Facoltativo
Microsoft.Component.ClickOnce | Pubblicazione ClickOnce | Facoltativo
Microsoft.Component.NetFX.Native | .NET Native | Facoltativo
Microsoft.VisualStudio.Component.AppInsights.Tools | Developer Analytics Tools | Facoltativo
Microsoft.VisualStudio.Component.DiagnosticTools | Strumenti di profilatura | Facoltativo
Microsoft.VisualStudio.Component.Git | GIT per Windows | Facoltativo
Microsoft.VisualStudio.Component.Graphics | Editor di immagini e modelli 3D | Facoltativo
Microsoft.VisualStudio.Component.Phone.Emulator | Emulatore Windows 10 Mobile (Anniversary Edition) | Facoltativo
Microsoft.VisualStudio.Component.SQL.CLR | Tipi di dati CLR per SQL Server | Facoltativo
Microsoft.VisualStudio.Component.VisualStudioData | Origini dati e riferimenti al servizio | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | Facoltativo
Microsoft.VisualStudio.ComponentGroup.UWP.Cordova | Strumenti della piattaforma UWP (Universal Windows Platform) per Cordova (2.0) | Facoltativo

## <a name="unaffiliated-components"></a>Componenti non affiliati

Questi sono i componenti non inclusi in alcun carico di lavoro, che possono però essere selezionati come un singolo componente.

ID componente | Nome
--- | ---
Component.GitHub.VisualStudio | Estensione GitHub per Visual Studio
Microsoft.Component.Blend.SDK.WPF | Blend for Visual Studio SDK per .NET
Microsoft.Component.HelpViewer | Help Viewer
Microsoft.Net.Component.3.5.DeveloperTools | Strumenti di sviluppo per .NET Framework 3.5
Microsoft.VisualStudio.Component.DependencyValidation.Community | Convalida delle dipendenze
Microsoft.VisualStudio.Component.LinqToSql | Strumenti di LINQ to SQL
Microsoft.VisualStudio.Component.TestTools.Core | Funzionalità di base degli strumenti di test
Microsoft.VisualStudio.Component.TypeScript.2.0 | TypeScript 2.0 SDK

## <a name="see-also"></a>Vedere anche

* [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)
* [Guida di Visual Studio Administrator](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
* [Creare un'installazione offline di Visual Studio](create-an-offline-installation-of-visual-studio.md)

