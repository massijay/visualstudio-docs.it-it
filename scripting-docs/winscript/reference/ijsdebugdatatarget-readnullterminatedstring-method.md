---
title: "Metodo IJsDebugDataTarget::ReadNullTerminatedString | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: IJsDebugDataTarget.ReadNullTerminatedString
apilocation: jscript9diag.dll
ms.assetid: 64683b39-6fc2-40c4-82ae-2a6f58d392d5
caps.latest.revision: 4
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 4
---
# Metodo IJsDebugDataTarget::ReadNullTerminatedString
Legge il numero di caratteri specificato dalla destinazione.  
  
## Sintassi  
  
```  
HRESULT ReadNullTerminatedString(  
   UINT64 address,  
   UINT16 characterSize,  
   UINT32 maxCharacters,  
   BSTR *pString  
);  
```  
  
#### Parametri  
 `address`  
 \[in\] Indirizzo da cui leggere.  
  
 `characterSize`  
 \[in\] dimensione di ciascun carattere della stringa  
  
 `maxCharacters`  
 \[in\] Numero massimo di caratteri da leggere. Il valore maxCharacters deve essere accettabile.  Qualsiasi richiesta per più di 128 MB di memoria avrà esito negativo.  Se la stringa è maggiore di maxCharacters, la stringa risultante sarà troncata dopo il valore di maxCharacters.  
  
 `pString`  
 \[out\] Stringa BSTR letta dalla destinazione.  
  
## Valore restituito  
  
## Note  
 Restituisce S\_FALSE se troncato.  
  
## Requisiti  
 **Intestazione:** jscript9diag.h  
  
## Vedere anche  
 [Interfaccia IJsDebugDataTarget](../../winscript/reference/ijsdebugdatatarget-interface.md)