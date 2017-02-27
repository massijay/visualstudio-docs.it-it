---
title: "L&#39;accesso alle Stored carattere e le impostazioni dei colori | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "tipi di carattere, l'accesso alle impostazioni archiviate"
  - "controllo tipo di carattere e colore [Visual Studio SDK], persistenza"
  - "colori, accesso alle impostazioni archiviate"
ms.assetid: beba7174-e787-45c2-b6ff-a60f67ad4998
caps.latest.revision: 26
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 26
---
# L&#39;accesso alle Stored carattere e le impostazioni dei colori
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) vengono archiviate le impostazioni modificate per i tipi di carattere e colori nel Registro di sistema. È possibile utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia per accedere a queste impostazioni.  
  
## <a name="to-initiate-state-persistence-of-fonts-and-colors"></a>Per avviare la persistenza dello stato dei tipi di carattere e colori  
 Informazioni di carattere e colori vengono archiviate in base alla categoria nel seguente percorso del Registro di sistema: [HKCU\SOFTWARE\Microsoft \Visual Studio\\*\< versione di Visual Studio>*\FontAndColors\\*\< CategoryGUID>*], dove *\< CategoryGUID>* è il GUID di categoria.  
  
 Di conseguenza, per avviare la persistenza, un VSPackage necessario:  
  
-   Ottenere un <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia chiamando `QueryService` nel provider di servizi globale.  
  
     `QueryService` deve essere chiamato utilizzando un argomento ID servizio di `SID_SVsFontAndColorStorage` e un argomento di ID di interfaccia di `IID_IVsFontAndColorStorage`.  
  
-   Utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> per aprire una categoria deve essere resa persistente utilizzando il GUID della categoria e un flag modalità come argomenti.  
  
     La modalità specificata dal `fFlags` argomento, viene costruito dai valori di <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> enumerazione. Questa modalità consente di controllare:  
  
    -   Le impostazioni che è possibile accedere tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia.  
  
    -   Tutte le impostazioni o solo quelle che gli utenti modificano e che sono recuperabili tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia.  
  
    -   Le modalità di propagazione delle modifiche alle impostazioni utente.  
  
    -   Il formato dei valori di colore che vengono utilizzati.  
  
## <a name="to-use-state-persistence-of-fonts-and-colors"></a>Utilizzare la persistenza dello stato dei tipi di carattere e colori  
 Colori e i tipi persistenti prevede:  
  
-   Sincronizzare le impostazioni IDE con impostazioni archiviate nel Registro di sistema.  
  
-   Propagazione delle informazioni sulla modifica del Registro di sistema.  
  
-   Impostazione e recupero delle impostazioni archiviate nel Registro di sistema.  
  
 La sincronizzazione dell'impostazione di archiviazione con le impostazioni IDE è trasparente. L'IDE sottostante scrive automaticamente le impostazioni aggiornate per **elementi visualizzati** alle voci del Registro di sistema di categorie.  
  
 Se più VSPackage condividono una determinata categoria, un VSPackage richiede che gli eventi vengono generati quando i metodi del <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia vengono utilizzati per modificare le impostazioni del Registro di sistema archiviati.  
  
 Per impostazione predefinita, non è abilitata la generazione di eventi. Per abilitare la generazione di eventi, una categoria deve essere aperto tramite <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>. In questo modo l'IDE chiamare appropriato <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents> metodo che implementa un VSPackage.  
  
> [!NOTE]
>  Le modifiche tramite il **carattere e colori** pagina delle proprietà di generare eventi indipendenti <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>. È possibile utilizzare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager> per determinare se è necessario un aggiornamento delle impostazioni di carattere e colori memorizzati nella cache prima di chiamare i metodi dell'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> (classe).  
  
### <a name="storing-and-retrieving-information"></a>L'archiviazione e recupero di informazioni  
 Per ottenere o configurare le informazioni che un utente può modificare per un elemento di visualizzazione denominata in una categoria aperto, chiamare VSPackage il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetItem%2A> metodi.  
  
 Informazioni sui tipi di carattere degli attributi per una determinata categoria verrà ottenuta tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.SetFont%2A> metodi.  
  
> [!NOTE]
>  Il `fFlags` argomento passato al <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.OpenCategory%2A> metodo all'apertura di tale categoria definisce il comportamento del <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> metodi. Per impostazione predefinita, questi itemsthat aboutdisplay di metodi restituiscono solo le informazioni sono state modificate. Tuttavia, se viene aperto con una categoria di <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS> flag sia aggiornato ed sono accessibile elementi visualizzati invariato da <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A>.  
  
 Per impostazione predefinita, solo modificato **elementi visualizzati** informazioni vengono mantenute nel Registro di sistema. Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> interfaccia non può essere utilizzato per recuperare tutte le impostazioni per i tipi di carattere e colori.  
  
> [!NOTE]
>  Il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> e <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetFont%2A> restituiscono REGDB_E_KEYMISSING, (0x80040152L) quando vengono utilizzati per recuperare informazioni su unchanged **elementi visualizzati**.  
  
 Le impostazioni di tutti **elementi visualizzati** in un particolare **categoria** può essere ottenuto utilizzando i metodi del `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults` interfaccia.  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.__FCSTORAGEFLAGS>   
 [Implementazione di elementi visualizzati e categorie personalizzate](../extensibility/implementing-custom-categories-and-display-items.md)