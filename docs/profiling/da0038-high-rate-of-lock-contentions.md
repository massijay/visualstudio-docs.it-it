---
title: "DA0038: Frequenza elevata di conflitti di blocco | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.38"
  - "vs.performance.rules.DA0038"
  - "vs.performance.DA0038"
ms.assetid: ae0c8b2f-17b2-4f3d-a834-aa2f6371753b
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0038: Frequenza elevata di conflitti di blocco
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|ID regola|DA0038|  
|Categoria|Utilizzo di .NET Framework|  
|Metodo di profilatura|Campionamento<br /><br /> Strumentazione<br /><br /> Memoria .NET|  
|Messaggio|È stata rilevata una frequenza elevata di conflitti di blocco .NET.  Per determinare la causa, eseguire un profilo della concorrenza.|  
|Tipo regola|Informazioni|  
  
 Quando si esegue la profilatura tramite i metodi di campionamento, memoria .NET o conflitto di risorse, è necessario raccogliere almeno 25 campioni per attivare questa regola.  
  
## Causa  
 I dati relativi alle prestazioni di sistema raccolti con i dati di profilatura indicano che si è verificata una frequenza significativamente elevata di conflitti di blocco durante l'esecuzione dell'applicazione.  Considerare la possibilità di eseguire di nuovo la profilatura utilizzando il metodo di profilatura della concorrenza per individuare la causa dei conflitti.  
  
## Descrizione della regola  
 I blocchi vengono utilizzati per proteggere sezioni critiche di codice che devono essere eseguiti in serie un thread alla volta in un'applicazione multithreading.  Microsoft .NET Common Language Run\-time \(CLR\) fornisce un set completo di primitive di sincronizzazione e blocco.  Ad esempio, il linguaggio C\# supporta un'istruzione lock \(SyncLock in Visual Basic\).  Un'applicazione gestita può chiamare i metodi Monitor.Enter e Monitor.Exit nello spazio dei nomi System.Threading per acquisire e rilasciare direttamente un blocco.  .NET Framework supporta primitive di sincronizzazione e blocco aggiuntive, includendo classi che supportano mutex, blocchi ReaderWriter e semafori.  Per ulteriori informazioni, vedere [Cenni preliminari sulle primitive di sincronizzazione](http://go.microsoft.com/fwlink/?LinkId=177867) nella Guida per gli sviluppatori di .NET Framework sul sito Web MSDN.  Le classi .NET Framework sono sovrapposte ai servizi di sincronizzazione di livello inferiore incorporati nel sistema operativo Windows.  Includono oggetti sezione critica e molte funzioni diverse di segnalazione eventi e attesa.  Per ulteriori informazioni, vedere la sezione [Sincronizzazione](http://go.microsoft.com/fwlink/?LinkId=177869) della documentazione relativa allo sviluppo Win32 e COM in MSDN Library  
  
 I percorsi di memoria condivisi sottostanti le classi .NET Framework e gli oggetti Windows nativi utilizzati per la sincronizzazione e il blocco devono essere modificati tramite operazioni interlock.  Le operazioni interlock utilizzano istruzioni specifiche dell'hardware che agiscono sui percorsi di memoria condivisi per modificare il proprio stato utilizzando operazioni atomiche.  La coerenza delle operazioni atomiche è garantita attraverso tutti i processori del computer.  Blocchi e WaitHandle sono gli oggetti .NET che utilizzano automaticamente operazioni interlock quando vengono impostati o reimpostati.  Nell'applicazione possono essere presenti anche altre strutture dei dati della memoria condivisa che richiedono l'utilizzo di operazioni interlock per essere aggiornate in modo thread\-safe.  Per ulteriori informazioni, vedere la sezione [Operazioni interlocked](http://go.microsoft.com/fwlink/?LinkId=177870) in .NET Framework di MSDN library  
  
 Sincronizzazione e blocco sono meccanismi utilizzati per assicurare che tali applicazioni multi\-threading vengano eseguite correttamente.  Ogni thread di un'applicazione multi\-threading è un'unità di 'esecuzione indipendente, pianificata indipendentemente dal sistema operativo.  Si verifica un conflitto di blocco quando un thread che sta tentando di acquisire un blocco viene ritardato perché il blocco è trattenuto da un altro thread.  
  
 I blocchi sono spesso annidati.  L'annidamento si verifica quando un thread che esegue una sezione critica esegue una funzione che a sua volta richiede un altro blocco.  Una certa quantità di annidamento del blocco è inevitabile.  È possibile che la sezione critica chiami un metodo .NET Framework che si basa su blocchi per garantire che sia thread\-safe.  Una chiamata da una sezione critica nell'applicazione a un metodo Framework, che a sua volta utilizza un blocco tramite un handle di blocco diverso, causa l'annidamento dei blocchi.  Condizioni del blocco annidate possono causare problemi di prestazioni che sono notoriamente difficili da individuare e correggere.  
  
 Questa regola viene attivata quando misure adottate durante l'esecuzione di una profilatura indicano la presenza di quantità eccessivamente elevata di conflitti di blocco.  I conflitti di blocco ritardano l'esecuzione di thread in attesa del blocco.  È consigliabile analizzare anche quantità abbastanza limitate di conflitti di blocco in unit test o in test di carico eseguiti su hardware di fascia più bassa.  
  
> [!NOTE]
>  Quando la frequenza dei conflitti di blocco indicata nei dati di profilatura è eccessivamente elevata, viene generato il messaggio di avviso [DA0039: Frequenza molto elevata di conflitti di blocco](../profiling/da0039-very-high-rate-of-lock-contentions.md) anziché questo messaggio informativo.  
  
## Come esaminare un avviso  
 Fare doppio clic sul messaggio per passare alla visualizzazione [Contrassegni](../profiling/marks-view.md) dei dati di profilatura.  Individuare la colonna **LocksAndThreads CLR .NET\\Conflitti\/sec**.  Determinare se sono presenti fasi specifiche di esecuzione del programma in cui i conflitti di blocco sono maggiori rispetto ad altre fasi.  
  
 Questa regola viene attivata solo quando non si utilizza il metodo di profilatura della concorrenza.  Il metodo di profilatura della concorrenza è lo strumento migliore da utilizzare per diagnosticare i problemi di prestazioni correlati ai conflitti di blocco nell'applicazione.  Per comprendere il comportamento di blocco dell'applicazione, raccogliere dati di profilatura della concorrenza.  Questa operazione consente di individuare i blocchi con il maggior numero di conflitti, per quanto tempo viene ritardato il tempo di esecuzione del thread in attesa dei blocchi in conflitto e il codice specifico interessato.  I profili di concorrenza raccolgono dati su tutti i conflitti di blocco, incluso il comportamento di blocco di funzionalità di Windows native, classi .NET Framework e qualsiasi altra libreria di terze parti a cui fa riferimento l'applicazione.  Per informazioni sulla profilatura della concorrenza dall'IDE di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], vedere [Raccolta di dati di concorrenza di thread e processi](../profiling/collecting-thread-and-process-concurrency-data.md).  Per collegamenti a informazioni sulla profilatura della concorrenza dalla riga di comando, vedere la sezione **Using the Concurrency Method to Collect Resource Contention and Thread Activity Data** in [Utilizzo di metodi di profilatura dalla riga di comando](../profiling/using-profiling-methods-to-collect-performance-data-from-the-command-line.md).