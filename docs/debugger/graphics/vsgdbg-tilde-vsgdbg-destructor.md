---
title: 'VsgDbg:: ~ VsgDbg (distruttore) | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7a3b97fb-d344-4df7-b195-9347d1edfcf7
caps.latest.revision: "4"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: e8d34fc9ac09f944fea44baff3ceea4a121a8009
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="vsgdbgvsgdbg-destructor"></a>VsgDbg::~VsgDbg (distruttore)
Elimina un'istanza di `VsgDbg` classe. Se le informazioni grafiche sono attiva la registrazione, il file di log di grafica viene finalizzato e chiuso e vengono rilasciate le risorse utilizzate durante l'acquisizione di informazioni grafiche attivamente.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
~VsgDbg();  
```  
  
## <a name="see-also"></a>Vedere anche  
 [VsgDbg::VsgDbg (Costruttore)](vsgdbg-vsgdbg-constructor.md)