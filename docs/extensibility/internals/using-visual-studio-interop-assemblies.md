---
title: "Utilizzo di assembly di interoperabilità di Visual Studio | Documenti di Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Visual Studio, interop assemblies
- interop assemblies, Visual Studio
- managed VSPackages, interop assemblies
ms.assetid: 1043eb95-4f0d-4861-be21-2a25395b3b3c
caps.latest.revision: 33
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
ms.openlocfilehash: 9762ba0404e739c167cadc3e9d3106c7f3ee14e8
ms.lasthandoff: 02/22/2017

---
# <a name="using-visual-studio-interop-assemblies"></a>Utilizzo di assembly di interoperabilità di Visual Studio
Assembly di interoperabilità Visual Studio consentono alle applicazioni gestite accedere alle interfacce COM che forniscono l'estensibilità di Visual Studio. Esistono alcune differenze tra le interfacce COM rette e le versioni di interoperabilità. Ad esempio, HRESULT generalmente rappresentati come valori int e devono essere gestiti nello stesso modo come eccezioni e parametri (in particolare i parametri out) vengono considerati in modo diverso.  
  
## <a name="handling-hresults-returned-to-managed-code-from-com"></a>Gestione di valori HRESULT restituiti al codice gestito da COM  
 Quando si chiama un'interfaccia COM dal codice gestito, esaminare il valore HRESULT e generare un'eccezione, se necessario. La <xref:Microsoft.VisualStudio.ErrorHandler>classe contiene il <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>metodo che genera un'eccezione COM, a seconda del valore di HRESULT passato piace</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> </xref:Microsoft.VisualStudio.ErrorHandler>  
  
 Per impostazione predefinita, <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>genera un'eccezione ogni volta che viene passato un valore HRESULT con un valore minore di zero.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> Nei casi in cui tali HRESULT sono valori accettabili e non deve essere generata alcuna eccezione, i valori di HRESULT di aggiuntive devono essere passati a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>dopo i valori vengono verificati.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A> Se il valore HRESULT sottoposto a test corrisponde a tutti i valori HRESULT passati in modo esplicito <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>, viene generata alcuna eccezione.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>  
  
> [!NOTE]
>  La <xref:Microsoft.VisualStudio.VSConstants>classe contiene le costanti per valori HRESULT più comuni, ad esempio, <xref:Microsoft.VisualStudio.VSConstants.S_OK>e <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>, e [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] HRESULT, ad esempio, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>e <xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT>.</xref:Microsoft.VisualStudio.VSConstants.VS_E_UNSUPPORTEDFORMAT> </xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> </xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL> </xref:Microsoft.VisualStudio.VSConstants.S_OK> </xref:Microsoft.VisualStudio.VSConstants> <xref:Microsoft.VisualStudio.VSConstants>fornisce inoltre i <xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A> <xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A>metodi</xref:Microsoft.VisualStudio.ErrorHandler.Failed%2A> e, che corrispondono alle macro SUCCEEDED e non riuscito di COM.</xref:Microsoft.VisualStudio.ErrorHandler.Succeeded%2A></xref:Microsoft.VisualStudio.VSConstants>  
  
 Ad esempio, si consideri la seguente chiamata di funzione, in cui <xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>è un valore restituito accettabile, ma qualsiasi altro HRESULT minore di zero rappresenta un errore.</xref:Microsoft.VisualStudio.VSConstants.E_NOTIMPL>  
  
 [!code-vb[N.&1; VSSDKHRESULTInformation](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_1.vb) ] 
 [!code-cs [VSSDKHRESULTInformation n.&1;](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_1.cs)]  
  
 Se sono presenti più valori restituiti accettabili, valori HRESULT aggiuntivi possono solo essere aggiunto all'elenco nella chiamata a <xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>.</xref:Microsoft.VisualStudio.ErrorHandler.ThrowOnFailure%2A>  
  
 [!code-vb[N.&2; VSSDKHRESULTInformation](../../extensibility/internals/codesnippet/VisualBasic/using-visual-studio-interop-assemblies_2.vb) ] 
 [!code-cs [VSSDKHRESULTInformation n.&2;](../../extensibility/internals/codesnippet/CSharp/using-visual-studio-interop-assemblies_2.cs)]  
  
