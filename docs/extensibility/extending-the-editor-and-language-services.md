---
title: Estensione dell&quot;Editor e servizi linguistici | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- editors [Visual Studio SDK], new -
ms.assetid: 8d04f8db-eda7-4b3e-b6eb-c06df104502a
caps.latest.revision: 22
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
ms.openlocfilehash: 4d04f4588b1005e9b5ccb42c6042d01aacb45710
ms.lasthandoff: 02/22/2017

---
# <a name="extending-the-editor-and-language-services"></a>Estensione dell'Editor e servizi di linguaggio
È possibile aggiungere funzionalità del linguaggio (ad esempio IntelliSense) per il proprio editor ed estendere la maggior parte delle funzionalità dell'editor di codice di Visual Studio.  Per un elenco completo di ciò che è possibile estendere, vedere [servizio di linguaggio e punti di estensione di Editor](../extensibility/language-service-and-editor-extension-points.md).  
  
 Estendere la maggior parte delle funzionalità dell'editor mediante Managed Extensibility Framework (MEF). Ad esempio, se si desidera estendere la funzionalità di editor la colorazione della sintassi, è possibile scrivere un MEF *componente* che definisce le classificazioni per cui si desidera colorazione diversi e la modalità desiderata come gestiti. L'editor supporta inoltre più estensioni della stessa funzionalità.  
  
 Il livello di presentazione dell'editor è basato su Windows Presentation Framework (WPF). WPF fornisce una libreria di grafica per la formattazione del testo flessibile e fornisce inoltre visualizzazioni quali grafici e animazioni.  
  
 Visual Studio SDK fornisce adapter noto come *shim* per supportare i package VS che sono stati scritti per le versioni precedenti. Tuttavia, se si dispone di un VSPackage esistente, è consigliabile aggiornarlo per la nuova tecnologia per ottenere migliorate prestazioni e affidabilità.  
  
## <a name="related-topics"></a>Argomenti correlati  
  
