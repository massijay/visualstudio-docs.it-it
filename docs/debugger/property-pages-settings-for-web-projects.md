---
title: "Impostazioni delle pagine delle propriet&#224; per i progetti Web | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
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
helpviewer_keywords: 
  - "compilazioni di debug, impostazioni di progetto"
  - "configurazioni di debug, Web (progetti)"
  - "debug [Visual Studio], applicazioni Web"
  - "debug di applicazioni Web, impostazioni di progetto"
  - "progetto (impostazioni) [Visual Studio], configurazioni di debug"
  - "progetti [Visual Studio], configurazioni di debug"
ms.assetid: 8ec5160a-6408-4f47-8d41-f0e20e79a3b9
caps.latest.revision: 11
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 11
---
# Impostazioni delle pagine delle propriet&#224; per i progetti Web
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile modificare le impostazioni delle proprietà per la configurazione di debug di un sito Web nella finestra di dialogo **Pagine delle proprietà**, come descritto in [Procedura: impostare le configurazioni di debug e rilascio](../debugger/how-to-set-debug-and-release-configurations.md).  Nelle tabelle riportate di seguito sono indicate le sezioni della finestra di dialogo **Pagine delle proprietà** in cui sono disponibili le impostazioni correlate al debugger.  
  
### Cartella Proprietà di configurazione \(categoria Opzioni di avvio\)  
  
|**Impostazione**|**Descrizione**|  
|----------------------|---------------------|  
|**Azione di avvio**|Intestazione sotto la quale sono raggruppate le opzioni correlate all'avvio dell'applicazione.|  
|**Usa pagina corrente**|Specifica la pagina corrente come punto di avvio per il debug.|  
|**Pagina specifica**|Specifica la pagina Web da cui iniziare la procedura di debug.|  
|**Avvia programma esterno**|Specifica il comando per l'avvio del programma da sottoporre a debug.|  
|**Argomenti della riga di comando**|Specifica gli argomenti relativi al comando riportato sopra.|  
|**Cartella di lavoro**|Specifica la cartella di lavoro del programma sottoposto a debug.  In [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] la cartella di lavoro è la cartella dalla quale viene avviata l'applicazione, che per impostazione predefinita è \\bin\\debug.|  
|**Avvia URL**|Specifica la posizione dell'applicazione Web da sottoporre a debug.|  
|**Non aprire alcuna pagina.  Attendi richiesta da un'applicazione esterna.**|Specifica di attendere una richiesta da un'applicazione esterna.  Questa opzione non avvia Internet Explorer né altre applicazioni.  Esegue semplicemente le operazioni di preparazione necessarie per eseguire il debug su richiesta di un'applicazione.|  
|**Server**|Intestazione sotto la quale sono raggruppate le opzioni correlate al server da utilizzare.|  
|**Usa server Web predefinito**|Specifica di utilizzare il server Web predefinito.|  
|**Usa server personalizzato**|Consente di immettere l'URL di base da utilizzare come server.|  
|**Debugger**|Intestazione sotto la quale sono raggruppate le opzioni correlate al tipo di debug da eseguire.|  
|**Debug ASP.NET**|Attiva il debug di pagine ASP scritte per la piattaforma di sviluppo [!INCLUDE[vstecasp](../code-quality/includes/vstecasp_md.md)].  È necessario specificare un URL in **Avvia URL**.|  
|**Debug codice nativo**|Consente di eseguire il debug delle chiamate al codice Win32 nativo \(non gestito\) dall'applicazione gestita in uso.|  
|**Debug SQL Server**|Consente di eseguire il debug di oggetti di database di SQL Server.|  
|**Debug Silverlight**|Consente di eseguire il debug dei componenti di Silverlight.|  
  
## Vedere anche  
 [Impostazioni di debug e preparazione](../debugger/debugger-settings-and-preparation.md)