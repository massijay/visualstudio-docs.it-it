---
title: "Utilizzando i tipi di carattere e colori | Microsoft Docs"
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
  - "tipi di carattere, il controllo nell'IDE"
  - "IDE, controllare i tipi di carattere e colore del testo"
  - "Pagina delle proprietà di tipi di carattere e colori"
  - "controllo tipo di carattere e colore [Visual Studio SDK]"
  - "testo, IDE"
ms.assetid: d1a9b99f-fbdc-45ed-920a-e08c3d931ac9
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# Utilizzando i tipi di carattere e colori
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

[!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] fornisce il supporto per l'utilizzo dei tipi di carattere e colori al testo visualizzato.  
  
## In questa sezione  
 [Tipo di carattere e colore Panoramica](../extensibility/font-and-color-overview.md)  
 Vengono illustrate le impostazioni di carattere e colore del testo nell'ambiente di sviluppo integrato di \(IDE\) [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  Inoltre vengono presentati i concetti di categorie e degli elementi della visualizzazione e viene descritto come Vspackage ed editor principale utilizzano gli attributi di testo.  
  
 [Recupero di tipi di carattere e le informazioni di colore per testo colorazione](../extensibility/getting-font-and-color-information-for-text-colorization.md)  
 Vengono illustrate le linee guida per l'implementazione di colorazione del testo in package VS che gestiscono **categorie** diverso da **editor di testo**.  
  
 [L'accesso alle Stored carattere e le impostazioni dei colori](../extensibility/accessing-stored-font-and-color-settings.md)  
 Viene illustrato come le impostazioni correnti dei colori e tipi di carattere possono essere archiviate, recuperare e applicare.  
  
 [Implementazione di elementi visualizzati e categorie personalizzate](../extensibility/implementing-custom-categories-and-display-items.md)  
 Vengono descritti i passaggi di base da cui una finestra può creare e utilizzare il proprio di **Visualizzare elementi** e di **categorie** per supportare la visualizzazione di testo.  
  
 Questo approccio richiede un VSPackage di implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider> e le interfacce correlate.  
  
 [Procedura: accedere ai tipi di carattere incorporati e combinazione di colori](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)  
 Viene illustrato come definire e registrare una categoria utilizzando i tipi incorporate e i colori e avviano l'utilizzo di fornito dal sistema di tipi di carattere e colori.  
  
## Riferimenti  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
 SCC\_E\_UNKNOWNPROJECT  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
 Consente a un VSPackage per supportare la pagina dell'IDE **Tipi di carattere e colori** definendo i tipi di carattere predefinite e i colori per una finestra o un componente dell'interfaccia utente.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>  
 Fornisce un meccanismo che un package VS che fornisce il tipo di carattere e il supporto di colore possibile specificare un gruppo di elementi visualizzato \- una super\-categoria che rappresenta un'unione due o più delle categorie.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>  
 Consente a un VSPackage per recuperare il tipo di carattere e ai dati, o lo rende al Registro di sistema.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
 Notifica a package VS che utilizza il tipo di carattere e le informazioni sui colori sulle modifiche nel tipo di carattere e colori le impostazioni.  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorUtilities>  
 Fornisce gli strumenti per utilizzare l'input e i dati di output utilizzati con i metodi del meccanismo di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]**Il tipo di carattere e colori** .  
  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
 Controlla la memorizzazione nella cache delle impostazioni dei colori e del tipo di carattere.  
  
## Sezioni correlate  
 [Lo sviluppo di un servizio di linguaggio](../extensibility/internals/developing-a-legacy-language-service.md)  
 Viene illustrato come Vspackage possibile utilizzare i servizi di linguaggio per personalizzare l'editor di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .  
  
 [Colorazione in editor personalizzati della sintassi](../extensibility/syntax-coloring-in-custom-editors.md)  
 Descries quali l'editor di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizza i servizi di linguaggio per implementare la colorazione della sintassi.  
  
 [Estensione di altre parti di Visual Studio](../extensibility/extending-other-parts-of-visual-studio.md)  
 Viene illustrato come utilizzare i servizi di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] per creare elementi dell'interfaccia utente che corrispondono al resto di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].