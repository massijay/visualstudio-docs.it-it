---
title: "Sequenza di inizializzazione dei sottotipi di progetto | Microsoft Docs"
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
  - "progetto (sottotipi), sequenza di inizializzazione"
ms.assetid: f657f8c3-5e68-4308-9971-e81e3099ba29
caps.latest.revision: 15
caps.handback.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
---
# Sequenza di inizializzazione dei sottotipi di progetto
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

The environment constructs a project by calling the base project factory implementation of <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>.  La costruzione di un sottotipo di progetto inizia quando l'ambiente determina che l'elenco di tipi di progetto GUID per l'estensione di un file di progetto non è vuoto.  L'estensione e il GUID del progetto di file di progetto specificano se il progetto è un tipo di progetto csprcs o di [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .  Ad esempio, l'estensione vbproj e {F184B08F\- C81 C\-45F6\-A57F\-5ABD9991F28F} identifica un progetto [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] .  
  
## L'inizializzazione dell'ambiente di sottotipi di progetto  
 La procedura descritta di seguito vengono illustrate la sequenza di inizializzazione per un sistema di progetto aggregato dai sottotipi più di progetto.  
  
1.  L'ambiente chiama l'entity\_M:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject\(System.String, System.String, System.String, System.UInt32, System.Guid@, System.IntPtr@, System.Int32@\) di base del progetto e quando il progetto analizza il file di progetto rileva che l'elenco di aggregazione del tipo di progetto GUID non è `null`.  Il progetto viene interrotta direttamente nella creazione del progetto.  
  
2.  Il progetto chiama `QueryService` su servizio di <xref:Microsoft.VisualStudio.Shell.Interop.SVsCreateAggregateProject> per creare un sottotipo di progetto tramite l'implementazione dell'ambiente del metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> .  All'interno del metodo l'ambiente effettua chiamate di funzioni ricorsive alle implementazioni di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>, di `M:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject(System.Object)` metodi e di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A> mentre sta scorrendo l'elenco di tipo di progetto GUID, a partire dal sottotipo più esterno del progetto.  
  
     I seguenti dettagli passaggi di inizializzazione.  
  
    1.  L'implementazione del metodo di `HrCreateInnerProj```di chiamate al metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> con la seguente dichiarazione di funzione:  
  
<CodeContentPlaceHolder>0</CodeContentPlaceHolder>  
         Quando questa funzione viene chiamata per la prima volta, ovvero, per il sottotipo più esterno del progetto, i parametri `pOuter` e `pOwner` vengono passati come `null` e la funzione imposta il sottotipo più esterno `IUnknown` di progetto a `pOuter`.  
  
    2.  Dopo la funzione di `HrCreateInnerProj` di chiamate dell'ambiente con il secondo tipo di progetto GUID nell'elenco.  Questo GUID corrisponde alla seconda esecuzione di istruzioni interna del sottotipo di progetto in nel progetto di base nella sequenza di aggregazione.  
  
    3.  `pOuter` ora sta puntando a `IUnknown` del sottotipo più esterno del progetto e chiamate di `HrCreateInnerProj` l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> è seguito da una chiamata all'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A>.  Nel metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A> passate in `IUnknown` di controllo del sottotipo più esterno del progetto, `pOuter`.  Le necessità di proprietà di progetto \(sottotipo interno del progetto\) di creare il relativo oggetto del progetto di aggregazione di seguito.  Nell'implementazione del metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.SetInnerProject%2A> viene passato un puntatore a `IUnknown` del progetto interno che sta eseguendo l'aggregazione.  Questi due metodi creano l'oggetto di aggregazione e le implementazioni devono rispettare le regole di aggregazione COM assicurarsi che un sottotipo di progetto non viene completato tramite un conteggio dei riferimenti a se stesso.  
  
    4.  `HrCreateInnerProj` chiamare l'implementazione di <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProjectFactory.PreCreateForOuter%2A>.  In questo metodo, il sottotipo di progetto esegue il lavoro di inizializzazione.  È possibile, ad esempio, registrare gli eventi della soluzione in <xref:Microsoft.VisualStudio.Shell.Interop.IVsAggregatableProject.InitializeForOuter%2A>.  
  
    5.  `HrCreateInnerProj` viene chiamato in modo ricorsivo fino a raggiungere l'ultimo GUID \(il progetto di base\) nell'elenco.  Per ognuna di queste chiamate, i passaggi, da c a d, vengono ripetuti.  punti di`pOuter` al sottotipo più esterno `IUnknown` di progetto per ogni livello di aggregazione.  
  
 Nell'esempio vengono descritti il processo a livello di codice in una rappresentazione approssimativa del metodo di <xref:Microsoft.VisualStudio.Shell.Interop.IVsCreateAggregateProject.CreateAggregateProject%2A> mentre viene implementato dall'ambiente.  Il codice è solo un esempio; non deve essere compilato e qualsiasi controllo degli errori è stato rimosso per maggiore chiarezza.  
  
## Esempio  
  
### Codice  
  
```  
HRESULT CreateAggregateProject  
(  
    LPCOLESTR lpstrGuids,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    REFIID iidProject,   
    void **ppvProject)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpunkProj;  
    CComPtr<IVsAggregatableProject> srpAggProject;  
    CComBSTR bstrGuids = lpstrGuids;  
    BOOL fCanceled = FALSE;  
    *ppvProject = NULL;  
  
    HrCreateInnerProj(  
         bstrGuids, NULL, NULL, pszFilename, pszLocation,   
         pszName, grfCreateFlags, &srpunkProj, &fCanceled);  
    srpunkProj->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggProject));  
    srpAggProject->OnAggregationComplete();  
    srpunkProj->QueryInterface(iidProject, ppvProject);  
}  
  
HRESULT HrCreateInnerProj  
(  
    WCHAR *pwszGuids,   
    IUnknown *pOuter,   
    IVsAggregatableProject *pOwner,   
    LPCOLESTR pszFilename,   
    LPCOLESTR pszLocation,  
    LPCOLESTR pszName,   
    VSCREATEPROJFLAGS grfCreateFlags,   
    IUnknown **ppInner,   
    BOOL *pfCanceled  
)  
{  
    HRESULT hr = NOERROR;  
    CComPtr<IUnknown> srpInner;  
    CComPtr<IVsAggregatableProject> srpAggInner;  
    CComPtr<IVsProjectFactory> srpProjectFactory;  
    CComPtr<IVsAggregatableProjectFactory> srpAggPF;  
    GUID guid = GUID_NULL;  
    WCHAR *pwszNextGuids = wcschr(pwszGuids, L';');  
    WCHAR wszText[_MAX_PATH+150] = L"";  
  
    if (pwszNextGuids)  
    {  
        *pwszNextGuids++ = 0;  
    }  
  
    CLSIDFromString(pwszGuids, &guid);  
    GetProjectTypeMgr()->HrGetProjectFactoryOfGuid(  
        guid, &srpProjectFactory);  
    srpProjectFactory->QueryInterface(  
        IID_IVsAggregatableProjectFactory,   
        (void **)&srpAggPF);  
    srpAggPF->PreCreateForOuter(pOuter, &srpInner);  
    srpInner->QueryInterface(  
        IID_IVsAggregatableProject, (void **)&srpAggInner);  
  
    if (pOwner)  
    {  
        IfFailGo(pOwner->SetInnerProject(srpInner));  
    }  
  
    if (pwszNextGuids)  
    {  
        CComPtr<IUnknown> srpNextInner;  
        HrCreateInnerProj(  
            pwszNextGuids, pOuter ? pOuter : srpInner,   
            srpAggInner, pszFilename, pszLocation, pszName,   
            grfCreateFlags, &srpNextInner, pfCanceled);  
    }  
  
    return srpAggInner->InitializeForOuter(  
        pszFilename, pszLocation, pszName, grfCreateFlags,   
        IID_IUnknown, (void **)ppInner, pfCanceled);  
}  
```  
  
## Vedere anche  
 <xref:Microsoft.VisualStudio.Shell.Flavor>   
 [Progetto \(sottotipi\)](../../extensibility/internals/project-subtypes.md)