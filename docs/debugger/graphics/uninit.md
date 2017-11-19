---
title: UnInit | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cd4fc0b-974a-4e61-9ea8-0aaa1a0c52ea
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 285cfb5a68055612fc7d77022b8f9d1d61067ded
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="uninit"></a>UnInit
Finalizza il file di log di grafica, lo chiude e libera le risorse utilizzate durante la registrazione attiva delle informazioni grafiche da parte dell'applicazione.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
void UnInit();  
```  
  
## <a name="remarks"></a>Note  
 `UnInit` viene automaticamente chiamata quando viene eliminata un'istanza della classe `VsgDbg`. Se l'istanza `VsgDbg` non stava registrando attivamente le informazioni grafiche, questa operazione non ha effetto.  
  
 Una volta chiamata `UnInit` su un'istanza della classe `VsgDbg`, è possibile creare e un nuovo file di log di grafica chiamando `Init` e finalizzarlo chiamando `UnInit`. È possibile ripetere questa procedura tutte le volte che si desidera utilizzare la stessa istanza `VsgDbg` per creare diversi file di log di grafica indipendenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Init](init.md)