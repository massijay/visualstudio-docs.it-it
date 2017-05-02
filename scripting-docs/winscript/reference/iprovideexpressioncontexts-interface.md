---
title: "Interfaccia IProvideExpressionContexts | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
helpviewer_keywords: 
  - "Interfaccia IProvideExpressionContexts"
ms.assetid: e4c70f2c-7d86-4fdc-a1cb-f5a0bb8ed037
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Interfaccia IProvideExpressionContexts
Consente di enumerare i contesti di espressione noti da un componenti specifici.  I moduli di gestione di script in genere implementano l'interfaccia.  
  
 L'amministratore processo di debug utilizza questa interfaccia per trovare tutti i contesti globali di espressione associati a un thread specificato.  
  
> [!NOTE]
>  Questa interfaccia viene chiamata dal thread desiderati.  Spetta al implementatore per identificare il thread corrente e restituire un enumeratore appropriato.  
  
## Metodi  
 Oltre ai metodi ereditati da `IUnknown`, l'interfaccia `IProvideExpressionContexts` espone i metodi seguenti.  
  
|Metodo|Descrizione|  
|------------|-----------------|  
|[IProvideExpressionContexts::EnumExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-enumexpressioncontexts.md)|Restituisce un enumeratore i contesti di espressione noti che questo componente.|