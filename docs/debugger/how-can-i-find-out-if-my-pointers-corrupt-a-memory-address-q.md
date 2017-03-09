---
title: "Come &#232; possibile stabilire se i puntatori danneggino un indirizzo di memoria? | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "FSharp"
  - "VB"
  - "CSharp"
  - "C++"
  - "C++"
helpviewer_keywords: 
  - "indirizzi, puntatori che danneggiano un indirizzo di memoria"
  - "indirizzi di memoria danneggiati"
  - "debug [C++], danneggiamento della memoria"
  - "danneggiamento di indirizzi di memoria per mezzo di puntatori"
  - "memoria, danneggiamento"
  - "puntatori, danneggiamento di indirizzi di memoria"
ms.assetid: a147c939-4fb1-415c-8410-cf303781e9e8
caps.latest.revision: 19
caps.handback.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Come &#232; possibile stabilire se i puntatori danneggino un indirizzo di memoria?
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

## Descrizione del problema  
 È probabile che uno dei puntatori stia danneggiando la memoria all'indirizzo 0x00408000.  Come è possibile appurare cosa sta accadendo in tale posizione?  
  
## Soluzione  
  
#### Controllare l'integrità della memoria heap  
  
-   Il danneggiamento della memoria è principalmente causato dai problemi che si verificano nella memoria heap.  Provare a utilizzare l'utilità per i flag globali \(gflags.exe\) o pageheap.exe.  Vedere [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;it\-it;286470](http://support.microsoft.com/default.aspx?scid=kb;en-us;286470).  
  
#### Per individuare i punti in cui l'indirizzo di memoria è modificato  
  
1.  Impostare un punto di interruzione di dati all'indirizzo 0x00408000.  Vedere [Impostare un punto di interruzione di modifica dei dati \(solo C\+\+ nativo\)](../debugger/using-breakpoints.md#BKMK_Set_a_data_change_breakpoint__native_C___only_).  
  
2.  Quando si raggiunge un punto di interruzione, utilizzare la finestra **Memoria** per visualizzare il contenuto della memoria a partire dall'indirizzo 0x00408000.  Per ulteriori informazioni, vedere [Finestra Memoria](../debugger/memory-windows.md).  
  
## Vedere anche  
 [Domande frequenti sul debug del codice nativo](../debugger/debugging-native-code-faqs.md)   
 [Debug del codice nativo](../debugger/debugging-native-code.md)