---
title: IDebugCoreServer2::GetMachineUtilities_V7 | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
helpviewer_keywords:
- IDebugCoreServer2::GetMachineUtilities_V7
ms.assetid: 64c1f08f-853b-4498-9810-29791581ef2f
caps.latest.revision: 17
ms.author: gregvanl
manager: ghogen
translation.priority.mt:
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
translationtype: Machine Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 8cec5befece6b3415a903ed84d8d31cbe3988ee8
ms.lasthandoff: 02/22/2017

---
# <a name="idebugcoreserver2getmachineutilitiesv7"></a>IDebugCoreServer2::GetMachineUtilities_V7
Questo metodo ottiene l'utilità di computer per un server.  
  
> [!NOTE]
>  Questo metodo è obsoleto: non utilizzare ([!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)] restituisce sempre `E_NOTIMPL` se questo metodo viene chiamato). Viene mantenuta per motivi storici.  
  
## <a name="syntax"></a>Sintassi  
  
```cpp#  
HRESULT GetMachineUtilities_V7(  
   IDebugMDMUtil2_V7** ppUtil  
);  
```  
  
```c#  
int GetMachineUtilities_V7(  
   out IDebugMDMUtil2_V7 ppUtil  
);  
```  
  
#### <a name="parameters"></a>Parametri  
 `ppUtil`  
 [out] Restituisce un `IDebugMDMUtil2_V7` interfaccia che rappresenta le informazioni di utilità macchina.  
  
## <a name="return-value"></a>Valore restituito  
 Restituisce sempre `E_NOTIMPL`, che indica che il metodo non è implementato.  
  
## <a name="remarks"></a>Note  
 [!INCLUDE[vsprvs](../../../code-quality/includes/vsprvs_md.md)]Restituisce sempre `E_NOTIMPL` se questo metodo viene chiamato.  
  
## <a name="see-also"></a>Vedere anche  
 [IDebugCoreServer2](../../../extensibility/debugger/reference/idebugcoreserver2.md)