## <a name="returning-hresults-to-com-from-managed-code"></a>Restituzione di valori HRESULT a COM dal codice gestito  
 Se si verifica alcuna eccezione, restituisce il codice gestito <xref:Microsoft.VisualStudio.VSConstants.S_OK>alla funzione COM che ha chiamato tale</xref:Microsoft.VisualStudio.VSConstants.S_OK> L'interoperabilità COM supporta eccezioni comuni fortemente tipizzate nel codice gestito. Ad esempio, un metodo che riceve un inaccettabile `null` argomento genera un <xref:System.ArgumentNullException>.</xref:System.ArgumentNullException>  
  
 Se non si è certi che eccezione da generare, ma si conosce il valore HRESULT si desidera tornare a COM, è possibile utilizzare il <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>metodo consente di generare un'eccezione appropriata.</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> Questa operazione funziona anche con un errore non standard, ad esempio, <xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA>.</xref:Microsoft.VisualStudio.VSConstants.VS_E_INCOMPATIBLEDOCDATA> <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>tenta di eseguire il mapping di HRESULT passato a un'eccezione fortemente tipizzata.</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A> Se ciò non è possibile, genera un'eccezione COM generica. Il risultato finale è che il valore HRESULT è passare <xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>dal codice gestito viene restituito alla funzione COM che ha chiamato tale</xref:System.Runtime.InteropServices.Marshal.ThrowExceptionForHR%2A>  
  
> [!NOTE]
>  Le eccezioni compromettono le prestazioni e servono per indicare condizioni anomale dei programmi. Le condizioni che si verificano spesso devono essere gestite inline, invece di generare un'eccezione.  
  
## <a name="iunknown-parameters-passed-as-type-void"></a>IUnknown parametri passati come tipo void * *  
 Cercare [i parametri definiti come tipo out] `void **` in COM interfaccia, ma che sono definiti come `[``iid_is``]` nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo del metodo assembly di interoperabilità.  
  
 In alcuni casi, un'interfaccia COM che genera un `IUnknown` oggetto e l'interfaccia COM quindi passa come tipo `void **`. Queste interfacce sono particolarmente importanti in quanto se la variabile viene definita come [out] nel file IDL, la `IUnknown` oggetto è con conteggio dei riferimenti con il `AddRef` (metodo). Se l'oggetto non viene gestita correttamente, si verifica una perdita di memoria.  
  
> [!NOTE]
>  Un `IUnknown` l'oggetto creato dall'interfaccia COM e restituito in una variabile [out] causa una perdita di memoria se non viene rilasciato in modo esplicito.  
  
 Metodi gestiti che gestiscono tali oggetti devono considerare <xref:System.IntPtr>come puntatore a un `IUnknown` e chiamare il <xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A>per ottenere l'oggetto.</xref:System.Runtime.InteropServices.Marshal.GetObjectForIUnknown%2A> </xref:System.IntPtr> Il chiamante deve quindi eseguire il cast il valore restituito per qualsiasi tipo è appropriato. Quando l'oggetto non è più necessario, chiamare <xref:System.Runtime.InteropServices.Marshal.Release%2A>di rilascio del mouse.</xref:System.Runtime.InteropServices.Marshal.Release%2A>  
  
 Di seguito è riportato un esempio di chiamata il <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>metodo e la gestione di `IUnknown` oggetto correttamente:</xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
```  
MyClass myclass;  
Object object;  
IntPtr pObj;  
Guid iid = Typeof(MyClass).Guid;  
int hr = windowFrame.QueryViewInterface(ref iid, out pObj);     
if (NativeMethods.Succeeded(hr))   
{  
    try   
    {  
        object = Marshal.GetObjectForIUnknown(pObj);  
        myclass = object;  
    }  
    finally   
    {  
        Marshal.Release(pObj);  
    }  
}  
else   
{  
    // error calling QueryViewInterface  
}  
```  
  
> [!NOTE]
>  I seguenti metodi sono noti per passare `IUnknown` oggetto puntatori come tipo <xref:System.IntPtr>.</xref:System.IntPtr> Gestirli come descritto in questa sezione.  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectFactory.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsOwnedProjectFactory.InitializeForOwner%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsHierarchy.GetNestedHierarchy%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsSolution.CreateProject%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsWindowFrame.QueryViewInterface%2A>  
  
-   <xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A></xref:Microsoft.VisualStudio.Shell.Interop.IVsProjectCfg2.get_CfgType%2A>  
  
