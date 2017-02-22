---
title: "Inizia | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b85d0fe9-f67a-4b7c-8d48-7eecf3f2dfe9
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Inizia
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'opzione **Start** è un'opzione di VSPerfCmd.exe che consente di inizializzare il profiler al metodo di profilo specificato.  
  
## Sintassi  
  
```  
VSPerfCmd.exe /Start:Method /Output:FileName [Options]  
```  
  
#### Parametri  
 `Method`  
 Deve essere una delle seguenti parole chiave:  
  
-   **TRACE**: specifica il metodo di strumentazione.  
  
-   **SAMPLE**: specifica il metodo di campionamento.  
  
-   **COVERAGE**: specifica il code coverage.  
  
-   **CONCURRENCY** \- Specifica il metodo di conflitto di risorse.  
  
## Opzioni obbligatorie  
 È necessario specificare l'opzione **Output** quando nella riga di comando viene specificato **Start**.  
  
 **Output:** `filename`  
 Specifica il nome del file di output.  
  
## Opzioni esclusive  
 È possibile utilizzare le opzioni seguenti solo con l'opzione **Start** nella riga di comando.  
  
 **CrossSession**&#124;**CS**  
 Abilita analisi tra processi incrociati.  Sono supportati entrambi i nomi **CrossSession** e **CS**.  
  
 **User:**\[`domain\`\]`username`  
 Consente ai client di accedere al monitor con l'account specificato.  
  
 **WinCounter:** `Path` \[**Automark**:`n`\]  
 **WinCounter** specifica un contatore delle prestazioni di Windows da includere come contrassegno nel file di dati di profilo.  **AutoMark** specifica in millisecondi l'intervallo di tempo fra le raccolte del file di dati.  
  
## Opzioni non valide  
 Non è possibile utilizzare le opzioni seguenti con l'opzione **Start** nella riga di comando.  
  
 **Status**  
 **Status** viene applicato ai processi profilati.  Questa opzione elenca i processi e i thread insieme al relativo stato di analisi corrente \(On\/Off\).  Ad esempio, se un processo è arrestato, **Status** non indica questo stato nel rapporto.  **Status** mostra che il processo è profilato o non profilato.  
  
 **Shutdown**\[**:**`Timeout`\]  
 Disattiva il profiler.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato come utilizzare l'opzione **Start** di VSPerfCmd.exe per inizializzare il profiler.  
  
```  
VSPerfCmd.exe /Start:Sample /Output:TestApp.exe.vsp  
VSPerfCmd.exe /Launch:TestApp.exe  
```  
  
## Vedere anche  
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [Profilatura di applicazioni autonome](../profiling/command-line-profiling-of-stand-alone-applications.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)   
 [Profilatura di servizi](../profiling/command-line-profiling-of-services.md)