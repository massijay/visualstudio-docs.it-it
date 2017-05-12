---
title: "IVariantChangeType::ChangeType | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IVariantChangeType.ChangeType
apilocation: scrobj.dll
helpviewer_keywords: 
  - "IVariantChangeType::ChangeType"
ms.assetid: 52374764-c42e-49af-a219-ee00c535a118
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# IVariantChangeType::ChangeType
Accetta un valore variabile e crea un nuovo variant con un tipo specificato.  
  
## Sintassi  
  
```  
HRESULT ChangeType(  
   VARIANT*  pvarDst,  
   VARIANT*  pvarSrc,  
   LCID  lcid,  
   VARTYPE  vtNew  
);  
```  
  
#### Parametri  
 `pvarDst`  
 \[in, out\] variante di Oggetto per contenere il valore rappresentato da `pvarSrc`, ma con il tipo specificato da `vtNew`.  
  
 `pvarSrc`  
 \[in\] valore variabile di Oggetto per convertire un nuovo tipo.  
  
 `lcid`  
 \[in\] il contesto delle impostazioni locali da utilizzare quando convertono gli argomenti a o dalle stringhe.  
  
 `vtNew`  
 \[in\] specifica il tipo `pvarDst` diventino.  
  
## Valore restituito  
 Il metodo restituisce un tipo `HRESULT`.  I valori possibili sono, ma non sono limitati a, quelli nella tabella seguente.  
  
|Valore|Descrizione|  
|------------|-----------------|  
|`S_OK`|Il metodo è riuscito.|  
  
## Note  
 Gli argomenti `pvarSrc` e `pvarDst` possono essere uguali, nel qual caso il valore originale viene sovrascritto.  Questo metodo passa `pvarDst` alla funzione `VariantClear` e di conseguenza `pvarDst` deve essere inizializzato su un valore valido.  
  
## Vedere anche  
 [Interfaccia IVariantChangeType](../../winscript/reference/ivariantchangetype-interface.md)