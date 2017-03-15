---
title: "Utilizzando gli indicatori di testo con l&#39;API Legacy | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "editor [Visual Studio SDK], legacy - degli indicatori di testo"
ms.assetid: 937a0b19-1216-45d5-a7ad-4fe1d6f73097
caps.latest.revision: 16
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 16
---
# Utilizzando gli indicatori di testo con l&#39;API Legacy
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Un marcatore di testo è un intervallo mobile di testo in un buffer che può influire sulla visualizzazione e il comportamento di un'area di testo.  I marcatori includono i punti di interruzione, i segnalibri, le linee ondulate e aree di sola lettura.  I marcatori di testo sono fondamentalmente diversi da colorazione della sintassi.  La colorazione della sintassi è un modo rapido comunicare la sintassi del linguaggio associata a un'area di testo.  La colorazione della sintassi è richiesta in genere quando le finestre aggiorna lo schermo, quando la velocità è importante.  La colorazione della sintassi modifica solo il colore del testo.  I marcatori di testo possono modificare molte altre proprietà di testo.  I marcatori di testo possono “float„ e implementano il comportamento e la colorazione speciali.  
  
 A causa del sovraccarico delle prestazioni associato ai marcatori di testo, non creare molti marcatori per i buffer di testo.  Ogni marcatore viene aggiornato ogni volta che un utente modifica il contenuto del buffer.  
  
> [!NOTE]
>  Gli utenti possono modificare il colore di un tipo visibile del marcatore ma la non relativi forma e stile.  Per ulteriori informazioni, vedere [Tipi di carattere e colori, Ambiente, finestra di dialogo Opzioni](../ide/reference/fonts-and-colors-environment-options-dialog-box.md).  
  
## Argomenti correlati  
  
|Titolo|Descrizione|  
|------------|-----------------|  
|[Procedura: aggiungere testo Standard marcatori](../extensibility/how-to-add-standard-text-markers.md)|Viene descritto come aggiungere un tipo standard del marcatore di testo fornito dall'editor di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] a una visualizzazione di testo.|  
|[Procedura: implementare i marcatori di errore](../extensibility/how-to-implement-error-markers.md)|Viene descritto come implementare un'istanza del marcatore di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] utilizzato per indicare gli errori utilizzando le linee ondulate.|  
|[Procedura: creare indicatori di testo personalizzato](../extensibility/how-to-create-custom-text-markers.md)|Viene descritto come creare e aggiungere un tipo personalizzato del marcatore di testo a una visualizzazione di testo.|  
|[Procedura: utilizzare gli indicatori di testo](../extensibility/how-to-use-text-markers.md)|Viene illustrato come aggiungere marcatori di testo.|  
|[Nell'Editor di componenti di base](../extensibility/inside-the-core-editor.md)|Vengono descritte le funzionalità dell'editor principale e vengono fornite informazioni dettagliate su come personalizzare l'editor principale.|  
|[Editor Features](http://msdn.microsoft.com/it-it/bdac940d-1f14-4019-a01f-fd0bb3dc7198)|Vengono descritte le funzionalità disponibili nell'editor di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] .|  
  
## Riferimento  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType>  
 Fornisce un meccanismo uniforme per ottenere informazioni su un tipo specifico del marcatore di testo, se predefinito dall'editor o registrato da un VSPackage.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextLineMarker>  
 Fornisce l'accesso a e modificare la posizione di un marcatore di testo in un buffer di testo utilizzando le coordinate bidimensionali.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarker>  
 Fornisce metodi per gestire i marcatori di testo.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient>  
 Fornisce i callback dell'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] e altri processi utilizzati per modificare un marcatore di testo.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientAdvanced>  
 Estende la funzionalità disponibile tramite l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> fornendo i callback aggiuntivi.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClientEx>  
 Estende la funzionalità disponibile tramite l'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerClient> fornendo i callback aggiuntivi.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerColorSet>  
 Consente a un tipo di marcatori per determinare se altri tipi del marcatore condividono lo stesso set di colori.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerContextProvider>  
 Fornisce il contesto dei marcatori di testo nell'editor principale.  Per le condizioni di errore, il metodo <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget.QueryStatus%2A> deve gestire i seguenti casi di errore:  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerGlyphDropHandler>  
 Un gestore fornito per i marcatori dei glifi supportano la funzione di trascinamento.  Un glifo viene visualizzata un'icona che indica la posizione di un marcatore.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextMarkerTypeProvider>  
 Restituisce un'interfaccia di <xref:Microsoft.VisualStudio.TextManager.Interop.IVsPackageDefinedTextMarkerType> da un servizio che fornisce i marcatori di testo all'altro package VS.  
  
 <xref:Microsoft.VisualStudio.TextManager.Interop.IVsTextStreamMarker>  
 Fornisce l'accesso a e modificare la posizione di un marcatore di testo in un buffer di testo utilizzando le coordinate unidimensionali.  Se possibile, non utilizzare questa interfaccia.