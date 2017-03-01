---
title: "Novità di Visual Studio 2015 SDK | Documenti di Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c64aac80-a411-463f-b7bd-8b7607a52ece
caps.latest.revision: 13
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
ms.sourcegitcommit: 512014c5070e4314ad2b7d0e8c5c404c43f32cd9
ms.openlocfilehash: 8d77fce54b12b90f6a2632fd1c1741990be42a08
ms.lasthandoff: 02/22/2017

---
# <a name="what39s-new-in-the-visual-studio-2015-sdk"></a>Novità di Visual Studio 2015 SDK
Visual Studio SDK presenta le seguenti funzionalità nuove e aggiornate per Visual Studio 2015, aggiornato di Visual Studio 2015 e Visual Studio 2017.  
  
## <a name="vs-2015-sdk-update-1"></a>Visual Studio 2015 SDK Update 1  
 Aggiornamento 1 include gli strumenti per l'estensione funzionano bene con combinazioni di colori e il servizio di immagini di Visual Studio.  
  
 Questi argomenti sono sotto il [VSSDK utilità](../extensibility/internals/vssdk-utilities.md) sezione:  
  
-   Il [gli strumenti dei temi di colore](../extensibility/internals/color-theming-tools.md) consentono di creare e modificare i colori personalizzati per Visual Studio.  
  
-   Il [immagine servizio strumenti](../extensibility/internals/image-service-tools.md) è possibile utilizzare Visual Studio manifesto dei file di immagine.  
  
