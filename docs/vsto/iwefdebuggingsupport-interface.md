---
title: Interfaccia IWefDebuggingSupport | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 0bd1c6a6-67a5-4478-b942-8b937b28f723
caps.latest.revision: "12"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 7768465f46e5344b88da9006a7de2396e3b75ba6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="iwefdebuggingsupport-interface"></a>Interfaccia IWefDebuggingSupport
  Implementata da un ambiente di debug, ad esempio Visual Studio, per semplificare il debug di App per Office. L'applicazione di Office, ad esempio Word o Excel, ottiene l'interfaccia da Visual Studio e quindi chiama i metodi dell'interfaccia in determinati momenti durante la sessione di debug.  
  
## <a name="syntax"></a>Sintassi  
  
```  
[  
    uuid(ccaf1a90-ce1c-4199-9cd6-b40c5c57a671),  
    oleautomation  
]  
interface IWefDebuggingSupport : IUnknown  
{  
    HRESULT SetWefProcessId(  
        [in] DWORD dwProcessId);  
    HRESULT GetAutoInsertExtensions(  
        [out, retval] SAFEARRAY(BSTR)* psaExtensionNames);  
}  
```  
  
## <a name="methods"></a>Metodi  
 Nella tabella seguente sono elencati i metodi che definisce l'interfaccia IWefDebuggingSupport.  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo GetAutoInsertExtensions](../vsto/getautoinsertextensions-method.md)|Ottiene informazioni sulle App per Office che devono essere inseriti automaticamente durante il debug.|  
|[Metodo SetWefProcessId](../vsto/setwefprocessid-method.md)|Fornisce l'identificatore di processo che verrà eseguito il contenuto Web estensioni Framework (WEF).|  
  
  