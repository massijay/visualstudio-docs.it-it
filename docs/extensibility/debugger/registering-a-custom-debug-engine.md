---
title: "Registrazione di un motore di Debug personalizzato | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "motori di debug, la registrazione"
ms.assetid: 9984cd3d-d34f-4662-9ace-31766499abf5
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# Registrazione di un motore di Debug personalizzato
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Il motore di debug debba registrarsi in quanto una class factory seguenti convenzioni COM, nonché registrare con Visual Studio tramite la sottochiave del Registro di sistema di Visual Studio.  
  
> [!NOTE]
>  Un esempio di come registrare un motore di debug sono reperibili nell'esempio TextInterpreter, che viene compilato come parte di [Tutorial: Building a Debug Engine Using ATL COM](http://msdn.microsoft.com/it-it/9097b71e-1fe7-48f7-bc00-009e25940c24).  
  
## Processo del Server di DLL  
 In genere, un motore di debug viene implementato nella propria DLL come server COM. Ciò significa che il motore di debug deve registrare il CLSID del factory classe con COM prima di Visual Studio possono accedervi. Quindi il motore di debug è necessario registrarsi con Visual Studio stesso per stabilire le proprietà, altrimenti noto come metriche, il debug supporta del motore. La scelta delle metriche che vengono scritti nella sottochiave del Registro di sistema di Visual Studio per il motore di debug dipende dalle funzionalità che supporta il motore di debug.  
  
 [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md) descrive non solo le posizioni del Registro di sistema necessarie per la registrazione di un motore di debug; vengono inoltre descritte la libreria dbgmetric.lib, che contiene un numero di funzioni utili e le dichiarazioni per gli sviluppatori in C\+\+ che consentono la modifica del Registro di sistema più semplice.  
  
### Esempio  
 Nell'esempio è un esempio tipico \(dall'esempio TextInterpreter\) in cui viene illustrato come utilizzare il `SetMetric` funzione \(da dbgmetric.lib\), per registrare un motore di debug con Visual Studio. Le metriche passate sono anche definite in dbgmetric.lib.  
  
> [!NOTE]
>  TextInterpreter è un motore di debug di base; non implementa e pertanto non viene registrato, ovvero tutte le altre caratteristiche. Un motore di debug più completato avrebbe un elenco di `SetMetric` supporta chiamate o equivalenti, uno per ogni funzionalità, il motore di debug.  
  
```  
// Define base registry subkey to Visual Studio.  
static const WCHAR strRegistrationRoot[] = L"Software\\Microsoft\\VisualStudio\\8.0";  
  
HRESULT CTextInterpreterModule::RegisterServer(BOOL bRegTypeLib, const CLSID * pCLSID)  
{  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricName, L"Text File", false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricCLSID, CLSID_Engine, false, strRegistrationRoot);  
    SetMetric(metrictypeEngine, __uuidof(Engine), metricProgramProvider, CLSID_MsProgramProvider, false, strRegistrationRoot);  
  
    return base::RegisterServer(bRegTypeLib, pCLSID);  
}  
```  
  
## Vedere anche  
 [Creazione di un motore di Debug personalizzato](../../extensibility/debugger/creating-a-custom-debug-engine.md)   
 [Helper SDK per il debug](../../extensibility/debugger/reference/sdk-helpers-for-debugging.md)   
 [Tutorial: Building a Debug Engine Using ATL COM](http://msdn.microsoft.com/it-it/9097b71e-1fe7-48f7-bc00-009e25940c24)