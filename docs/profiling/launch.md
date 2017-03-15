---
title: "Avvio | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f81bde5c-3394-4b79-a315-c2f6491689b3
caps.latest.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 13
---
# Avvio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **Launch** avvia il profiler mediante il metodo di campionamento, inoltre avvia l'applicazione specificata.  
  
 Per utilizzare l'opzione **Launch** è necessario specificare il metodo **Sample** nell'opzione **Start**.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /Launch:AppName [Options]  
```  
  
#### Parametri  
 `AppName`  
 Nome dell'applicazione da avviare.  I percorsi completi e parziali dalla directory corrente sono supportati.  
  
## Opzioni valide  
 Le opzioni VSPerfCmd seguenti possono essere combinate con l'opzione **Launch** su una sola riga di comando.  
  
 **Start:** `Method`  
 Inizializza la sessione del profiler dalla riga di comando e imposta il metodo di profilo specificato.  
  
 **GlobalOn**e **GlobalOff**  
 Riprende \(**GlobalOn**\) o sospende \(**GlobalOff**\) l'esecuzione del profilo, ma non termina la sessione di profilo.  
  
 **ProcessOn:** `PID` e **ProcessOff**:`PID`  
 Riprende \(**ProcessOn**\) o sospende \(**ProcessOff**\) l'esecuzione del profilo per il processo specificato.  
  
 **TargetCLR**  
 Specifica la versione di Common Language Runtime \(CLR\) di .NET Framework di cui eseguire il profilo quando in una sessione di profilo sono caricate più versioni.  Per impostazione predefinita, viene eseguito il profilo della prima versione caricata.  
  
## Opzioni esclusive  
 Le opzioni seguenti possono essere utilizzate solo con l'opzione **Launch**.  
  
 **Console**  
 Avvia l'applicazione della riga di comando specificata in una nuova finestra.  
  
 **Args:** `ArgList`  
 Specifica l'elenco di argomenti da passare all'applicazione.  
  
 **LineOff**  
 Disabilita la raccolta dei dati di profilo a livello di riga.  
  
## Opzioni di campionamento  
 È possibile specificare una delle seguenti opzioni di intervallo di campionamento nella riga di comando **Launch**.  L'intervallo di campionamento predefinito è 10.000.000 cicli di clock del processore.  
  
 **Timer**\[**:**`Cycles`\]**PF**\[**:**`Events`\]**Sys**\[**:**`Events`\]**Counter**\[**:**`Name`,`Reload`,`FriendlyName`\]**GC**\[:**allocation**&#124;**lifetime**\]  
 Specifica il tipo e il numero dell'intervallo di campionamento.  
  
-   **Timer**: esegue il campionamento ogni `Cycles` cicli di clock del processore non interrotti.  Se `Cycles` non è specificato, vengono utilizzati 10.000.000 cicli.  
  
-   **PF**: esegue il campionamento ogni `Events` errori di pagina.  Se `Events` non è specificato, vengono utilizzati 10 errori di pagina.  
  
-   **Sys**: esegue il campionamento ogni chiamate di `Events` al sistema operativo.  Se `Events` non è specificato, vengono utilizzate 10 chiamate di sistema.  
  
-   **Counter**: esegue il campionamento ogni numero `Reload` del contatore delle prestazioni della CPU specificato da `Name`.  Facoltativamente, `FriendlyName` può specificare una stringa da utilizzare come intestazione di colonna nei rapporti del profiler.  
  
-   **GC**: raccoglie i dati di memoria .NET.  Per impostazione predefinita \(**allocation**\), i dati vengono raccolti a ogni evento di allocazione della memoria.  Quando viene specificato il parametro **lifetime**, i dati vengono raccolti anche a ogni evento di Garbage Collection.  
  
## Esempio  
 In questo esempio viene illustrato l'utilizzo di **Launch** per avviare un'applicazione.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)