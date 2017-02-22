---
title: "IDebugClassField::DoesInterfaceExist | Microsoft Docs"
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
  - "IDebugClassField::DoesInterfaceExist"
helpviewer_keywords: 
  - "Metodo IDebugClassField::DoesInterfaceExist"
ms.assetid: cc0c8642-1a76-4fda-a309-7018a34883c9
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# IDebugClassField::DoesInterfaceExist
[!INCLUDE[vs2017banner](../../../code-quality/includes/vs2017banner.md)]

Determina se una specifica interfaccia è definita nella classe.  
  
## Sintassi  
  
```cpp#  
HRESULT DoesInterfaceExist(   
   LPCOLESTR pszInterfaceName  
);  
```  
  
```c#  
int DoesInterfaceExist(  
   [In] string pszInterfaceName  
);  
```  
  
#### Parametri  
 `pszInterfaceName`  
 \[in\]  Stringa contenente il nome dell'interfaccia per trovare.  
  
## Valore restituito  
 Se l'operazione riesce, restituisce S\_OK, restituisce S\_FALSE se l'interfaccia non esiste; in caso contrario, restituisce un codice di errore.  
  
## Note  
 Questo metodo in effetti ottiene un'enumerazione di tutte le interfacce e individuare l'elenco un'interfaccia corrispondente.  
  
## Vedere anche  
 [IDebugClassField](../../../extensibility/debugger/reference/idebugclassfield.md)