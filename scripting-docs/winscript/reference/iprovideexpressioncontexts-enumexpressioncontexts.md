---
title: "IProvideExpressionContexts::EnumExpressionContexts | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IProvideExpressionContexts.EnumExpressionContexts
apilocation: jscript.dll
helpviewer_keywords: 
  - "IProvideExpressionContexts::EnumExpressionContexts"
ms.assetid: ec5f0065-00df-41e6-b480-4c04ba464872
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IProvideExpressionContexts::EnumExpressionContexts
Restituisce un enumeratore i contesti di espressione noti che questo componente.  
  
## Sintassi  
  
```  
HRESULT EnumExpressionContexts(  
   IEnumDebugExpressionContexts**  ppedec  
);  
```  
  
#### Parametri  
 `ppedec`  
 \[out\] enumeratore i contesti di espressione noti che questo componente.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 L'amministratore processo di debug utilizza questo metodo per trovare tutti i contesti globali di espressione associati a un thread specificato.  
  
> [!NOTE]
>  Questo metodo viene chiamato dal thread desiderati.  Spetta al implementatore per identificare il thread corrente e restituire un enumeratore appropriato.  
  
## Vedere anche  
 [Interfaccia IProvideExpressionContexts](../../winscript/reference/iprovideexpressioncontexts-interface.md)