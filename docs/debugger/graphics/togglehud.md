---
title: ToggleHUD | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7261e01d-3c72-46ce-9fb3-5f33b2ddb901
caps.latest.revision: "5"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 5bf1e27b9385257203653f3bff5241f6c3875373
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="togglehud"></a>ToggleHUD
Attiva o disattiva la diagnostica della grafica *HUD* o disattivazione di sovrapposizione (Head-Up Display).  
  
## <a name="syntax"></a>Sintassi  
  
```C++  
void ToggleHUD();  
```  
  
## <a name="remarks"></a>Note  
 La diagnostica della grafica HUD viene visualizzata nell'angolo superiore sinistro dell'applicazione in esecuzione nella diagnostica della grafica. Visualizza informazioni di runtime sull'applicazione e sull'acquisizione delle informazioni grafiche e i messaggi aggiunti chiamando il [AddMessage](addmessage.md) funzione membro.  
  
 Per attivare o disattivare l'HUD, non è necessario essere attivamente acquisizione di informazioni grafiche, vale a dire, può essere modificato tramite un'istanza del `VsgDbg` (classe), ma la [Init](init.md) funzione membro non deve essere chiamato per primo.