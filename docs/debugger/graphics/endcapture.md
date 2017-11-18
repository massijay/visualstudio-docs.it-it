---
title: EndCapture | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 06084c3b-e065-49b6-968e-d578762fb871
caps.latest.revision: "6"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 0f587b10fea4b593234be2a536baa13cf7b3db66
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="endcapture"></a>EndCapture
Termina un intervallo di acquisizione avviato con `BeginCapture`.  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
void EndCapture();  
```  
  
## <a name="remarks"></a>Note  
 Un intervallo di acquisizione in genere estende un subset di un singolo frame, come ad esempio quando si desidera acquisire informazioni grafiche solo su un determinato tipo di chiamata di disegno. Se l'intervallo di acquisizione estende una chiamata da presentare, vengono acquisiti due frame di informazioni grafiche. Il primo frame estende l'intervallo tra la chiamata a `BeginCapture` e la chiamata da presentare; il secondo frame estende l'intervallo tra il primo evento Direct3D dopo la chiamata da presentare e la chiamata a `EndCapture`.  
  
 Per acquisire un intervallo, è necessario preparare l'app per acquisire e registrare le informazioni grafiche, vale a dire, è necessario chiamare [Init](init.md) tramite un'istanza del `VsgDbg` classe prima di chiamare `BeginCapture` o `EndCapture`.  
  
## <a name="see-also"></a>Vedere anche  
 [BeginCapture](begincapture.md)   
 [CaptureCurrentFrame](capturecurrentframe.md)