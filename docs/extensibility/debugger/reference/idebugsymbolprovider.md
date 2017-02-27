---
title: "IDebugSymbolProvider | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugSymbolProvider"
helpviewer_keywords: 
  - "Interfaccia IDebugSymbolProvider"
ms.assetid: df5f095f-1dee-46f9-84cf-92417c71d5fb
caps.latest.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 14
---
# IDebugSymbolProvider
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Questa interfaccia rappresenta un provider di simboli che fornisce i simboli e i tipi, restituendo li come campi.  
  
## Sintassi  
  
```  
IDebugSymbolProvider : IUnknown  
```  
  
## Note per gli implementatori  
 Un provider di simbolo deve implementare questa interfaccia per definire il simbolo e le informazioni sul tipo a un analizzatore di espressioni.  
  
## Note per i chiamanti  
 Questa interfaccia viene ottenuta mediante la funzione di `CoCreateInstance` di COM \(per i provider non gestiti di simboli\) o quando si caricano l'assembly corretto di codice gestito e viene creata un'istanza del provider del simbolo in base alle informazioni presenti in tale assembly.  Il motore di debug creare un'istanza del provider dei simboli per l'utilizzo di coordinamento con l'analizzatore di espressioni.  Vedere l'esempio relativo a un approccio a creare un'istanza dell'interfaccia.  
  
## Metodi nell'ordine di Vtable  
 Nella tabella seguente sono elencati i metodi di `IDebugSymbolProvider`.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|`Initialize`|Deprecata.  Non utilizzare.|  
|`Uninitialize`|Deprecata.  Non utilizzare.|  
|[GetContainerField](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontainerfield.md)|Ottiene il campo contenente l'indirizzo di debug.|  
|`GetField`|Deprecata.  Non utilizzare.|  
|[GetAddressesFromPosition](../Topic/IDebugSymbolProvider::GetAddressesFromPosition.md)|Esegue il mapping di una posizione di documento in una matrice degli indirizzi di debug.|  
|[GetAddressesFromContext](../../../extensibility/debugger/reference/idebugsymbolprovider-getaddressesfromcontext.md)|Esegue il mapping di un contesto di documento in una matrice degli indirizzi di debug.|  
|[GetContextFromAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getcontextfromaddress.md)|Esegue il mapping di un indirizzo di debug in un contesto del documento.|  
|[GetLanguage](../../../extensibility/debugger/reference/idebugsymbolprovider-getlanguage.md)|Ottiene il linguaggio utilizzato per compilare il codice all'indirizzo di debug.|  
|`GetGlobalContainer`|Deprecata.  Non utilizzare.|  
|[GetMethodFieldsByName](../Topic/IDebugSymbolProvider::GetMethodFieldsByName.md)|Ottiene il campo che rappresenta il nome di un metodo completo.|  
|[GetClassTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-getclasstypebyname.md)|Ottiene il tipo di campo della classe che rappresenta un nome di classe completo.|  
|[GetNamespacesUsedAtAddress](../../../extensibility/debugger/reference/idebugsymbolprovider-getnamespacesusedataddress.md)|Crea un enumeratore per gli spazi dei nomi associati all'indirizzo di debug.|  
|[GetTypeByName](../../../extensibility/debugger/reference/idebugsymbolprovider-gettypebyname.md)|Esegue il mapping di un nome di simbolo a un tipo di simboli.|  
|[GetNextAddress](../Topic/IDebugSymbolProvider::GetNextAddress.md)|ottiene l'indirizzo di debug che segue un indirizzo specificato di debug in un metodo.|  
  
## Note  
 Questa interfaccia esegue il mapping tra le posizioni del documento negli indirizzi di debug e viceversa.  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Esempio  
 In questo esempio viene illustrato come creare un'istanza del provider dei simboli, specificando il GUID \(un motore di debug necessario conoscere questo valore\).  
  
```cpp#  
// A debug engine uses its own symbol provider and would know the GUID  
// of that provider.  
IDebugSymbolProvider *GetSymbolProvider(GUID *pSymbolProviderGuid)  
{  
    // This is typically defined globally.  For this example, it is  
    // defined here.  
    static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0Exp";  
    IDebugSymbolProvider *pProvider = NULL;  
    if (pSymbolProviderGuid != NULL) {  
        CLSID clsidProvider = { 0 };  
        ::GetSPMetric(*pSymbolProviderGuid,  
                      storetypeFile,  
                      metricCLSID,  
                      &clsidProvider,  
                      strRegistrationRoot);  
        if (IsEqualGUID(clsidProvider,GUID_NULL)) {  
            // No file type provider, try metadata provider.  
            ::GetSPMetric(*pSymbolProviderGuid,  
                          ::storetypeMetadata,  
                          metricCLSID,  
                          &clsidProvider,  
                          strRegistrationRoot);  
        }  
        if (!IsEqualGUID(clsidProvider,GUID_NULL)) {  
            CComPtr<IDebugSymbolProvider> spSymbolProvider;  
            spSymbolProvider.CoCreateInstance(clsidProvider);  
            if (spSymbolProvider != NULL) {  
                pProvider = spSymbolProvider.Detach();  
            }  
        }  
    }  
    return(pProvider);  
}  
```  
  
## Vedere anche  
 [Interfacce del Provider di simboli](../../../extensibility/debugger/reference/symbol-provider-interfaces.md)