---
title: "Tipo di carattere e colore Panoramica | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], tipo di carattere e colore"
  - "controllo tipo di carattere e colore [Visual Studio SDK], Editor"
ms.assetid: 2203e4e7-8b7f-44ec-8884-6ff718d4f278
caps.latest.revision: 22
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 22
---
# Tipo di carattere e colore Panoramica
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In questo argomento vengono illustrate le impostazioni di carattere e colore del testo nell'ambiente di sviluppo integrato di \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Inoltre vengono presentati i concetti di categorie e degli elementi della visualizzazione e viene descritto come Vspackage ed editor principale utilizzano gli attributi di testo.  
  
## I tipi di carattere e la pagina delle proprietà di colori  
 È possibile gestire gli attributi di testo visualizzato nell'ambiente di sviluppo integrato di \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dalla pagina delle proprietà di **Tipi di carattere e colori** .  Per trovare la pagina delle proprietà di **Tipi di carattere e colori** , scegliere dal menu di **strumenti** , fare clic su **opzioni**.  Espandere **Ambiente** e fare clic su **Tipi di carattere e colori**.  
  
## Categorie ed elementi della visualizzazione  
 I tipi di carattere e i colori sono organizzati in **categorie** e in **Visualizzare elementi**.  
  
-   **categoria** è un contenitore logico o funzionale per una serie di **Visualizzare elementi**.  
  
     Un elenco di **categorie** verrà visualizzato nella casella a discesa di **Impostazioni di visualizzazione per** della pagina delle proprietà di **Tipi di carattere e colori** .  
  
-   **elemento visualizzato** è un'entità ben definito di testo come un commento, una stringa, o una struttura di controllo che deve essere colorata se visualizzato.  
  
 Ogni **elemento visualizzato** è in modo univoco definito all'interno di **categoria** che lo contiene.  Pertanto, più di un **categoria** può avere **elemento visualizzato** con lo stesso nome.  
  
## Controllo di un VSPackage tipi di carattere e colori  
 [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] consente Vspackage a:  
  
-   Definire il tipo di carattere e colori **categorie**.  
  
-   Specificare i tipi di carattere e i colori utilizzati per presentare **Visualizzare elementi**.  
  
-   Interagire con la pagina delle proprietà di **Tipi di carattere e colori** .  
  
-   **categorie** più di aggregazione in gruppi.  
  
-   Mantenere le modifiche alle impostazioni predefinite.  
  
 Esistono due modi per interagire con il tipo di carattere e le selezioni dei colori all'interno di [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)].  
  
-   Un modo viene definito *colorazione della sintassi*.  Viene utilizzato da un package VS che consente di personalizzare l'editor esistente di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per implementare un servizio di linguaggio e creare un editor standard.  
  
     Solo un **categoria** supporta questo meccanismo, cioé, **editor di testo**.  
  
-   Un'alternativa più generale supporta tutti gli altri **categorie** e componenti dell'interfaccia utente diverso dall'editor standard per la visualizzazione del testo.  Per ulteriori informazioni, vedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>.  
  
## Impostazioni del testo dell'editor  
 Le impostazioni dei colori e tipi di carattere dell'editor principale di un oggetto del servizio di linguaggio dipendono da **editor di testocategoria** di ricerca nella casella a discesa di **Impostazioni di visualizzazione per** della pagina delle proprietà di **Tipi di carattere e colori** .  
  
 Quando si utilizzano gli editor, è necessario utilizzare il meccanismo speciale di controllo del colore di carattere e che il servizio di linguaggio fornisce per controllare e estendere le impostazioni di **editor di testo** .  Il meccanismo è noto come *colorazione della sintassi* e fornisce:  
  
-   Una tecnica semplificata per gestire i tipi di carattere e i colori degli elementi visualizzati.  
  
     Per ulteriori informazioni, vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsProvideColorableItems> e <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorableItem>.  
  
-   Un meccanismo definito e ottimizzato di colorazione.  
  
     Per ulteriori informazioni, vedere <xref:Microsoft.VisualStudio.TextManager.Interop.IVsColorizer>.  
  
-   La possibilità a entrambi gli elementi della visualizzazione di incorporato di utilizzo da **editor di testocategoria** e estenderle.  
  
     Per ulteriori informazioni, vedere [Procedura: utilizzare gli elementi di colori predefiniti](../extensibility/internals/how-to-use-built-in-colorable-items.md) e [Elementi di colori personalizzati](../extensibility/internals/custom-colorable-items.md).  
  
-   Persistenza automatica dello stato corrente degli elementi in visualizzazione personalizzate che incorporate di con la categoria di **editor di testo** .  
  
 Per ulteriori informazioni sulla colorazione della sintassi vedere [In un servizio di linguaggio Legacy colorazione della sintassi](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md).  
  
## Vedere anche  
 [Interfacce legacy nell'Editor](../extensibility/legacy-interfaces-in-the-editor.md)   
 [In un servizio di linguaggio Legacy colorazione della sintassi](../extensibility/internals/syntax-coloring-in-a-legacy-language-service.md)