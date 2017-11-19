---
title: Metodo SetWefProcessId | Documenti Microsoft
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
ms.assetid: 404eec23-a67e-4f5b-b27d-86651f08be03
caps.latest.revision: "8"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0821c799a4d6385997704724c00a2aff4669eb17
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="setwefprocessid-method"></a>Metodo SetWefProcessId
  Fornisce l'identificatore di processo che verrà eseguito il contenuto Web estensioni Framework (WEF).  
  
## <a name="syntax"></a>Sintassi  
  
```  
HRESULT SetWefProcessId(  
    [in] DWORD dwProcessId  
);  
```  
  
#### <a name="parameters"></a>Parametri  
  
|Parametro|Descrizione|  
|---------------|-----------------|  
|*cui dwProcessId*|L'identificatore di processo che verrà utilizzato per eseguire il contenuto WEF.|  
  
## <a name="return-value"></a>Valore restituito  
 Valore HRESULT che indica se il metodo è stato completato correttamente.  
  
## <a name="remarks"></a>Note  
 Questo metodo deve essere chiamato dopo aver creato il processo del contenuto WEF ma prima dell'esecuzione di qualsiasi contenuto WEF.  
  
 Se si desidera l'ambiente di sviluppo per collegare un debugger al processo WEF contenuto, l'ambiente è necessario eseguire questa operazione nell'implementazione di questo metodo.  
  
  