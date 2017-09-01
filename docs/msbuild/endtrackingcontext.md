---
title: EndTrackingContext | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- EndTrackingContext
apilocation:
- filetracker.dll
apitype: COM
helpviewer_keywords:
- EndTrackingContext
ms.assetid: c2c5d794-8dc8-4594-8717-70dc79a0e75d
caps.latest.revision: 3
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 11a9cee75f912c5fb31cf4a031644abe9c63d744
ms.openlocfilehash: ed89d29f5c8d2d8f3d87b1007c64344f40f7a1a9
ms.contentlocale: it-it
ms.lasthandoff: 06/03/2017

---
# <a name="endtrackingcontext"></a>EndTrackingContext
Consente di terminare il contesto di verifica corrente.  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT WINAPI EndTrackingContext();  
```  
  
## <a name="return-value"></a>Valore restituito  
 **HRESULT** con il bit **SUCCEEDED** impostato se il contesto di verifica è terminato.  
  
## <a name="requirements"></a>Requisiti  
 **Intestazione:** FileTracker.h  
  
## <a name="see-also"></a>Vedere anche  
 [StartTrackingContext](../msbuild/starttrackingcontext.md)
