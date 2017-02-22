---
title: "Risoluzione dei problemi relativi agli strumenti di profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0b61cdf7-75b7-4abd-aff2-7bd997717626
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
---
# Risoluzione dei problemi relativi agli strumenti di profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Durante l'utilizzo degli strumenti di profilatura è possibile riscontrare uno dei problemi seguenti:  
  
-   [Non vengono raccolti dati dagli strumenti di profilatura](#NoDataCollected)  
  
-   [Nelle visualizzazioni e nei rapporti di prestazioni vengono visualizzati numeri anziché nomi di funzione](#NoSymbols)  
  
##  <a name="NoDataCollected"></a> Non vengono raccolti dati dagli strumenti di profilatura  
 Dopo avere profilato un'applicazione, non viene creato un file dei dati di profilatura \(con estensione vsp\) e nella finestra Output o nella finestra di comando viene visualizzato il seguente avviso:  
  
 PRF0025: Dati non raccolti.  
  
 Il problema potrebbe risalire a diverse cause:  
  
-   Un processo profilato tramite il campionamento o il metodo di memoria .NET avvia un processo figlio che esegue il lavoro dell'applicazione.  In alcune applicazioni, ad esempio, viene letta la riga di comando per determinare se sono state avviate come applicazioni Windows o come applicazioni della riga di comando.  Se era necessaria un'applicazione Windows, il processo originale avvia un nuovo processo configurato come applicazione Windows e quello originale viene quindi chiuso.  Poiché i dati per i processi figlio non vengono raccolti automaticamente tramite gli strumenti di profilatura, non verrà raccolto alcun dato.  
  
     Per raccogliere i dati di profilatura in questa situazione, associare il profiler al processo figlio anziché utilizzarlo per avviare l'applicazione.  Per ulteriori informazioni, vedere [Procedura: Connettere e disconnettere il profiler a processi in esecuzione](../profiling/how-to-attach-and-detach-performance-tools-to-running-processes.md) e [Associa \(VSPerfCmd\)](../profiling/attach.md)  
  
##  <a name="NoSymbols"></a> Nelle visualizzazioni e nei rapporti di prestazioni vengono visualizzati numeri anziché nomi di funzione  
 Dopo avere profilato un'applicazione, vengono visualizzati numeri anziché nomi di funzione nei rapporti e nelle visualizzazioni.  
  
 Questo problema è dovuto all'impossibilità di trovare, tramite il motore di analisi degli strumenti di profilatura, i file con estensione pdb in cui sono contenute informazioni sui simboli mappate alle informazioni sul codice sorgente, ad esempio nomi di funzione e numeri di riga al file compilato.  Per impostazione predefinita, il file con estensione pdb viene creato tramite il compilatore durante la compilazione dell'applicazione.  Un riferimento alla directory locale del file con estensione pdb viene archiviato nell'applicazione compilata.  Tramite il motore di analisi viene eseguita una ricerca del file con estensione pdb nella directory a cui si fa riferimento e quindi nel file in cui è incluso attualmente il file dell'applicazione.  Se il file con estensione pdb non viene individuato, vengono utilizzati gli offset anziché i nomi di funzione.  
  
 È possibile risolvere il problema in uno dei due modi seguenti:  
  
-   Trovare i file con estensione pdb e posizionarli nella stessa directory dei file dell'applicazione.  
  
-   Incorporare le informazioni sui simboli nel file dei dati di profilatura \(con estensione vsp\).  Per ulteriori informazioni, vedere [Salvataggio delle informazioni sui simboli con i file di dati di profilatura](../profiling/saving-symbol-information-with-performance-data-files.md).  
  
> [!NOTE]
>  Il motore di analisi richiede che la versione del file con estensione pdb corrisponda a quella del file dell'applicazione compilato.  Un file con estensione pdb generato da una compilazione precedente o successiva del file dell'applicazione non sarà utilizzabile.