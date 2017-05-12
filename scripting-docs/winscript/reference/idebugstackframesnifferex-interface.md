---
title: "Interfaccia IDebugStackFrameSnifferEx | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugStackFrameSnifferEx"
ms.assetid: fd6cf744-dee7-45f2-9a90-355b90372923
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDebugStackFrameSnifferEx
Consente di enumerare gli stack frame logici utilizzati da un componente.  I moduli di gestione di script in genere implementano l'interfaccia.  L'amministratore processo di debug utilizza questa interfaccia per trovare tutti gli stack frame associati a un thread specificato.  
  
> [!NOTE]
>  Questa interfaccia viene chiamata dal thread desiderati.  L'implementazione di deve identificare il thread corrente e restituire un enumeratore appropriato.  
  
 Oltre ai metodi ereditati da `IDebugStackFrameSniffer`, l'interfaccia `IDebugStackFrameSnifferEx` espone i metodi seguenti.  
  
## Metodi nell'ordine Vtable  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugStackFrameSnifferEx::EnumStackFramesEx](../../winscript/reference/idebugstackframesnifferex-enumstackframesex.md)|Restituisce un enumeratore stack frame del thread corrente.|