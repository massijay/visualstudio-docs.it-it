---
title: "IDebugMethodField::EnumLocals | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "IDebugMethodField::EnumLocals"
helpviewer_keywords: 
  - "Metodo IDebugMethodField::EnumLocals"
ms.assetid: b0456a6d-2b96-49e2-a871-516571b4f6a5
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# IDebugMethodField::EnumLocals
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Crea un enumeratore per le variabili locali selezionate del metodo.  
  
## Sintassi  
  
```cpp#  
HRESULT EnumLocals(   
   IDebugAddress*     pAddress,  
   IEnumDebugFields** ppLocals  
);  
```  
  
```c#  
int EnumLocals(  
   IDebugAddress        pAddress,   
   out IEnumDebugFields ppLocals  
);  
```  
  
#### Parametri  
 `pAddress`  
 \[in\]  [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) Un oggetto che rappresenta l'indirizzo di debug che seleziona il contesto o l'ambito da cui ottenere le variabili locali.  
  
 `ppLocals`  
 \[out\]  Restituisce [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md) un oggetto che rappresenta un elenco di locali; in caso contrario, restituisce un valore null se non vi sono locali.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK o restituisce S\_FALSE se non vi sono locali.  In caso contrario, restituisce un codice di errore.  
  
## Note  
 Solo le variabili definite all'interno del blocco contenente l'indirizzo specificato di debug vengono enumerate.  Se tutti i locali incluse variabili locali generati dal compilatore sono necessari, chiamare [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md) il metodo.  
  
 Un metodo può contenere più contesti o i blocchi di definizione.  Ad esempio, il seguente metodo inventato contiene tre ambiti, i due blocchi interni e il corpo del metodo.  
  
```c#  
public void func(int index)  
{  
    // Method body scope  
    int a = 0;  
    if (index == 1)  
    {  
        // Inner scope 1  
        int temp1 = a;  
    }  
    else  
    {  
        // Inner scope 2  
        int temp2 = a;  
    }  
}  
```  
  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md) l'oggetto rappresenta il metodo stesso di `func` .  Chiamando il metodo di `EnumLocals` con [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md) un insieme all'indirizzo di `Inner Scope 1` restituisce un'enumerazione che contiene la variabile di `temp1` , ad esempio.  
  
## Vedere anche  
 [IDebugMethodField](../../../extensibility/debugger/reference/idebugmethodfield.md)   
 [IDebugAddress](../../../extensibility/debugger/reference/idebugaddress.md)   
 [IEnumDebugFields](../../../extensibility/debugger/reference/ienumdebugfields.md)   
 [EnumAllLocals](../../../extensibility/debugger/reference/idebugmethodfield-enumalllocals.md)