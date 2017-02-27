---
title: "Contrassegno | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1d72cef3-bb09-4bbb-8864-6ea0ab623ff9
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Contrassegno
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **Mark** di VSPerfCmd.exe consente di inserire le informazioni specificate nel file dei dati di profilo.  Mark può essere elencato in un rapporto VSPerfReport a parte o nella visualizzazione Rapporto Mark dell'interfaccia utente del profiler.  **Mark** può essere utilizzato per specificare i punti iniziale e finale nei filtri di rapporto e visualizzazione.  
  
 **Mark** deve essere l'unica opzione specificata nella riga di comando.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /Mark:MarkID,[MarkName]   
```  
  
#### Parametri  
 `MarkID`  
 Intero definito dall'utente elencato come MarkID nei rapporti e nelle visualizzazioni del profiler.  `MarkID` non deve essere necessariamente univoco.  
  
 `MarkName`  
 \(Facoltativo\) Stringa definita dall'utente elencata come Nome contrassegno nei rapporti e nelle visualizzazioni del profiler.  Se non viene specificato `MarkName`, il campo Nome contrassegno dell'elenco relativo è vuoto.  Racchiudere tra virgolette doppie le stringhe che contengono spazi o barre \("\/"\).  
  
## Esempio  
 In questo esempio viene inserito un contrassegno con ID 123 e un nome "TestMark".  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
VSPerfCmd.exe /Mark:123,TestMark  
```  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)