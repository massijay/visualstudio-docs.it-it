---
title: Introduzione al servizio di linguaggio e le estensioni di Editor | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new - extensions
ms.assetid: 6b151891-c06d-40b1-9867-42298caa8492
caps.latest.revision: 21
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
ms.sourcegitcommit: 5658ecf52637a38bc3c2a5ad9e85b2edebf7d445
ms.openlocfilehash: 3cc009e23d123f50b108533e135bd51e123b3809
ms.lasthandoff: 02/22/2017

---
# <a name="getting-started-with-language-service-and-editor-extensions"></a>Introduzione al servizio di linguaggio e le estensioni di Editor
È possibile utilizzare estensioni dell'editor per aggiungere funzionalità del linguaggio, ad esempio la struttura, corrispondenza parentesi graffe, IntelliSense e lampadine proprio linguaggio di programmazione o a qualsiasi tipo di contenuto. È inoltre possibile personalizzare l'aspetto e il comportamento dell'editor di Visual Studio, ad esempio testo colorazione, margini, grafici e altri elementi visivi. È inoltre possibile definire il tipo di contenuto e specificare l'aspetto e il comportamento delle viste di testo in cui viene visualizzato il contenuto.  
  
 Per iniziare a scrivere estensioni dell'editor, utilizzare i modelli di progetto di editor che vengono installati come parte di Visual Studio SDK. Visual Studio SDK è un insieme scaricabile di strumenti che semplificano lo sviluppo di estensioni di Visual Studio o utilizzando i package VS mediante Managed Extensibility Framework (MEF).  
  
> [!NOTE]
>  Per ulteriori informazioni sul SDK di Visual Studio, vedere [Visual Studio SDK](../extensibility/visual-studio-sdk.md).  
  
 È consigliabile conoscere i seguenti concetti e le tecnologie prima di scrivere le proprie estensioni dell'editor.  
  
## <a name="the-windows-presentation-foundation-wpf-and-editor-extensions"></a>Windows Presentation Foundation (WPF) e le estensioni di Editor  
 L'interfaccia utente dell'editor di Visual Studio (UI) viene implementato utilizzando Windows Presentation Foundation (WPF). WPF fornisce un'esperienza avanzata visual e un modello di programmazione coerente che separa gli aspetti visivi del codice dalla logica di business. Quando si creano estensioni di editor, è possibile utilizzare molti elementi WPF e funzionalità. Per ulteriori informazioni, vedere [Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d).  
  
## <a name="the-managed-extensibility-framework-mef-and-editor-extensions"></a>Managed Extensibility Framework (MEF) e le estensioni di Editor  
 Editor di Visual Studio utilizza Managed Extensibility Framework (MEF) per gestire i suoi componenti e le estensioni. La libreria MEF consente anche agli sviluppatori più facilmente creare estensioni per un'applicazione host come Visual Studio. In questo framework, si definisce un'estensione in base a un contratto MEF ed esportarlo come componente MEF. L'applicazione host gestisce le parti di componente ricerca, effettuarne la registrazione e assicurandosi che vengano applicate a contesto corretto.  
  
> [!NOTE]
>  Per ulteriori informazioni su MEF nell'editor, vedere [Managed Extensibility Framework nell'Editor](../extensibility/managed-extensibility-framework-in-the-editor.md).  
  
## <a name="visual-studio-editor-extension-points-and-extensions"></a>Estensioni e i punti di estensione di Editor di Visual Studio  
 Punti di estensione editor sono componenti MEF che è possibile personalizzare ed estendere. In alcuni casi per estendere il punto di estensione, che implementa un'interfaccia e l'esportazione con metadati corretto. In altri casi sufficiente dichiarare un'estensione ed esportarlo come un tipo particolare.  
  
 Di seguito sono riportati alcuni dei tipi di base di estensioni dell'editor:  
  
-   Margini e le barre di scorrimento  
  
-   Tag  
  
-   Aree di controllo  
  
-   Opzioni  
  
-   IntelliSense  
  
 Per ulteriori informazioni sui punti di estensione di editor, vedere [servizio di linguaggio e punti di estensione di Editor](../extensibility/language-service-and-editor-extension-points.md).  
  
