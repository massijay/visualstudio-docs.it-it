---
title: "Come è possibile stabilire se i puntatori danneggino un indirizzo di memoria? | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-debug
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- CSharp
- VB
- FSharp
- C++
helpviewer_keywords:
- addresses, pointers corrupting memory address
- memory, corruption
- pointers, corrupting memory addresses
- memory address corruption by pointers
- debugging [C++], memory corruption
- corrupted memory address
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: "19"
author: mikejo5000
ms.author: mikejo
manager: ghogen
ms.openlocfilehash: 863acbf45268330e106360dd7778acab94b670de
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="how-can-i-find-out-if-my-pointers-corrupt-a-memory-address"></a>Come è possibile stabilire se i puntatori danneggino un indirizzo di memoria?
## <a name="problem-description"></a>Descrizione del problema  
 È probabile che uno dei puntatori stia danneggiando la memoria all'indirizzo 0x00408000. Come è possibile appurare cosa sta accadendo in tale posizione?  
  
## <a name="solution"></a>Soluzione  
  
#### <a name="check-for-heap-corruption"></a>Controllare l'integrità della memoria heap  
  
-   Il danneggiamento della memoria è principalmente causato dai problemi che si verificano nella memoria heap. Provare a utilizzare l'utilità per i flag globali (gflags.exe) o pageheap.exe. Vedere [http://support.microsoft.com/default.aspx?scid=kb;en-us;286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).  
  
#### <a name="to-find-where-the-memory-address-is-modified"></a>Per individuare i punti in cui l'indirizzo di memoria è modificato  
  
1.  Impostare un punto di interruzione di dati all'indirizzo 0x00408000. Vedere [impostare un punto di interruzione di modifica (solo C++ nativo) dati](../debugger/using-breakpoints.md#BKMK_set_a_data_breakpoint_native_cplusplus_only).  
  
2.  Quando si raggiunge il punto di interruzione, utilizzare il **memoria** consente di visualizzare memoria contenuto a partire dall'indirizzo 0x00408000. Per ulteriori informazioni, vedere [memoria Windows](../debugger/memory-windows.md).  
  
## <a name="see-also"></a>Vedere anche  
 [Domande frequenti sul codice nativo debug](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)