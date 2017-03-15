---
title: Implementazione di elementi visualizzati e categorie personalizzate | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- font and color control [Visual Studio SDK], categories
- custom categories
ms.assetid: 99311a93-d642-4344-bbf9-ff6e7fa5bf7f
caps.latest.revision: 25
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
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: d117676515988f1bf7f73ed1e9786c7c2919135e
ms.lasthandoff: 02/22/2017

---
# <a name="implementing-custom-categories-and-display-items"></a>Implementazione di elementi visualizzati e categorie personalizzate
Può fornire un VSPackage controllo dei tipi di carattere e colori del testo per il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato (IDE) tramite le categorie personalizzate e gli elementi di visualizzazione.  
  
 Categorie personalizzate e gli elementi si trovano il **tipi di carattere e colori** pagina delle proprietà. Per aprire il **tipi di carattere e colori** nella pagina proprietà di **strumenti** menu, fare clic su **opzioni**. Espandere **ambiente** e quindi fare clic su **tipi di carattere e colori**.  
  
 Quando si utilizza questo meccanismo, è necessario implementare i package VS il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>interfaccia e le interfacce associate.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>  
  
 In generale, questo meccanismo può essere utilizzato per modificare tutte le **visualizzare gli elementi** e **categorie** che li contengono. Tuttavia, non deve essere utilizzato per modificare il **testo EditorCategory** o il relativo **visualizzare gli elementi**. Per ulteriori informazioni, vedere [tipo di carattere e colore Panoramica](../extensibility/font-and-color-overview.md).  
  
 Per implementare personalizzato **categorie** o **visualizzare gli elementi**, è necessario un VSPackage:  
  
-   Creare o identificare categorie nel Registro di sistema.  
  
     Implementazione dell'IDE del **tipi di carattere e colori** pagina delle proprietà utilizza queste informazioni per eseguire correttamente le query per il servizio supporta una determinata categoria.  
  
-   Creare o identificare gruppi (facoltativi) nel Registro di sistema.  
  
     Può essere utile definire un gruppo, che rappresenta l'unione di due o più categorie. Se viene definito un gruppo, l'IDE automaticamente unisce le sottocategorie e distribuisce gli elementi all'interno del gruppo.  
  
-   Implementare il supporto IDE.  
  