## <a name="deploying-editor-extensions"></a>Distribuzione di estensioni dell'Editor  
 In Visual Studio, si distribuisce estensioni editor aggiungendo un file di metadati denominato source.extension.vsixmanifest alla soluzione, compilare la soluzione, e quindi aggiungendo una copia dei file binari e il manifesto in una cartella che è noto a Visual Studio. Il file manifesto definisce le informazioni di base relativi all'estensione (ad esempio nome, autore, versione e tipo di contenuto). Per ulteriori informazioni su come distribuire le estensioni e il file di manifesto VSIX, vedere [Shipping estensioni di Visual Studio](../extensibility/shipping-visual-studio-extensions.md).  
  
 Quando si installa un'estensione in un computer, includere i file binari e il manifesto in una sottocartella della cartella in cui è noto a Visual Studio.  
  
> [!WARNING]
>  Non è necessario occuparsi dei manifesti e percorsi di distribuzione se si utilizza uno dei modelli di estendibilità di editor che sono inclusi in Visual Studio. I modelli contengono tutto il necessario per registrare e distribuire un'estensione.  
  
## <a name="running-extensions-in-the-experimental-instance"></a>Estensioni in esecuzione nell'istanza sperimentale  
 È possibile isolare la versione di lavoro di Visual Studio durante lo sviluppo di un'estensione mediante la distribuzione nella cartella seguente sperimentale (in Windows Vista e Windows 7):  
  
 *% LOCALAPPDATA %*\VisualStudio\10.0Exp\Extensions\\*aziendale*\\*ExtensionID*  
  
 dove *% LOCALAPPDATA %* è il nome dell'utente connesso, *aziendale* è il nome della società che possiede l'estensione e *ExtensionID* è l'ID dell'estensione.  
  
 Quando si distribuisce un'estensione per il percorso sperimentale, viene eseguito in modalità debug. Una seconda istanza di Visual Studio viene avviata ed è denominata **Microsoft Visual Studio - istanza sperimentale**.  
  
## <a name="managing-extensions"></a>Gestione delle estensioni  
 Sono elencate le estensioni di Visual Studio in **estensioni e aggiornamenti** (nel **strumenti** menu). Se si sta testando un'estensione nell'istanza sperimentale, è elencato nel **estensioni e aggiornamenti** nell'istanza sperimentale, ma non è elencato nell'istanza di sviluppo.  
  
 Per ulteriori informazioni, vedere [ricerca e utilizzo delle estensioni di Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).  
  
## <a name="using-templates-to-create-editor-extensions"></a>Utilizzo di modelli per creare estensioni dell'Editor  
 È possibile utilizzare editor modelli per creare estensioni MEF che personalizzano classificatori, grafici e i margini. Sono disponibili modelli per progetti c# e Visual Basic. Per ulteriori informazioni, vedere [creazione di un'estensione con un modello di elemento Editor](../extensibility/creating-an-extension-with-an-editor-item-template.md).  
  
 È inoltre possibile utilizzare il modello di progetto VSIX per creare estensioni. Questo modello fornisce solo gli elementi necessari per distribuire qualsiasi tipo di estensione e includere un file di progetto che include le attività di compilazione che consentono di distribuire l'estensione del file source.extension.vsixmanifest e i riferimenti all'assembly necessari. Per ulteriori informazioni, vedere [modello di progetto VSIX](../extensibility/vsix-project-template.md).  
  
 È inoltre possibile creare editor di componenti MEF da un'estensione di pacchetto di Visual Studio. Le procedure dettagliate seguenti per informazioni dettagliate, vedere:  
  
-   [Procedura dettagliata: Utilizzo di un comando della Shell con un'estensione di Editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)  
  
-   [Procedura dettagliata: Utilizzo di un tasto di scelta rapida con un'estensione di Editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)  
  
## <a name="see-also"></a>Vedere anche  
 [Servizio di linguaggio e punti di estensione di Editor](../extensibility/language-service-and-editor-extension-points.md)
