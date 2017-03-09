---
title: "DA0024: Tempo CPU GC eccessivo | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.performance.DA0024"
  - "vs.performance.24"
  - "vs.performance.rules.DA0024"
ms.assetid: 228872da-77d0-4da5-b455-ac57fb1867c9
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# DA0024: Tempo CPU GC eccessivo
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|Id regola|DA0024|  
|Categoria|Utilizzo di .NET framework|  
|Metodo di profilatura|Tutti|  
|Messaggio|Percentuale tempo in GC è molto elevata. Esiste una quantità eccessiva di overhead di garbage collection.|  
|Tipo regola|Avviso|  
  
 Quando esegue la profilatura tramite il campionamento di memoria .NET o metodi di contesa di risorse, è necessario raccogliere almeno 10 campioni per attivare questa regola.  
  
## <a name="cause"></a>Causa  
 I dati sulle prestazioni del sistema raccolti durante l'analisi indicano che la quantità di tempo impiegato nell'operazione di garbage collection è eccessivo rispetto al tempo di elaborazione totale dell'applicazione.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Microsoft .NET common language runtime (CLR) fornisce un meccanismo di gestione automatica della memoria che utilizza un garbage collector di recuperare memoria da oggetti non più utilizzati dall'applicazione. Il garbage collector è orientato alla generazione, basandosi sull'ipotesi che molte allocazioni sono di breve durate. Le variabili locali, ad esempio, devono essere di breve durate. Avviano gli oggetti appena creati nella generazione 0 (gen 0) e quindi procedono alla generazione 1 se vengono conservati dopo un'esecuzione di operazioni di garbage collection e infine transizione alla generazione 2 se l'applicazione li utilizza ancora.  
  
 Gli oggetti nella generazione 0 vengono raccolti frequentemente e in genere molto efficiente. Gli oggetti nella generazione 1 vengono raccolti meno frequentemente e meno efficiente. Infine, oggetti di lunga durata nella generazione 2 devono essere raccolti ancor meno frequente. Raccolta di generazione 2, ovvero eseguire una completa di garbage collection, è anche l'operazione più dispendiosa.  
  
 Questa regola viene attivata quando la quantità di tempo impiegato nell'operazione di garbage collection è eccessivo rispetto al tempo di elaborazione totale dell'applicazione.  
  
> [!NOTE]
>  Quando la percentuale di tempo impiegato per l'operazione di garbage collection è significativo, ma non eccessiva rispetto al tempo di elaborazione totale dell'applicazione, il [DA0023: tempo CPU GC elevato](../profiling/da0023-high-gc-cpu-time.md) avviso viene generato invece di questa regola.  
  
## <a name="how-to-investigate-a-warning"></a>Come ricercare un messaggio di avviso  
 Fare doppio clic sul messaggio nella finestra Elenco errori per passare per il [visualizzazione contrassegni](../profiling/marks-view.md) dei dati di profilatura. Trovare il **memoria CLR .NET\\Percentuale tempo in GC** colonna. Determinare se sono presenti fasi specifiche dell'esecuzione del programma in cui il sovraccarico di garbage collection della memoria gestita è più pesante rispetto ad altre fasi. Confrontare i valori dei contatori % tempo in GC valore per la frequenza di garbage collection segnalato nel **raccolte di generazione 0**, **raccolte di generazione 1**, **raccolte di generazione 2** valori.  
  
 Il valore percentuale tempo in GC tenta segnalare la quantità di tempo impiegato da un'applicazione di eseguire operazioni di garbage collection proporzionale alla quantità totale di elaborazione. Tenere presente che esistono circostanze in cui il valore percentuale tempo in GC può segnalare un valore molto elevato, ma non a causa di un numero eccessivo di operazioni di garbage collection. Per ulteriori informazioni sul modo in cui viene calcolata la percentuale di tempo in GC, vedere il [differenza tra i dati delle prestazioni segnalati da strumenti diversi – 4](http://go.microsoft.com/fwlink/?LinkId=177863) voce di **Weblog del Maoni** su MSDN. Se si verificano errori di pagina o l'applicazione viene superata da altre operazioni con priorità superiore sul computer durante l'operazione di garbage collection, la percentuale di tempo nel contatore GC rifletterà tali ritardi aggiuntivi.