## <a name="new-way-to-add-the-visual-studio-sdk-to-visual-studio"></a>Nuovo modo per aggiungere il SDK di Visual Studio per Visual Studio  
 A partire da Visual Studio 2015, non è necessario scaricare separatamente il SDK di Visual Studio. In alternativa, è possibile installarlo come parte del processo di installazione normale, o è possibile scegliere di installarlo in un secondo momento. Quando si apre o si crea una soluzione VSIX, Visual Studio verrà chiesto di installare gli strumenti di Visual Studio Extensibility. Per ulteriori informazioni, vedere [l'installazione di Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).  
  
## <a name="new-ways-of-creating-extensions"></a>Nuove modalità di creazione di estensioni  
 A partire da Visual Studio 2015 SDK, sono diverse opzioni per la creazione di estensioni, a seconda del linguaggio di programmazione si utilizza.  
  
### <a name="visual-c-and-visual-basic"></a>Visual C# e Visual Basic  
 Per c# e Visual Basic, esiste una vasta gamma di modelli di elemento di progetto che consentono di creare package VS, i comandi di menu, finestre degli strumenti, classificatori editor, editor grafici ed estensioni margine dell'editor. È possibile aggiungere uno o tutti questi elementi per il progetto VSIX standard. Per altre informazioni, vedere:  
  
-   [Creazione di un'estensione con un comando di Menu](../extensibility/creating-an-extension-with-a-menu-command.md)  
  
-   [Creazione di un'estensione con una finestra degli strumenti](../extensibility/creating-an-extension-with-a-tool-window.md)  
  
-   [Creazione di un'estensione con un modello di elemento di Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md)  
  
-   [Creazione di un'estensione con un VSPackage](../extensibility/creating-an-extension-with-a-vspackage.md)  
  
     La procedura guidata VSPackage non crea più estensioni in c# o Visual Basic.  
  
### <a name="c"></a>C++  
 Per C++, la procedura guidata VSPackage supporta i comandi di menu e finestre degli strumenti editor personalizzati. Cercare nel **nuovo progetto** finestra di dialogo in **Visual C++ / Extensibility**.  
  
## <a name="vs-sdk-reference-assemblies-via-nuget"></a>Assembly di riferimento SDK di Visual Studio tramite NuGet  
 Per garantire una maggiore portabilità e la condivisione dei progetti di estendibilità, è possibile utilizzare le versioni NuGet degli assembly di riferimento di Visual Studio SDK.  Questi sono disponibili in [nuget.org](http://www.nuget.org) pubblicato da [VisualStudioExtensibility](http://www.nuget.org/profiles/VisualStudioExtensibility) e possono essere facilmente aggiunti al progetto o soluzione tramite Visual Studio **fa riferimento / gestione pacchetti NuGet** finestra di dialogo. È possibile aggiungere singoli riferimenti agli assembly di estensibilità specifica o tutti il SDK di Visual Studio fa riferimento ad assembly contemporaneamente utilizzando il SDK di Visual Studio [pacchetto Meta](http://www.nuget.org/packages/VSSDK_Reference_Assemblies). Per ulteriori informazioni su NuGet, vedere [NuGet Panoramica](http://docs.nuget.org/) e [la gestione di pacchetti NuGet mediante la finestra di dialogo](http://docs.nuget.org/Consume/Package-Manager-Dialog).  
  
 Quando si utilizzano le versioni NuGet degli assembly di riferimento di Visual Studio SDK, un altro utente non è necessario installare il SDK di Visual Studio per aprire e compilare il progetto.  L'assembly di riferimento di NuGet e strumenti di compilazione di Visual Studio SDK verranno installati automaticamente nel proprio computer per il progetto.  
  
 I modelli di elementi di Visual Studio SDK usavano NuGet per i riferimenti e gli strumenti di compilazione in modo si ottengono i vantaggi di NuGet per impostazione predefinita.  
  
> [!NOTE]
>  È possibile continuare a utilizzare gli assembly di riferimento di Visual Studio SDK installato con i progetti (sotto \<percorso di installazione di Visual Studio > \ VSSDK\VisualStudioIntegration\Common\Assemblies) e i progetti di estendibilità esistenti non devono essere aggiornate per l'utilizzo di pacchetti NuGet.  Il progetto **fa riferimento / Aggiungi riferimento** finestra di dialogo continua a utilizzare gli assembly di riferimento di Visual Studio SDK installato.  
>   
>  Se si desidera modificare i progetti esistenti per utilizzare NuGet, vedere [procedura: eseguire la migrazione di VSPackage in Visual Studio 2015](../extensibility/how-to-migrate-extensibility-projects-to-visual-studio-2015.md) che ha una sezione sull'aggiornamento di progetti di estendibilità per i pacchetti NuGet.  
  
## <a name="light-bulbs"></a>Le lampadine  
 Uno dei modi più interessanti nuovo di scrittura del codice di estensione viene fornito dal progetto Roslyn. Per ulteriori informazioni, vedere [Roslyn](https://github.com/dotnet/Roslyn).  
  
 Le lampadine sono una nuova funzionalità che viene fornito con VSSDK. Si tratta di icone utilizzate nell'editor di Visual Studio che si espandono per visualizzare un set di azioni di refactoring del codice o correzioni per problemi identificati dagli analizzatori di codice incorporato. Per ulteriori informazioni, vedere [procedura dettagliata: visualizzazione di suggerimenti lampadina](../extensibility/walkthrough-displaying-light-bulb-suggestions.md).  
  
## <a name="updated-user-experience-guidelines"></a>Linee guida sull'esperienza utente aggiornato  
 Progettazione di funzionalità o nuove estensioni per Visual Studio? Controllare l'aggiornato ed espanso [linee guida esperienza utente di Visual Studio](../extensibility/ux-guidelines/visual-studio-user-experience-guidelines.md).  Si noterà il [colore token](../extensibility/ux-guidelines/shared-colors-for-visual-studio.md), [le dimensioni dei caratteri](../extensibility/ux-guidelines/fonts-and-formatting-for-visual-studio.md), [specifiche del layout della finestra di dialogo](../extensibility/ux-guidelines/layout-for-visual-studio.md)e altre indicazioni necessarie per la nuova interfaccia utente è totalmente integrato con Visual Studio.
