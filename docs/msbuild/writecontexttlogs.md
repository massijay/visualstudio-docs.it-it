---
title: WriteContextTLogs | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname: WriteContextTLogs
apilocation: filetracker.dll
apitype: COM
helpviewer_keywords: WriteContextTLogs
ms.assetid: ffc6c7be-3f22-4624-9ffc-0122fe72b6ec
caps.latest.revision: "5"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: 30c3c96a0999fe65c6fe0fa95163feaf526adfbf
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="writecontexttlogs"></a>WriteContextTLogs
Scrive i file di log per il contesto corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp  
HRESULT WINAPI WriteContextTLogs(LPCTSTR intermediateDirectory, LPCTSTR tlogRootName);  
```  
  
#### <a name="parameters"></a>Parametri  
 [in] `intermediateDirectory`  
 Directory in cui archiviare il log di rilevamento.  
  
 [in] `tlogRootName`  
 Nome radice del nome file di log.  
  
## <a name="return-value"></a>Valore restituito  
 **HRESULT** con il bit **SUCCEEDED** impostato se il contesto di rilevamento è stato creato.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** FileTracker.h  
  
## <a name="see-also"></a>Vedere anche  
 [WriteAllTLogs](../msbuild/writealltlogs.md)