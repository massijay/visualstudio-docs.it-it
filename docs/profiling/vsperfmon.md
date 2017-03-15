---
title: "VSPerfMon | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "VSPerfMon (strumento)"
  - "riga di comando, strumenti"
  - "strumenti da riga di comando, VSPerfMon (strumento)"
  - "dati [Visual Studio ALM], VSPerfMon (strumento)"
  - "dati sulle prestazioni, VSPerfMon (strumento)"
  - "strumenti per le prestazioni, VSPerfMon"
  - "strumenti per la profilatura,VSPerfCmd"
ms.assetid: 37052afb-7a58-441f-bb17-f1587cc57068
caps.latest.revision: 30
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 30
---
# VSPerfMon
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile utilizzare lo strumento VSPerfMon per raccogliere dati relativi alle prestazioni per un'applicazione. Questo strumento viene in genere avviato da VSPerfCmd.exe.  VSPerfMon consente di visualizzare informazioni aggiuntive sulla connessione o la disconnessione dei processi che non sono disponibili utilizzando lo strumento VSPerfCmd.  Per visualizzare le informazioni, avviare VSPerfMon in una finestra separata.  Per richiamare lo strumento in questione, utilizzare la sintassi riportata di seguito.  
  
```  
VSPerfMon [/U] </TRACE [/COUNTER:cfg] | /SAMPLE | /COVERAGE> /CROSSSESSION /OUTPUT <file name> [/WINCOUNTER:cfg] [/USER [DOMAIN\]username]  
```  
  
 Nella tabella riportata di seguito sono descritte le opzioni dello strumento VSPerfMon.  
  
|Opzioni|Descrizione|  
|-------------|-----------------|  
|**U**|L'output della console reindirizzato viene scritto come Unicode.  Deve essere la prima opzione specificata.|  
|**OUTPUT:** `<` *file name* `>`|Reindirizza l'output al nome file specificato.|  
|**TRACE**|Avvia Performance Monitor per la profilatura mediante strumentazione.|  
|**SAMPLE**|Avvia Performance Monitor per la profilatura mediante campionamento.|  
|**COVERAGE**|Avvia Performance Monitor per la raccolta del code coverage.|  
|**CONCURRENCY**|Avvia Performance Monitor per la profilatura dei conflitti delle risorse.|  
|**USER:** `[` *domain* `\]` *username*|Consente ai client di accedere a Performance Monitor con l'account specificato.|  
|**CROSSSESSION**|Attiva la profilatura tra sessioni.|  
|**COUNTER** `:cfg`|Quando si utilizza il metodo di profilatura strumentazione \(TRACE\), specifica un contatore CPU di cui raccogliere di dati per ogni punto di strumentazione.  È possibile raccogliere i dati di più contatori specificando più opzioni Counter.<br /><br /> Utilizzare la seguente sintassi per specificare il contatore delle prestazioni \(*cfg*\):<br /><br /> CounterName\[**,**Reload\[,FriendlyName\]\]<br /><br /> -   CounterName è il nome di un contatore restituito dal comando VSPerfCmd \/QueryCounters.<br />-   Il ricaricamento è l'intervallo di campionamento degli eventi del contatore.  Non utilizzare *Reload* con il metodo di strumentazione.<br />-   Se specificato, FriendlyName sostituisce CounterName nei nomi delle colonne dei rapporti degli strumenti di profilatura.|  
|**WINCOUNTER** `:path`|Specifica un contatore delle prestazioni di Windows da includere con i dati di contrassegno.  `path` è una stringa del contatore delle prestazioni di Windows nel percorso del contatore in formato PDH.  Di seguito è riportato un esempio.<br /><br /> \\Processor \(0\)\\% Processor Time<br /><br /> \\System\\Context Switches\/sec|  
|**AUTOMARK** `:n`|Specifica l'intervallo di tempo \(in millisecondi\) che intercorre tra contrassegni automatici quando si utilizza \/WINCOUNTER.  Arrotondamento al valore 500 ms più vicino.<br /><br /> Utilizzare 0 per disattivare i contrassegni automatici. \(impostazione predefinita\=500ms se non specificato\)|  
  
## Vedere anche  
 [VSInstr](../profiling/vsinstr.md)   
 [VSPerfCmd](../profiling/vsperfcmd.md)   
 [VSPerfReport](../profiling/vsperfreport.md)   
 [Visualizzazioni dei report degli strumenti per la profilatura](../profiling/performance-report-views.md)