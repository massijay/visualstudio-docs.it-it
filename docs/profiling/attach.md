---
title: "Attach | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 79614283-6733-4592-a53a-d428052271ad
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Attach
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **Attach** consente di avviare il profilo dei campioni del processo in esecuzione specificato dall'ID processo \(PID\).  
  
 Per utilizzare l'opzione **Attach**, è necessario specificare il metodo **Sample** nell'opzione Start.  
  
> [!NOTE]
>  Se l'opzione **Start** è stata specificata con l'opzione **Crosssession**, le chiamate a **VSPerfCmd \/Attach** o **VSPerfCmd \/Detach** devono specificare anche **Crosssession**.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /Attach:ProcessID [Options]  
```  
  
#### Parametri  
 `ProcessID`  
 ID del processo in esecuzione.  L'ID di un processo in esecuzione è elencato nella scheda Processi di Gestione attività di Windows.  
  
## Opzioni valide  
 Le opzioni **VSPerfCmd** seguenti possono essere combinate con l'opzione **Attach** in una sola riga di comando.  
  
 **Crosssession**  
 Abilita il profilo di applicazioni in sessioni diverse da quella di accesso.  Obbligatoria se l'opzione **Start** è stata specificata con l'opzione **Crosssession**.  
  
 **Start:** `Method`  
 Inizializza la sessione del profiler dalla riga di comando e imposta il metodo di profilo specificato.  
  
 **TargetCLR**  
 Specifica la versione di Common Language Runtime \(CLR\) di .NET Framework di cui eseguire il profilo quando in una sessione di profilo sono caricate più versioni.  Per impostazione predefinita, viene eseguito il profilo della prima versione caricata.  
  
 **GlobalOn GlobalOff**  
 Riprende \(**GlobalOn**\) o sospende \(**GlobalOff**\) l'esecuzione del profilo, ma non termina la sessione di profilo.  
  
 **ProcessOn:** `PID` **ProcessOff:** `PID`  
 Riprende \(**ProcessOn**\) o sospende \(**ProcessOff**\) l'esecuzione del profilo per il processo specificato.  
  
## Opzioni di intervallo  
 È possibile specificare una delle opzioni di intervallo di campionamento seguenti nella riga di comando Attach.  L'intervallo di campionamento predefinito è 10.000.000 cicli di clock del processore.  
  
 **Timer**\[**:**`Cycles`\]**PF**\[**:**`Events`\]**Sys**\[**:**Events\]**Counter**\[**:**`Name`,`Reload`,`FriendlyName`\]  
 Specifica il numero e il tipo dell'intervallo di campionamento.  
  
-   **Timer**: esegue il campionamento ogni `Cycles` cicli di clock del processore.  Se `Cycles` non è specificato, vengono utilizzati 10.000.000 cicli.  
  
-   **PF**: esegue il campionamento ogni `Events` errori di pagina.  Se `Events` non è specificato, vengono utilizzati 10 errori di pagina.  
  
-   **Sys**: esegue il campionamento ogni chiamate di `Events` al sistema operativo.  Se `Events` non è specificato, vengono utilizzate 10 chiamate di sistema.  
  
-   **Counter**: esegue il campionamento ogni numero `Reload` del contatore delle prestazioni della CPU specificato da `Name`.  Facoltativamente, `FriendlyName` può specificare una stringa da utilizzare come intestazione di colonna nei rapporti del profiler.  
  
## Esempio  
 In questo esempio viene illustrato come connettersi a un'istanza in esecuzione di un'applicazione con ID processo 12345.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Attach:12345  
```  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)