## <a name="optional-out-parameters"></a>[Out] parametri facoltativi  
 Cercare i parametri che sono definiti come [out] tipo di dati (`int`, `object`e così via) in COM interfaccia, ma che sono definiti come matrici dello stesso tipo di dati nel [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo del metodo assembly di interoperabilità.  
  
 Interfacce di alcuni COM, ad esempio <xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A>, considerare [come facoltativi parametri out].</xref:Microsoft.VisualStudio.Shell.Interop.IVsCfgProvider2.GetCfgs%2A> Se non è necessario un oggetto, le interfacce COM restituiscono un `null` come il valore del parametro anziché creare l'oggetto [out] puntatore. Si tratta di un comportamento correlato alla progettazione. Per queste interfacce, `null` i puntatori vengono considerati come parte del comportamento corretto del VSPackage e viene restituito alcun errore.  
  
 Poiché Common Language Runtime non consente il valore di parametro [out] da `null`, parte del comportamento di queste interfacce progettato non è disponibili direttamente nel codice gestito. Il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metodi di assembly di interoperabilità per le interfacce interessate ovviare al problema definendo i parametri pertinenti come matrici in quanto CLR consente il passaggio di `null` matrici.  
  
 Implementazioni gestite di questi metodi è necessario inserire una `null` matrice nel parametro quando non c'è niente da restituire. In caso contrario, creare una matrice a un elemento del tipo corretto e inserire il valore restituito nella matrice.  
  
 Metodi che ricevono informazioni dalle interfacce con [out] facoltativo gestiti parametri ricevano il parametro sotto forma di matrice. È sufficiente esaminare il valore del primo elemento della matrice. Se non è `null`, considerare il primo elemento, come se fosse il parametro originale.  
  
## <a name="passing-constants-in-pointer-parameters"></a>Costanti passando nei parametri di puntatore  
 Cercare i parametri che vengono definite come [in] i puntatori a interfaccia COM, ma che sono definiti come un <xref:System.IntPtr>digitare il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo del metodo assembly di interoperabilità.</xref:System.IntPtr>  
  
 Un problema analogo si verifica quando un'interfaccia COM passa un valore speciale, ad esempio 0, -1 o -2, anziché un puntatore all'oggetto. A differenza di [!INCLUDE[vcprvc](../../code-quality/includes/vcprvc_md.md)], CLR non costanti eseguire il cast come oggetti. Al contrario, il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] assembly di interoperabilità definisce il parametro come un <xref:System.IntPtr>tipo.</xref:System.IntPtr>  
  
 Implementazioni gestite di questi metodi devono sfruttare il fatto che la <xref:System.IntPtr>classe dispone di entrambi `int` e `void *` costruttori per creare un <xref:System.IntPtr>da un oggetto o una costante integer, come appropriato.</xref:System.IntPtr> </xref:System.IntPtr>  
  
 Metodi che ricevono gestiti <xref:System.IntPtr>devono utilizzare i parametri di questo tipo di <xref:System.IntPtr>operatori di conversione per gestire i risultati di tipo.</xref:System.IntPtr> </xref:System.IntPtr> Convertire innanzitutto il <xref:System.IntPtr>a `int` e verificarne il funzionamento costanti integer pertinente.</xref:System.IntPtr> Se non corrispondono, convertirlo in un oggetto del tipo richiesto e continuare.  
  
 Per esempi, vedere <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>e <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A>.</xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenSpecificEditor%2A> </xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShellOpenDocument.OpenStandardEditor%2A>  
  
## <a name="ole-return-values-passed-as-out-parameters"></a>OLE restituiscono i valori passati come [parametri out]  
 Cerca i metodi che dispongono di un `retval` valore restituito dell'interfaccia COM, ma che hanno un `int` restituire valore e un ulteriore [parametro di matrice in out] il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipo del metodo assembly di interoperabilità. Deve essere chiaro che questi metodi richiedono una gestione speciale in quanto il [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] prototipi di metodo di assembly di interoperabilità hanno un parametro rispetto ai metodi di interfaccia COM.  
  
 Numero di interfacce COM che gestiscono attività OLE invia informazioni sullo stato OLE al programma chiamante archiviato nel `retval` restituito dell'interfaccia. Anziché utilizzare un valore restituito, il corrispondente [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] metodi di assembly di interoperabilità inviano le informazioni relative al programma chiamante archiviato in [out] il parametro di matrice.  
  
 Implementazioni gestite di questi metodi devono creare una matrice a elemento singolo dello stesso tipo come parametro [out] e inserirlo nel parametro. Il valore dell'elemento della matrice deve essere identico COM appropriato `retval`.  
  
 Metodi gestiti che chiamano le interfacce di questo tipo devono inserire il primo elemento dalla matrice [out]. Questo elemento può essere considerato come se fosse un `retval` valore restituito dall'interfaccia COM corrispondente.  
  
## <a name="see-also"></a>Vedere anche  
 [Interoperabilità con codice non gestito](http://msdn.microsoft.com/Library/ccb68ce7-b0e9-4ffb-839d-03b1cd2c1258)
