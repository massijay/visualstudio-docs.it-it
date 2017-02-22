---
title: "Stato | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ba656fa4-ef9d-4d8c-a3b6-739c3b5d23ae
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Stato
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **Status** di VSPerfCmd.exe visualizza informazioni sullo stato del profiler e sui processi attualmente profilati.  
  
 **Status** deve essere l'unica opzione specificata nella riga di comando.  È necessario inizializzare il profiler con l'opzione **Start** di VSPerfCmd.exe prima di visualizzare qualsiasi stato.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /Status  
```  
  
#### Parametri  
 Nessuno  
  
## Note  
 L'opzione **Status** visualizza le informazioni di stato seguenti per il profiler.  
  
 **Output File Name**  
 Percorso e nome del file di dati del profiler corrente.  
  
 **Collection Mode**  
 SAMPLE o TRACE  
  
 **Maximum Processes**  
 Numero massimo di processi di cui è possibile eseguire contemporaneamente il profilo e numero di processi attualmente attivi.  
  
 **Maximum Threads**  
 Numero massimo di thread di cui è possibile eseguire contemporaneamente il profilo.  
  
 **Number of Buffers**  
 Numero di buffer di memoria dedicato alla scrittura di dati di profilo.  
  
 **Size of Buffers**  
 Dimensione del buffer di memoria in byte.  
  
 L'opzione **Status** visualizza le seguenti informazioni di stato per ciascun processo attualmente profilato.  
  
 **Process**  
 Nome del processo profilato.  
  
 **Process ID**  
 Identificatore di sistema del processo.  
  
 **Num Threads**  
 Numero di thread attualmente in esecuzione.  
  
 **Start\/Stop Count**  
 Conteggio del profiler interno principale per il controllo della raccolta dei dati per questo processo.  Il conteggio deve essere uguale a uno per la raccolta di dati.  Il conteggio Start\/Stop può essere modificato dalle API del profiler e dalle opzioni di VSPerfCmd **GlobalOn**, **GlobalOff**, **ProcessOn**, **ProcessOff**, **ThreadOn**e **ThreadOff**.  
  
 **Suspend\/Resume Count**  
 Conteggio del profiler interno secondario per il controllo della raccolta dei dati per questo processo.  Il conteggio deve essere minore di o uguale a zero per la raccolta dei dati.  Il conteggio **Suspend\/Resume** può essere modificato solo dalle API del profiler.  
  
 **Users with access rights to monitor**  
 Elenca i nomi degli utenti che hanno accesso al profiler.  È possibile concedere l'accesso ad altri utenti tramite l'opzione **Admin** di VSPerfCmd.exe  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)