|Titolo|Descrizione|  
|-----------|-----------------|  
|[Introduzione al servizio di linguaggio e le estensioni di Editor](../extensibility/getting-started-with-language-service-and-editor-extensions.md)|Viene illustrato come creare un'estensione per l'editor.|  
|[All'interno dell'Editor](../extensibility/inside-the-editor.md)|Descrive la struttura generale dell'editor e vengono elencate alcune delle relative funzionalità.|  
|[Managed Extensibility Framework nell'Editor](../extensibility/managed-extensibility-framework-in-the-editor.md)|Viene illustrato come utilizzare Managed Extensibility Framework (MEF) con l'editor.|  
|[Servizio di linguaggio e punti di estensione di Editor](../extensibility/language-service-and-editor-extension-points.md)|Elenca i punti di estensione dell'editor. Punti di estensione rappresentano le funzionalità dell'editor che possono essere esteso.|  
|[Procedura dettagliata: Creazione di un'area di controllo di visualizzazione, comandi e impostazioni (guide colonne)](../extensibility/walkthrough-creating-a-view-adornment-commands-and-settings-column-guides.md)|Vengono esaminati e viene illustrata la creazione di un area di controllo di visualizzazione che disegna linee gudie colonna che consentono di mantenere il codice per una determinata larghezza di visualizzazione.  Mostra inoltre la lettura e scrittura delle impostazioni, nonché dichiarazione e implementazione di comandi che è possibile richiamare la finestra di comando.|  
|[Editor di importazioni](../extensibility/editor-imports.md)|Elenca i servizi che è possibile importare un'estensione.|  
|[Adattamento del codice Legacy nell'editor](../extensibility/adapting-legacy-code-to-the-editor.md)|Vengono illustrati diversi modi per adattare il codice legacy (precedenti a Visual Studio 2010) per estendere l'editor.|  
|[La migrazione di un servizio di linguaggio Legacy](../extensibility/internals/migrating-a-legacy-language-service.md)|Viene illustrato come eseguire la migrazione di un servizio di linguaggio basato su VSPackage.|  
|[Procedura dettagliata: Collegamento di un tipo di contenuto a un'estensione nome File](../extensibility/walkthrough-linking-a-content-type-to-a-file-name-extension.md)|Viene illustrato come collegare un tipo di contenuto per un'estensione nome file.|  
|[Procedura dettagliata: Creazione di un glifo del margine](../extensibility/walkthrough-creating-a-margin-glyph.md)|Viene illustrato come aggiungere un'icona a un margine.|  
|[Procedura dettagliata: Evidenziazione del testo](../extensibility/walkthrough-highlighting-text.md)|Viene illustrato come utilizzare *tag* per evidenziare il testo.|  
|[Procedura dettagliata: struttura](../extensibility/walkthrough-outlining.md)|Viene illustrato come aggiungere la struttura per tipi specifici di parentesi graffe.|  
|[Procedura dettagliata: Visualizzazione di parentesi graffe corrispondenti](../extensibility/walkthrough-displaying-matching-braces.md)|Viene illustrato come evidenziare parentesi graffe corrispondenti.|  
|[Procedura dettagliata: Visualizzazione delle descrizioni comandi informazioni rapide](../extensibility/walkthrough-displaying-quickinfo-tooltips.md)|Viene illustrato come visualizzare i popup informazioni rapide che descrivono gli elementi di codice, ad esempio proprietà, metodi ed eventi.|  
|[Procedura dettagliata: Visualizzazione della Guida di firma](../extensibility/walkthrough-displaying-signature-help.md)|Viene illustrato come visualizzare i popup che forniscono informazioni sul numero e i tipi di parametri in una firma.|  
|[Walkthrough: Displaying Statement Completion](../extensibility/walkthrough-displaying-statement-completion.md) (Procedura dettagliata: Visualizzazione del completamento istruzioni)|Viene illustrato come implementare il completamento delle istruzioni.|  
|[Procedura dettagliata: Implementazione di frammenti di codice](../extensibility/walkthrough-implementing-code-snippets.md)|Viene illustrato come implementare l'espansione di frammento di codice.|  
|[Procedura dettagliata: Visualizzazione di suggerimenti di lampadina](../extensibility/walkthrough-displaying-light-bulb-suggestions.md)|Viene illustrato come visualizzare le lampadine per i suggerimenti di codice.|  
|[Procedura dettagliata: Utilizzo di un comando della Shell con un'estensione di Editor](../extensibility/walkthrough-using-a-shell-command-with-an-editor-extension.md)|Viene illustrato come associare un comando di menu in un VSPackage a un componente MEF.|  
|[Procedura dettagliata: Utilizzo di un tasto di scelta rapida con un'estensione di Editor](../extensibility/walkthrough-using-a-shortcut-key-with-an-editor-extension.md)|Viene illustrato come associare un collegamento del menu in un VSPackage a un componente MEF.|  
|[Managed Extensibility Framework (MEF)](http://msdn.microsoft.com/Library/6c61b4ec-c6df-4651-80f1-4854f8b14dde)|Vengono fornite informazioni su Managed Extensibility Framework (MEF).|  
|[Windows Presentation Foundation](http://msdn.microsoft.com/Library/f667bd15-2134-41e9-b4af-5ced6fafab5d)|Vengono fornite informazioni su Windows Presentation Foundation (WPF).|  
  
## <a name="reference"></a>Riferimento  
 L'editor di Visual Studio include spazi dei nomi seguenti.  
  
 <xref:Microsoft.VisualStudio.Language.Intellisense></xref:Microsoft.VisualStudio.Language.Intellisense>  
  
 <xref:Microsoft.VisualStudio.Language.StandardClassification></xref:Microsoft.VisualStudio.Language.StandardClassification>  
  
 <xref:Microsoft.VisualStudio.Editor></xref:Microsoft.VisualStudio.Editor>  
  
 <xref:Microsoft.VisualStudio.Text></xref:Microsoft.VisualStudio.Text>  
  
 <xref:Microsoft.VisualStudio.Text.Adornments></xref:Microsoft.VisualStudio.Text.Adornments>  
  
 <xref:Microsoft.VisualStudio.Text.Classification></xref:Microsoft.VisualStudio.Text.Classification>  
  
 <xref:Microsoft.VisualStudio.Text.Differencing></xref:Microsoft.VisualStudio.Text.Differencing>  
  
 <xref:Microsoft.VisualStudio.Text.Document></xref:Microsoft.VisualStudio.Text.Document>  
  
 <xref:Microsoft.VisualStudio.Text.Editor></xref:Microsoft.VisualStudio.Text.Editor>  
  
 <xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods></xref:Microsoft.VisualStudio.Text.Editor.OptionsExtensionMethods>  
  
 <xref:Microsoft.VisualStudio.Text.Formatting></xref:Microsoft.VisualStudio.Text.Formatting>  
  
 <xref:Microsoft.VisualStudio.Text.IncrementalSearch></xref:Microsoft.VisualStudio.Text.IncrementalSearch>  
  
 <xref:Microsoft.VisualStudio.Text.Operations></xref:Microsoft.VisualStudio.Text.Operations>  
  
 <xref:Microsoft.VisualStudio.Text.Outlining></xref:Microsoft.VisualStudio.Text.Outlining>  
  
 <xref:Microsoft.VisualStudio.Text.Projection></xref:Microsoft.VisualStudio.Text.Projection>  
  
 <xref:Microsoft.VisualStudio.Text.Tagging></xref:Microsoft.VisualStudio.Text.Tagging>  
  
 <xref:Microsoft.VisualStudio.Utilities></xref:Microsoft.VisualStudio.Utilities>
