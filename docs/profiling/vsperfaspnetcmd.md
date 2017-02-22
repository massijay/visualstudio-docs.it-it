---
title: "VSPerfASPNetCmd | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti di profilatura, VSPerfASPNETCmd"
  - "VSPerfASPNETCmd"
ms.assetid: f9e9f895-57bb-41e8-8bd1-cdaa738ec220
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# VSPerfASPNetCmd
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Lo strumento da riga di comando **VSPerfASPNetCmd.exe** consente di profilare siti Web ASP.NET senza richiedere l'impostazione di variabili di ambiente o il riavvio del computer.  Utilizzare **VSPerfASPNetCmd.exe** anziché [VSPerfCmd](../profiling/vsperfcmd.md) quando si profilano siti Web ASP.NET e non è necessaria la funzionalità aggiuntiva fornita da **VSPerCmd**.  Per ulteriori informazioni su **VSPerfASPNetCmd**, vedere [Profilatura rapida di sito Web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md).  **VSPerfASPNetCmd** è lo strumento da riga di comando preferito da utilizzare con il profiler autonomo per profilare un sito Web ASP.NET.  
  
## Sintassi  
 **vsperfaspnetcmd** \[\/*Options*\] *Website*  
  
## Opzioni  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**\/Sample** o   **\/s**|Profila il sito Web utilizzando il metodo di campionamento.  **\/Sample** è il metodo predefinito. \/Sample non può essere utilizzata con l'opzione **\/Trace**.|  
|**\/Trace** o   **\/t**|Profila il sito Web utilizzando il metodo di strumentazione. \/Trace non può essere utilizzata con l'opzione **\/Sample**.|  
|**\/Memory**\[**:**`Type`\]                  o   **\/m**\[**:**{**a**&#124;**l**}\]|Profila l'allocazione della memoria e facoltativamente le durate degli oggetti \(Garbage Collection\).  **\/Memory** può essere utilizzata con il metodo di campionamento o di strumentazione.<br /><br /> *Type* può corrispondere a uno dei seguenti nomi:<br /><br /> -   **allocation** \(o **a**\) raccoglie unicamente dati sull'allocazione di memoria.<br />-   **lifetime** \(o **l**\) raccoglie dati sull'allocazione di memoria e sulla durata degli oggetti.<br /><br /> Il valore `Type` predefinito è **allocation**.|  
|**\/Tip** o   **\/i**|Aggiunge informazioni dettagliate sulle richieste ASP.NET e sulle chiamate ADO.NET ai dati di profilatura.  **\/Tip** può essere utilizzata con il metodo di campionamento o strumentazione e con l'opzione **\/Memory**.|  
|**\/Output:** `File`  o   **\/o:**`File`|Consente di specificare il percorso e il nome del file di dati di profilatura \(con estensione vsp\).|  
|**\/NoWait** o   **\/n**|Restituisce immediatamente il prompt dei comandi in modo che sia possibile utilizzare comandi aggiuntivi nella finestra del prompt dei comandi.  È necessario digitare **VSPerfASPNETCmd \/Shutdown** su una riga di comando separata per disattivare la profilatura.|  
|**\/PackSymbols**\[:{**on**&#124;**off**}o   **\/p**\[:{**on**&#124;**off**}|Incorpora simboli, ovvero nomi di funzione e di parametro e così via, in file dei dati di profilatura \(con estensione vsp\).|  
|**\/Shutdown:** `Website`o   **\/d:**`Website`|Disattiva la profilatura.  Utilizzare come unica opzione su una riga di comando dopo avere utilizzato l'opzione **\/NoWait** per avviare la profilatura o se il profiler viene terminato in modo imprevisto.  Specificare lo stesso URL utilizzato nel comando **VSPerfASPNETCmd** originale.|  
|`Website`|L'URL del sito Web da profilare.|  
  
## Vedere anche  
 [Profilatura rapida di sito Web con VSPerfASPNETCmd](../profiling/rapid-web-site-profiling-with-vsperfaspnetcmd.md)   
 [Profilatura di applicazioni Web ASP.NET](../profiling/command-line-profiling-of-aspnet-web-applications.md)