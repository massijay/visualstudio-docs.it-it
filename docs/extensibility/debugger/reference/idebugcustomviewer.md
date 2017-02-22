---
title: "IDebugCustomViewer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugCustomViewer"
helpviewer_keywords: 
  - "Interfaccia IDebugCustomViewer"
ms.assetid: 7aca27d3-c7b8-470f-b42c-d1e9d9115edd
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugCustomViewer
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia consente a un analizzatore di \(EE\) espressioni per visualizzare un valore di proprietà in qualsiasi formato è necessario.  
  
## Sintassi  
  
```  
IDebugCustomViewer : IUknown  
```  
  
## Note per gli implementatori  
 L'EE implementa questa interfaccia per visualizzare un valore di proprietà in un formato personalizzato.  
  
## Note per i chiamanti  
 Una chiamata alla funzione di `CoCreateInstance` di COM creare un'istanza dell'interfaccia.  `CLSID` passato a `CoCreateInstance` viene ottenuto dal Registro di sistema.  Una chiamata [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md) ottiene la posizione nel Registro di sistema.  Vedere le note per informazioni dettagliate e l'esempio.  
  
## Metodi nell'ordine di Vtable  
 questa interfaccia implementa il seguente metodo:  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[Disponibili DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md)|Effettua qualsiasi è necessario visualizzare un valore specificato.|  
  
## Note  
 Questa interfaccia viene utilizzata quando un valore della proprietà non può essere visualizzato dal normale media\-per l'esempio, con una tabella dati o un altro tipo di proprietà complessi.  Un visualizzatore personalizzato, come rappresentato dall'interfaccia di `IDebugCustomViewer` , è diverso da un visualizzatore del tipo, un programma esterno per la visualizzazione dei dati di un tipo specifico indipendentemente dall'EE.  L'EE implementa un visualizzatore personalizzato specifico nell'EE.  Un utente seleziona il tipo del visualizzatore da utilizzare, sia un visualizzatore del tipo o un visualizzatore personalizzato.  Vedere [Visualizzazione e la visualizzazione dei dati](../../../extensibility/debugger/visualizing-and-viewing-data.md) per informazioni dettagliate su questo processo.  
  
 un visualizzatore personalizzato è registrato come l'EE e, pertanto, richiede un linguaggio GUID e un fornitore GUID.  Il nome di voci del Registro di sistema o \("\) esatto è noto solo in EE.  Questa metrica viene restituito [DEBUG\_CUSTOM\_VIEWER](../../../extensibility/debugger/reference/debug-custom-viewer.md) nella struttura, che a sua volta che viene restituito da una [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)chiamata.  Il valore archiviato nella metrica è `CLSID` passato alla funzione di `CoCreateInstance` di COM \(vedere l'esempio\).  
  
 [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) la funzione, `SetEEMetric`, può essere utilizzata per registrare un visualizzatore personalizzato.  Vedere la sezione del Registro di sistema “degli analizzatori di espressioni„ di `Debugging SDK Helpers` per le chiavi del Registro di sistema specifiche di un visualizzatore personalizzato ha bisogno.  Si noti che un visualizzatore personalizzato necessaria solo una metrica \(definito dall'implementatore dell'EE\) durante l'esecuzione di un analizzatore di espressioni richiede parecchia metriche predefinita.  
  
 In genere, un visualizzatore personalizzato fornisce una visualizzazione in sola lettura di dati, poiché [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md) l'interfaccia fornita [Disponibili DisplayValue](../../../extensibility/debugger/reference/idebugcustomviewer-displayvalue.md) non dispone di metodi per modificare il valore della proprietà ad eccezione come stringa.  Per supportare modificare blocchi arbitrari di dati, l'EE implementa un'interfaccia personalizzata nello stesso oggetto che implementa l'interfaccia di `IDebugProperty3` .  Questa interfaccia quindi fornisce i metodi necessari per modificare un blocco arbitrario di dati.  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Esempio  
 In questo esempio viene illustrato come ottenere il primo visualizzatore personalizzato da una proprietà se tale proprietà potrebbe di visualizzatori personalizzati.  
  
```cpp#  
IDebugCustomViewer *GetFirstCustomViewer(IDebugProperty2 *pProperty)  
{  
    // This string is typically defined globally.  For this example, it  
    // is defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugCustomViewer *pViewer = NULL;  
    if (pProperty != NULL) {  
        CComQIPtr<IDebugProperty3> pProperty3(pProperty);  
        if (pProperty3 != NULL) {  
            HRESULT hr;  
            ULONG viewerCount = 0;  
            hr = pProperty3->GetCustomViewerCount(&viewerCount);  
            if (viewerCount > 0) {  
                ULONG viewersFetched = 0;  
                DEBUG_CUSTOM_VIEWER viewerInfo = { 0 };  
                hr = pProperty3->GetCustomViewerList(0,  
                                                     1,  
                                                     &viewerInfo,  
                                                     &viewersFetched);  
                if (viewersFetched == 1) {  
                    CLSID clsidViewer = { 0 };  
                    CComPtr<IDebugCustomViewer> spCustomViewer;  
                    // Get the viewer's CLSID from the registry.  
                    ::GetEEMetric(viewerInfo.guidLang,  
                                  viewerInfo.guidVendor,  
                                  viewerInfo.bstrMetric,  
                                  &clsidViewer,  
                                  strRegistrationRoot);  
                    if (!IsEqualGUID(clsidViewer,GUID_NULL)) {  
                        // Instantiate the custom viewer.  
                        spCustomViewer.CoCreateInstance(clsidViewer);  
                        if (spCustomViewer != NULL) {  
                            pViewer = spCustomViewer.Detach();  
                        }  
                    }  
                }  
            }  
        }  
    }  
    return(pViewer);  
}  
```  
  
## Vedere anche  
 [Interfacce di base](../../../extensibility/debugger/reference/core-interfaces.md)   
 [GetCustomViewerList](../../../extensibility/debugger/reference/idebugproperty3-getcustomviewerlist.md)   
 [Helper SDK per il debug](../../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [IDebugProperty3](../../../extensibility/debugger/reference/idebugproperty3.md)