---
title: "Interfaccia IDebugStackFrameSniffer | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IDebugStackFrameSniffer"
ms.assetid: 5669598e-a6bd-4694-9cb2-bd908be72bed
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IDebugStackFrameSniffer
Consente di enumerare gli stack frame logici utilizzati da un componente.  I moduli di gestione di script in genere implementano l'interfaccia.  L'amministratore processo di debug utilizza questa interfaccia per trovare tutti gli stack frame associati a un thread specificato.  
  
> [!NOTE]
>  Il debugger chiama questa interfaccia dal thread desiderati.  Il modulo di gestione di script deve identificare il thread corrente e restituire un enumeratore appropriato.  
  
## Metodi  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IDebugStackFrameSniffer` espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IDebugStackFrameSniffer::EnumStackFrames](../../winscript/reference/idebugstackframesniffer-enumstackframes.md)|Restituisce un enumeratore stack frame del thread corrente.|