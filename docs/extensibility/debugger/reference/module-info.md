---
title: "MODULE_INFO | Microsoft Docs"
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
  - "MODULE_INFO"
helpviewer_keywords: 
  - "Struttura MODULE_INFO"
ms.assetid: f2e06180-1ab3-4eb5-a428-7994cceb61b6
caps.latest.revision: 8
caps.handback.revision: 8
ms.author: "gregvanl"
manager: "ghogen"
---
# MODULE_INFO
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Viene descritto un modulo specifico \(DLL, EXE, o assembly\).  
  
## Sintassi  
  
```cpp#  
typedef struct tagMODULE_INFO {   
   MODULE_INFO_FIELDS dwValidFields;  
   BSTR               m_bstrName;  
   BSTR               m_bstrUrl;  
   BSTR               m_bstrVersion;  
   BSTR               m_bstrDebugMessage;  
   UINT64             m_addrLoadAddress;  
   UINT64             m_addrPreferredLoadAddress;  
   DWORD              m_dwSize;  
   DWORD              m_dwLoadOrder;  
   FILETIME           m_TimeStamp;  
   BSTR               m_bstrUrlSymbolLocation;  
   MODULE_FLAGS       m_dwModuleFlags;  
} MODULE_INFO;  
```  
  
```c#  
public struct MODULE_INFO {   
   public uint     dwValidFields;  
   public string   m_bstrName;  
   public string   m_bstrUrl;  
   public string   m_bstrVersion;  
   public string   m_bstrDebugMessage;  
   public ulong    m_addrLoadAddress;  
   public ulong    m_addrPreferredLoadAddress;  
   public uint     m_dwSize;  
   public uint     m_dwLoadOrder;  
   public FILETIME m_TimeStamp;  
   public string   m_bstrUrlSymbolLocation;  
   public uint     m_dwModuleFlags;  
};  
```  
  
## Membri  
 dwValidFields  
 Una combinazione di flag [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md) dall'enumerazione che specifica quali campi vengono compilati.  
  
 m\_bstrName  
 Il nome del modulo.  
  
 m\_bstrUrl  
 il modulo URL.  
  
 m\_bstrVersion  
 La versione del modulo.  
  
 m\_bstrDebugMessage  
 Un messaggio facoltativo sul modulo, ad esempio, “simboli non può essere caricata.„  
  
 m\_addrLoadAddress  
 L'indirizzo del caricamento dei moduli.  
  
 m\_addrPreferredLoadAddress  
 L'indirizzo preferita del caricamento dei moduli.  
  
 m\_dwSize  
 Le dimensioni del form.  
  
 m\_dwLoadOrder  
 L'ordine di caricamento del form.  
  
 m\_TimeStamp  
 Il tempo il file di simboli ultima modifica.  
  
 m\_bstrUrlSymbolLocation  
 La posizione dei file di simboli \(ad esempio, “.  \\ "\) specificato nel modulo.  Utilizzato come posizione iniziale per individuare i simboli per un modulo.  
  
 m\_dwModuleFlags  
 Una combinazione di flag [MODULE\_FLAGS](../../../extensibility/debugger/reference/module-flags.md) dall'enumerazione che descrive il form.  
  
## Note  
 Questa struttura viene passata [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md) al metodo in cui viene soddisfatta.  
  
 Questa struttura corrisponde a ogni modulo elencato nella finestra di **moduli** .  
  
## Requisiti  
 intestazione: msdbg.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [MODULE\_INFO\_FIELDS](../../../extensibility/debugger/reference/module-info-fields.md)   
 [MODULE\_FLAGS](../../../extensibility/debugger/reference/module-flags.md)   
 [GetInfo](../../../extensibility/debugger/reference/idebugmodule2-getinfo.md)