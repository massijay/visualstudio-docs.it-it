---
title: "Procedura: Scegliere un metodo di raccolta | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "strumenti per le prestazioni, scelta del metodo di raccolta"
  - "strumenti per la profilatura, scelta del metodo di raccolta"
  - "metodi di raccolta di prestazioni"
ms.assetid: c87cfd3a-0fc7-49ae-9c05-d8480891cc63
caps.latest.revision: 34
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 34
---
# Procedura: Scegliere un metodo di raccolta
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Negli strumenti di profilatura di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] sono supportati tre metodi di raccolta dei dati di prestazioni, ovvero il campionamento, la strumentazione e la concorrenza.  Il metodo di campionamento o di strumentazione può essere utilizzato anche per raccogliere l'allocazione della memoria .NET e i dati di durata.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
 È possibile utilizzare la proprietà **Metodo** della sessione di prestazioni per specificare il metodo di raccolta più adeguato per un'applicazione.  È possibile impostare il metodo di raccolta da Creazione guidata sessione di prestazioni, Esplora prestazioni o dalle pagine delle proprietà di una sessione di prestazioni.  Se si utilizzano gli strumenti della riga di comando, vedere [Profilatura dalla riga di comando](../profiling/using-the-profiling-tools-from-the-command-line.md) per ulteriori informazioni.  
  
## Creazione guidata sessione di prestazioni  
  
#### Per selezionare un metodo di raccolta tramite Creazione guidata sessione di prestazioni  
  
-   Nella prima pagina della procedura guidata, selezionare una delle opzioni seguenti:  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**Campionamento CPU**|Consente di raccogliere le statistiche dell'applicazione utili per l'analisi iniziale e per l'approfondimento dei problemi relativi all'utilizzo della CPU.|  
|**Strumentazione**|Consente di raccogliere i dati di intervallo dettagliati utili per l'analisi mirata e per l'approfondimento dei problemi relativi alle prestazioni di input\/output.|  
|**Allocazione della memoria .NET**|Consente di raccogliere i dati dell'allocazione della memoria [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] mediante il metodo del profilo di campionamento.|  
|**Concorrenza**|Raccoglie dati numerici sui conflitti di risorse.|  
  
## Esplora prestazioni  
  
#### Per selezionare un metodo di raccolta utilizzando Esplora prestazioni  
  
1.  Sulla barra degli strumenti di **Esplora prestazioni**, fare clic sulla freccia accanto all'elenco a discesa **Metodo**.  
  
2.  Scegliere il metodo di raccolta che si preferisce.  
  
## Pagine delle proprietà della sessione di prestazioni  
  
#### Per selezionare il metodo di campionamento o di strumentazione tramite le proprietà della sessione di prestazioni  
  
1.  Selezionare la sessione di prestazioni in **Esplora prestazioni**.  
  
     Il nome di un file di sessione di prestazioni ha come estensione .psess.  
  
2.  Fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi scegliere **Proprietà**.  
  
3.  Da **Pagine delle proprietà** scegliere **Generale**.  
  
4.  Scegliere il metodo di raccolta che si preferisce.  
  
    -   Per informazioni sulle altre opzioni disponibili quando si raccolgono i dati di campionamento, vedere [Raccolta di statistiche sulle prestazioni tramite il campionamento](../profiling/collecting-performance-statistics-by-using-sampling.md)  
  
    -   Per informazioni sulle altre opzioni disponibili quando si raccolgono i dati di campionamento, vedere [Raccolta di dati di intervallo dettagliati tramite la strumentazione](../profiling/collecting-detailed-timing-data-by-using-instrumentation.md).  
  
#### Per selezionare la raccolta dati di memoria .NET tramite le proprietà della sessione di prestazioni  
  
1.  Selezionare la sessione di prestazioni in **Esplora prestazioni**.  
  
     Il nome di un file di sessione di prestazioni ha come estensione .psess.  
  
2.  Fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi scegliere **Proprietà**.  
  
3.  Da **Pagine delle proprietà** scegliere **Generale**.  
  
4.  Scegliere **Campionamento** o **Strumentazione**.  
  
5.  Fare clic su **Raccogliere le informazioni sull'allocazione dell'oggetto .NET** per raccogliere le dimensioni e il numero delle allocazioni degli oggetti [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].  
  
6.  \(Facoltativo\) Fare clic su **Raccogliere anche le informazioni sulla durata dell'oggetto .NET** per raccogliere dati sulle generazioni di Garbage Collection in cui è stata recuperata la memoria dell'oggetto.  
  
     Per informazioni sulle altre opzioni disponibili quando si raccolgono i dati di memoria .NET, vedere [Raccolta di dati di durata e allocazione di memoria .NET](../profiling/collecting-dotnet-memory-allocation-and-lifetime-data.md).  
  
#### Per selezionare la raccolta dati sulla concorrenza tramite le proprietà della sessione di prestazioni  
  
1.  In **Esplora prestazioni** fare clic con il pulsante destro del mouse sulla sessione di prestazioni e quindi scegliere **Proprietà**.  
  
2.  Da **Pagine delle proprietà** scegliere **Generale**.  
  
3.  Scegliere **Concorrenza**.  
  
## Vedere anche  
 [Configurazione di sessioni di prestazioni](../profiling/configuring-performance-sessions.md)   
 [Informazioni sui valori dei dati di campionamento](../profiling/understanding-sampling-data-values.md)   
 [Proprietà della sessione di prestazioni](../profiling/performance-session-properties.md)