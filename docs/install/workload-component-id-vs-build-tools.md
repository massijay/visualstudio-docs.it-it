---
title: ID dei carichi di lavoro e dei componenti di Visual Studio Build Tools 2017 | Microsoft Docs
description: Usare gli ID dei carichi di lavoro e dei componenti di Visual Studio per creare applicazioni basate su Windows classiche
keywords: 
author: TerryGLee
ms.author: tglee
manager: ghogen
ms.date: 05/10/2017
ms.topic: article
helpviewer_keywords:
- workload ID, Visual Studio
- component ID, Visual Studio
- install Visual Studio, administrator guide
ms.prod: visual-studio-dev15
ms.service: 
ms.technology:
- vs-ide-install
ms.assetid: b99298df-0280-47fc-af73-44cd7a8ac553
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 054126ddbdc9f0144983a1ef21fa43875699cbee
ms.openlocfilehash: 1147438d12d754233f6205de4a5d37920cb5b66a
ms.contentlocale: it-it
ms.lasthandoff: 05/10/2017

---

# <a name="visual-studio-build-tools-2017-component-directory"></a>Elenco dei componenti di Visual Studio Build Tools 2017

Le tabelle in questa pagina elencano gli ID che è possibile usare per installare Visual Studio tramite la riga di comando. Si noti che verranno aggiunti ulteriori componenti con il rilascio di aggiornamenti di Visual Studio.

Tenere presenti anche le note seguenti relative a questa pagina:

* Esiste una sezione a parte per ogni carico di lavoro, seguita dall'ID del carico di lavoro e da una tabella dei componenti disponibili per il carico di lavoro.
* Per impostazione predefinita, i componenti di tipo **Obbligatorio** verranno installati quando si installa il carico di lavoro. È anche possibile scegliere di installare i componenti di tipo **Consigliato** e **Facoltativo**.
* È stata inoltre aggiunta una sezione con l'elenco dei componenti aggiuntivi non affiliati ad alcun carico di lavoro.

Per altre informazioni su come usare questi ID, vedere la pagina [Usare i parametri della riga di comando per installare Visual Studio 2017](use-command-line-parameters-to-install-visual-studio.md). Per un elenco di ID di componenti e carichi di lavoro per altri prodotti, vedere la pagina [ID dei carichi di lavoro e dei componenti di Visual Studio 2017](workload-and-component-ids.md).

## <a name="msbuild-tools"></a>Strumenti MSBuild

**ID:** Microsoft.VisualStudio.Workload.MSBuildTools

**Descrizione:** fornisce gli strumenti necessari per creare applicazioni basate su MSBuild.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.Component.MSBuild | MSBuild | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.CoreBuildTools | Funzionalità di base di Visual Studio Build Tools | 15.0.26228.0 | Obbligatorio
Microsoft.VisualStudio.Component.Roslyn.Compiler | Compilatori Roslyn per C# e Visual Basic | 15.0.26208.0 | Obbligatorio


## <a name="visual-c-build-tools"></a>Strumenti di compilazione Visual C++

**ID:** Microsoft.VisualStudio.Workload.VCTools

**Descrizione:** consente di compilare applicazioni di Windows classiche usando tutta la potenza del set di strumenti Microsoft C++ e ATL, oltre a funzionalità facoltative quali MFC e C++/CLI.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Component.VC.CoreBuildTools | Funzionalità di base per Visual C++ Build Tools | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.Windows10SDK | Windows Universal C Runtime | 15.0.26208.0 | Obbligatorio
Microsoft.VisualStudio.Component.VC.CMake.Project | Strumenti Visual C++ per CMake | 15.0.26208.0 | Consigliato
Microsoft.VisualStudio.Component.Windows10SDK.15063.Desktop | Windows 10 SDK (10.0.15063.0) per app desktop C++ x86 e x64 | 15.0.26403.0 | Consigliato
Microsoft.Component.VC.Runtime.UCRTSDK | Windows Universal CRT SDK | 15.0.26208.0 | Facoltativo
Microsoft.Net.Component.4.6.1.SDK | .NET Framework 4.6.1 SDK | 15.0.26208.0 | Facoltativo
Microsoft.Net.Component.4.6.1.TargetingPack | .NET Framework 4.6.1 Targeting Pack | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Static.Analysis.Tools | Strumenti per analisi statica | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.ATL | Supporto per ATL in C++ | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.ATLMFC | Supporto di MFC e ATL (x86 e x64) | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.ClangC2 | Clang/C2 (sperimentale) | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.CLI.Support | Supporto C++/CLI | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.CoreIde | Funzionalità di base di Visual Studio C++ | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.Modules.x86.x64 | Moduli di libreria standard | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.VC.Tools.x86.x64 | Set di strumenti VC++ 2017 versione 141 (x86, x64) | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10240 | Windows 10 SDK (10.0.10240.0) | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.10586 | Windows 10 SDK (10.0.10586.0) | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows10SDK.14393 | Windows 10 SDK (10.0.14393.0) | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.Component.Windows81SDK | Windows 8.1 SDK | 15.0.26208.0 | Facoltativo
Microsoft.VisualStudio.ComponentGroup.NativeDesktop.Win81 | Windows 8.1 SDK e UCRT SDK | 15.0.26208.0 | Facoltativo


## <a name="web-development-build-tools"></a>Strumenti di compilazione sviluppo Web

**ID:** Microsoft.VisualStudio.Workload.WebBuildTools

**Descrizione:** attività e destinazioni di MSBuild per compilare applicazioni Web.

### <a name="components-included-by-this-workload"></a>Componenti inclusi per questo carico di lavoro

ID componente | Nome | Versione | Tipo di dipendenza
--- | --- | --- | ---
Microsoft.VisualStudio.Web.BuildTools.ComponentGroup | Strumenti di compilazione sviluppo Web | 15.0.26323.1 | Obbligatorio
## <a name="unaffiliated-components"></a>Componenti non affiliati

Questi sono i componenti non inclusi in alcun carico di lavoro, che possono però essere selezionati come un singolo componente.

ID componente | Nome | Versione
--- | --- | ---
N/D | n/d | N/D


## <a name="see-also"></a>Vedere anche

* [ID dei carichi di lavoro e dei componenti di Visual Studio](workload-and-component-ids.md)
* [Guida dell'amministratore di Visual Studio](visual-studio-administrator-guide.md)
* [Usare i parametri della riga di comando per installare Visual Studio](use-command-line-parameters-to-install-visual-studio.md)
  * [Esempi di parametri della riga di comando](command-line-parameter-examples.md)
* [Creare un'installazione offline di Visual Studio](create-an-offline-installation-of-visual-studio.md)
