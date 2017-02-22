---
title: "Elementi di colori personalizzati | Microsoft Docs"
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
  - "colori"
  - "servizi di linguaggio, gli elementi di colori personalizzati"
ms.assetid: b4d0ddee-c04b-48dc-ba82-f6068570cef0
caps.latest.revision: 24
caps.handback.revision: 24
ms.author: "gregvanl"
manager: "ghogen"
---
# Elementi di colori personalizzati
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

È possibile sostituire l'elenco dei tipi per colorare, ad esempio le parole chiave e commenti, mediante l'implementazione di elementi di colori personalizzati come parte del servizio di linguaggio.  
  
## Impostazioni utente di colori  
 È possibile visualizzare il **tipi di carattere e colori** la finestra di dialogo selezionando **Opzioni** sul **strumenti** menu e quindi selezionando **tipi di carattere e colori** in **ambiente**. Quando si seleziona una visualizzazione, ad esempio **Editor di testo** o **finestra di comando**,  **visualizzare gli elementi** casella di riepilogo vengono visualizzati tutti gli elementi colorabile predefiniti per tale visualizzazione. È possibile visualizzare e modificare il tipo di carattere, dimensioni, colore di primo piano e colore di sfondo per ogni elemento colorabile. Le scelte sono archiviate in una cache nel Registro di sistema e accessibili dal nome dell'elemento colorabile.  
  
## Presentazione dei colori  
 Poiché l'IDE gestisce l'override dell'utente del elementi colorabili il **tipi di carattere e colori** la finestra di dialogo, è necessario fornire solo con un nome di ogni elemento colorabile. Questo nome viene visualizzato un messaggio nel **visualizzare gli elementi** elenco. Gli elementi di colori vengono visualizzati in ordine alfabetico. Per raggruppare gli elementi di colori personalizzata del servizio di linguaggio, è possibile iniziare ogni nome con il nome della lingua, ad esempio **NewLanguage \- commento** e **NewLanguage \- parola chiave**.  
  
> [!CAUTION]
>  È necessario includere il nome della lingua nel nome dell'elemento colorabile per evitare conflitti con i nomi di elemento colorabile esistenti. Se si modifica il nome di uno degli elementi di colorabile durante lo sviluppo, è necessario azzerare la cache, che è stata creata la prima volta che gli elementi colorabili ha avuto accesso. È possibile reimpostare la cache sperimentale con lo strumento CreateExpInstance, che viene installato con Visual Studio SDK, in genere nella directory  
>   
>  **C:\\Programmi\\Microsoft file \(x86\) \\Microsoft Visual Studio 14.0\\VSSDK\\VisualStudioIntegration\\Tools\\Bin**  
>   
>  Per azzerare la cache, chiamare `CreateExpInstance /Reset`. Per ulteriori informazioni su CreateExpInstance, vedere [Utilità CreateExpInstance](../../extensibility/internals/createexpinstance-utility.md).  
  
 Il primo elemento nell'elenco di colori non viene mai fatto riferimento. Il primo elemento corrisponde a un indice di elemento colorabile predefinito pari a 0, e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] fornisce sempre i colori predefiniti del testo e gli attributi per tale elemento. Il modo più semplice risolvere i problemi con questo elemento privo di riferimento è di fornire un elemento colorabile segnaposto come primo elemento dell'elenco.  
  
## Implementazione di elementi di colori personalizzati  
  
1.  Definire cosa deve essere colorata nella propria lingua, ad esempio \(parola chiave\), operatore e identificatore.  
  
2.  Creare un'enumerazione di questi elementi colorabile.  
  
3.  Associare i tipi di token restituiti da un parser o uno scanner con i valori enumerati.  
  
     I valori che rappresentano i tipi di token, ad esempio, potrebbero essere gli stessi valori dell'enumerazione di elementi di colori personalizzati.  
  
4.  Nell'implementazione del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer.ColorizeLine%2A> metodo il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer> dell'oggetto, compilare l'elenco di attributi con i valori dell'enumerazione di elementi personalizzati colorabile corrispondenti ai tipi di token restituiti dal parser o scanner.  
  
5.  Nella stessa classe che implementa il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsLanguageInfo> interfaccia, implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> interfaccia e i due metodi, <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A>.  
  
6.  Implementare l'interfaccia <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
7.  Se si desidera supportare i valori di colore a 24 bit o elevato, implementare anche il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfaccia.  
  
8.  Nell'oggetto servizio del linguaggio, creare un elenco che contiene il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> oggetti, uno per ogni elemento colorabile in grado di identificare la parser o lo scanner.  
  
     È possibile accedere a ogni elemento nell'elenco utilizzando il valore corrispondente dell'enumerazione di elementi colori personalizzati. Utilizzare i valori di enumerazione come indice nell'elenco. Il primo elemento nell'elenco non avviene mai, poiché per il testo predefinito corrisponde allo stile [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] sempre gestisce se stesso. È possibile rimediare a questa inserendo un elemento colorabile segnaposto all'inizio dell'elenco.  
  
9. Nell'implementazione del metodo di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetItemCount%2A> metodo, restituire il numero di elementi nell'elenco di elementi di colori personalizzati.  
  
10. Nell'implementazione del <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems.GetColorableItem%2A> \(metodo\), restituiscono l'elemento colorabile richiesto dall'elenco.  
  
 Per un esempio di come implementare il <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem> interfacce, vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsHiColorItem>.  
  
## Vedere anche  
 [Modello di un servizio di linguaggio Legacy](../../extensibility/internals/model-of-a-legacy-language-service.md)   
 [Colorazione in editor personalizzati della sintassi](../../extensibility/syntax-coloring-in-custom-editors.md)   
 [In un servizio di linguaggio Legacy colorazione della sintassi](../../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)   
 [Implementazione di colorazione della sintassi](../../extensibility/internals/implementing-syntax-coloring.md)   
 [Procedura: utilizzare gli elementi di colori predefiniti](../../extensibility/internals/how-to-use-built-in-colorable-items.md)