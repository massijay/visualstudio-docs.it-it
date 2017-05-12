---
title: "Interfaccia IWefDebuggingSupport"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
ms.assetid: 0bd1c6a6-67a5-4478-b942-8b937b28f723
caps.latest.revision: 12
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 11
---
# Interfaccia IWefDebuggingSupport
  Implementata da un ambiente di debug, ad esempio Visual Studio, per facilitare il debug di applicazioni per Office.  L'applicazione di Office, quali Word o Excel, ottiene questa interfaccia da Visual Studio e quindi chiama i metodi dell'interfaccia a determinati punti durante la sessione di debug.  
  
## Sintassi  
  
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
  
## Metodi  
 Nella tabella seguente sono elencati i metodi che l'interfaccia IWefDebuggingSupport definisce.  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[Metodo GetAutoInsertExtensions](../vsto/getautoinsertextensions-method.md)|Ottiene informazioni sulle applicazioni per Office che devono essere inserite automaticamente durante il debug.|  
|[Metodo SetWefProcessId](../vsto/setwefprocessid-method.md)|Fornisce l'identificatore del processo che esegue il contenuto Web di Framework \(WEF\) extensions.|  
  
  