-   Gestire le modifiche di carattere e colori.  
  
 Per informazioni, vedere [l'accesso a carattere archiviati e le impostazioni dei colori](../extensibility/accessing-stored-font-and-color-settings.md).  
  
## <a name="to-create-or-identify-categories"></a>Per creare o identificare le categorie  
  
-   Creare un tipo speciale di voce del Registro di sistema categoria [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<versione di Visual Studio >*\FontAndColors\\`<Category>`]  
  
     *\<Categoria >* è il nome non localizzato della categoria.  
  
-   Popolare il Registro di sistema con due valori:  
  
    |Name|Tipo|Dati|Descrizione|  
    |----------|----------|----------|-----------------|  
    |Categoria|REG_SZ|GUID|Creato un GUID per identificare la categoria.|  
    |Pacchetto|REG_SZ|GUID|Il GUID del servizio che supporta la categoria di VSPackage.|  
  
 Il servizio specificato nel Registro di sistema deve fornire un'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>per la categoria corrispondente.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
## <a name="to-create-or-identify-groups"></a>Per creare o identificare i gruppi  
  
-   Creare un tipo speciale di voce del Registro di sistema categoria [HKLM\SOFTWARE\Microsoft \Visual Studio\\*\<versione di Visual Studio >*\FontAndColors\\*\<gruppo >*]  
  
     *\<gruppo >* è il nome localizzato del gruppo.  
  
-   Popolare il Registro di sistema con due valori:  
  
    |Name|Tipo|Dati|Descrizione|  
    |----------|----------|----------|-----------------|  
    |Categoria|REG_SZ|GUID|GUID creato per identificare il gruppo.|  
    |Pacchetto|REG_SZ|GUID|Il GUID del servizio che supporta la categoria.|  
  
 Il servizio specificato nel Registro di sistema deve fornire un'implementazione di `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` per il gruppo corrispondente.  
  
## <a name="to-implement-ide-support"></a>Per implementare il supporto IDE  
  
-   Implementare <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>, che restituisce un <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>interfaccia o un `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interfaccia IDE per ogni **categoria** o il gruppo GUID specificato.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider.GetObject%2A>  
  
-   Per ogni **categoria** supporta, un VSPackage implementa un'istanza separata del <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
-   I metodi implementati tramite <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>deve fornire l'IDE con:</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
    -   Elenchi di **visualizzare gli elementi** nel **categoria.**  
  
    -   Nomi localizzabili per **visualizzare gli elementi**.  
  
    -   Visualizzare le informazioni per ogni membro di **categoria**.  
  
    > [!NOTE]
    >  Ogni **categoria** deve contenere almeno un **l'elemento**.  
  
-   L'IDE utilizza il `T:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup` interfaccia per definire un'unione di diverse categorie.  
  
     L'implementazione fornisce l'IDE con:  
  
    -   Un elenco di **categorie** che costituiscono un determinato gruppo.  
  
    -   Accesso alle istanze di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>supporto ogni **categoria** all'interno del gruppo.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>  
  
    -   Nomi dei gruppi localizzabile.  
  
-   Aggiornamento dell'IDE:  
  
     L'IDE memorizza nella cache le informazioni sulla **carattere e colori** impostazioni. Pertanto, in caso di modifiche dell'IDE **carattere e colori** configurazione, è consigliabile verificare che la cache sia aggiornata.  
  
 Aggiornamento della cache viene eseguita tramite il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>l'interfaccia e può essere eseguita a livello globale o solo elementi.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
## <a name="to-handle-font-and-color-changes"></a>Per gestire tipi di carattere e colore viene modificato  
 Per supportare correttamente la colorazione del testo che visualizza un package VS, il servizio colorazione supporta VSPackage deve rispondere alle modifiche avviata dall'utente tramite il **tipi di carattere e colori** pagina delle proprietà. Un VSPackage esegue questa operazione:  
  
-   Gestione degli eventi generati da IDE implementando il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>  
  
     L'IDE chiama il metodo appropriato segue le modifiche apportate dall'utente di **tipi di carattere e colori** pagina. Ad esempio, chiama il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A>metodo se si seleziona un nuovo tipo di carattere.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents.OnFontChanged%2A>  
  
     -oppure-  
  
-   L'IDE per le modifiche di polling.  
  
     Questo può avvenire tramite implementato dal sistema <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> Sebbene principalmente per il supporto della persistenza, il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A>metodo può essere utilizzato per ottenere informazioni di carattere e colori per **visualizzare gli elementi**.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage.GetItem%2A> Per ulteriori informazioni, vedere [l'accesso a carattere archiviati e le impostazioni dei colori](../extensibility/accessing-stored-font-and-color-settings.md).  
  
    > [!NOTE]
    >  Per garantire che i risultati ottenuti tramite polling siano corretti, potrebbe essere utile usare il <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>per determinare se una cache scaricamento e aggiornamento sono necessari prima di chiamare i metodi di recupero dell'interfaccia di <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>interfaccia.</xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage> </xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorCacheManager>  
  
## <a name="see-also"></a>Vedere anche  
 <xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A></xref:Microsoft.VisualStudio.OLE.Interop.IServiceProvider.QueryService%2A>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaults>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorEvents>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorStorage>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorGroup>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider></xref:Microsoft.VisualStudio.Shell.Interop.IVsFontAndColorDefaultsProvider>   
 [Recupero di tipi di carattere e le informazioni di colore per testo colorazione](../extensibility/getting-font-and-color-information-for-text-colorization.md)   
 [L'accesso alle Stored carattere e le impostazioni dei colori](../extensibility/accessing-stored-font-and-color-settings.md)   
 [Procedura: accedere ai tipi di carattere incorporati e combinazione di colori](../extensibility/how-to-access-the-built-in-fonts-and-color-scheme.md)   
 [Tipo di carattere e colore Panoramica](../extensibility/font-and-color-overview.md)
