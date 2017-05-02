---
title: "Interfaccia IDebugFormatter | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugFormatter"
ms.assetid: 022142d4-c8e1-47ae-b771-3e24953293e5
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDebugFormatter
Consente a un linguaggio o un IDE personalizzare la conversione tra valori VARIABILI o tipi e stringhe di VARTYPE.  
  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IDebugFormatter` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugFormatter::GetStringForVariant](../../winscript/reference/idebugformatter-getstringforvariant.md)|Restituisce una stringa che rappresenta il valore VARIABILE specificato.|  
|[IDebugFormatter::GetVariantForString](../../winscript/reference/idebugformatter-getvariantforstring.md)|Restituisce un VARIANT contenente la stringa specificata.|  
|[IDebugFormatter::GetStringForVarType](../../winscript/reference/idebugformatter-getstringforvartype.md)|Restituisce una stringa che rappresenta il valore specificato di VARTYPE.|