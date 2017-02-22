---
title: "DEBUG_ADDRESS | Microsoft Docs"
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
  - "DEBUG_ADDRESS"
helpviewer_keywords: 
  - "Struttura DEBUG_ADDRESS"
ms.assetid: 79f5e765-9aac-4b6e-82ef-bed88095e9ba
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# DEBUG_ADDRESS
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

questa struttura rappresenta un indirizzo.  
  
## Sintassi  
  
```cpp  
typedef struct _tagDEBUG_ADDRESS {  
   ULONG32             ulAppDomainID;  
   GUID                guidModule;  
   _mdToken            tokClass;  
   DEBUG_ADDRESS_UNION addr;  
} DEBUG_ADDRESS;  
```  
  
```c#  
public struct DEBUG_ADDRESS {  
   public uint                ulAppDomainID;  
   public Guid                guidModule;  
   public int                 tokClass;  
   public DEBUG_ADDRESS_UNION addr;  
}  
```  
  
## termini  
 ulAppDomainID  
 L'id processo  
  
 guidModule  
 Il GUID del modulo che contiene questo indirizzo.  
  
 tokClass  
 il token che identifica la classe o il tipo di questo indirizzo.  
  
> [!NOTE]
>  Questo valore è specifico di un provider del simbolo e pertanto non ha senso generale oltre a identificatore per un tipo di classe.  
  
 addr  
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md) Una struttura, che contiene un'unione di strutture che descrivono i diversi tipi di indirizzo.  il valore `addr`.`dwKind` deriva [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md) dall'enumerazione, che viene illustrato come interpretare l'unione.  
  
## Note  
 Questa struttura viene passata [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md) al metodo da riempire.  
  
 **Avviso \[C\+\+ solo\]**  
  
 Se `addr.dwKind` è `ADDRESS_KIND_METADATA_LOCAL` e se `addr.addr.addrLocal.pLocal` non è un valore null, è necessario chiamare `Release` sul puntatore di token:  
  
```  
if (addr.dwKind == ADDRESS_KIND_METADATA_LOCAL &&  addr.addr.addrLocal.pLocal != NULL)  
{  
    addr.addr.addrLocal.pLocal->Release();  
}  
```  
  
## Requisiti  
 intestazione: sh.h  
  
 Spazio dei nomi: Microsoft.VisualStudio.Debugger.Interop  
  
 Assembly: Microsoft.VisualStudio.Debugger.Interop.dll  
  
## Vedere anche  
 [Strutture e unioni](../../../extensibility/debugger/reference/structures-and-unions.md)   
 [GetAddress](../../../extensibility/debugger/reference/idebugaddress-getaddress.md)   
 [DEBUG\_ADDRESS\_UNION](../../../extensibility/debugger/reference/debug-address-union.md)   
 [ADDRESS\_KIND](../../../extensibility/debugger/reference/address-kind.md)