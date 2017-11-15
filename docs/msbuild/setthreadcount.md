---
title: SetThreadCount | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: SetThreadCount
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: SetThreadCount
ms.assetid: 335335a5-8ca0-4e18-95f5-62aa6a691386
caps.latest.revision: "4"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 7c25dbb399a3be2af9b181c7ccbf495cc03bec19
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="setthreadcount"></a>SetThreadCount
Imposta il conteggio dei thread globale e assegna tale conteggio al thread corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT WINAPI SetThreadCount(int threadCount);  
```  
  
#### <a name="parameters"></a>Parametri  
 [in] `threadCount`  
 Numero di thread da usare.  
  
## <a name="return-value"></a>Valore restituito  
 **HRESULT** con il bit **SUCCEEDED** impostato se il conteggio thread è stato aggiornato.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** FileTracker.h