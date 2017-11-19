---
title: Implementazione di un fornitore di porta | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- debugging [Debugging SDK], implementing port suppliers
- port suppliers, implementing
ms.assetid: 6b8579df-58df-4c7f-8112-6015993e8765
caps.latest.revision: "11"
author: gregvanl
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: 3bc985bf9fb55b67b5a332f007abe98c6718fbf2
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="implementing-a-port-supplier"></a>Implementazione di un fornitore di porta
Un fornitore di porta fornisce porte su richiesta al gestore di sessione di debug (SDM). Un fornitore di porta deve essere implementato durante il debug in un computer non DCOM o quando un nuovo dispositivo deve essere supportato. Per consentire il debug di un telefono cellulare, ad esempio, è possibile implementare un fornitore di porta che fornisce porte connettono a telefoni cellulari (ad esempio tramite una connessione di cella o IR) ed elencare i processi e i programmi in esecuzione sul telefono.  
  
 Per debug programmi nei computer basati su Windows (incluso il debug remoto), Visual Studio offre i fornitori di porte per nativo e i processi di Common Language Runtime (CLR), pertanto non è necessario implementare il propria fornitore della porta in questi casi.  
  
## <a name="in-this-section"></a>Contenuto della sezione  
 [Implementazione e registrazione di un fornitore di porte](../../extensibility/debugger/implementing-and-registering-a-port-supplier.md)  
 Viene descritto come il SDM interagisce con il fornitore della porta e le relative porte.  
  
 [Interfacce obbligatorie dei fornitori di porte](../../extensibility/debugger/required-port-supplier-interfaces.md)  
 Vengono illustrate le interfacce che devono essere implementate per ottenere un fornitore di porta.  
  
## <a name="related-sections"></a>Sezioni correlate  
 [Concetti relativi al debugger](../../extensibility/debugger/debugger-concepts.md)  
 Vengono descritti i principali concetti dell'architettura di debug.  
  
## <a name="see-also"></a>Vedere anche  
 [Estendibilità del debugger di Visual Studio](../../extensibility/debugger/visual-studio-debugger-extensibility.md)