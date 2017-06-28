---
title: "IDiaSymbol::get_backEndBuild | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "IDiaSymbol::get_backEndBuild (metodo)"
ms.assetid: 423af497-9294-438e-92b4-456c6f56dc56
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# IDiaSymbol::get_backEndBuild
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Recupera il numero di build di back-end del compilatore.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT get_backEndBuild (   
   DWORD* pRetVal  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `pRetVal`  
 [out] Restituisce il numero di build di back-end. Vedere la sezione Osservazioni.  
  
## <a name="return-value"></a>Valore restituito  
 Se ha esito positivo, restituisce `S_OK`; in caso contrario, restituisce `S_FALSE` o un codice di errore.  
  
> [!NOTE]
>  Un valore restituito di `S_FALSE` significa che la proprietà non è disponibile per il simbolo.  
  
## <a name="remarks"></a>Note  
 Un compilatore è in genere composta da due elementi principali: il front-end (parser), che gestisce l'analisi del codice sorgente in un modulo intermedio, e un back-end (Generatore di codice), che converte il formato intermedio in assembly. Non è insolito per il front-end di una versione diversa di back-end.  
  
 Front-end o un numero di versione di back-end è composta da tre parti: \< principali>. \< secondaria>. \< build>, dove \< principali> è il numero di versione principale, \< secondaria> è il numero di versione secondaria, e \< compilare> è il numero di build. Ad esempio, 13.10.3077.  
  
## <a name="requirements"></a>Requisiti  
  
|Requisito|Descrizione|  
|-----------------|-----------------|  
|Intestazione:|DIA2.h|  
|Versione:|DIA SDK versione 7.0|  
  
## <a name="see-also"></a>Vedere anche  
 [IDiaSymbol](../../debugger/debug-interface-access/idiasymbol.md)