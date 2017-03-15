---
title: "Procedura: esportare una trama che contiene mipmap | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d1ad14b-44fb-4cf0-a995-5e2f60026524
caps.latest.revision: 7
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
caps.handback.revision: 7
---
# Procedura: esportare una trama che contiene mipmap
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La pipeline del contenuto di immagine può generare mipmap da un'immagine di origine come parte della fase di compilazione del progetto.  Quando non è necessario specificare manualmente il contenuto dell'immagine di ogni livello MIP, come può essere richiesto per ottenere determinati effetti, la generazione di mipmap in fase di compilazione assicura che il contenuto della mipmap sia sempre sincronizzato ed elimina il costo di prestazioni della generazione di mipmap in fase di esecuzione.  
  
 In questo documento vengono illustrate queste attività:  
  
-   La configurazione dell'immagine di origine deve essere elaborata dalla pipeline del contenuto di immagine.  
  
-   Configurazione della pipeline del contenuto di immagine perché generi mipmap.  
  
## Esportazione delle mipmap  
 Il mapping MIP fornisce automaticamente il livello di dettaglio nello spazio dello schermo per le superfici strutturate in un gioco 3D o in un'applicazione.  Migliora le prestazioni di rendering di un gioco o di un'applicazione calcolando anticipatamente le versioni sottocampionate di una trama in modo che l'operazione non debba essere ripetuta ogni volta che una trama viene campionata.  
  
#### Per esportare una trama con mipmap  
  
1.  Iniziare con una trama di base.  Caricare un file di immagine esistente oppure crearne uno, come descritto in [Procedura: Creare una trama di base](../Topic/How%20to:%20Create%20a%20Basic%20Texture.md).  Per supportare le mipmap, specificare una trama con valori di larghezza e altezza multipli di due ed equivalenti, ad esempio 64x64, 256x256 o 512x512.  
  
2.  Configurare il file di trama appena creato in modo che venga elaborato dalla pipeline del contenuto di immagine.  In **Esplora soluzioni** aprire il menu di scelta rapida per il file di trama appena creato, quindi scegliere **Proprietà**.  In **Proprietà di configurazione**, nella pagina **Generale**, impostare la proprietà **Tipo di elemento** su **Pipeline contenuti immagine**.  Assicurarsi che la proprietà **Contenuto** sia impostata su **Sì** e **Escludi da compilazione** sia impostata su **No**, quindi scegliere il pulsante **Applica**.  Viene visualizzata la pagina delle proprietà di configurazione **Pipeline contenuto immagine**.  
  
3.  Configurare la pipeline del contenuto di immagine perché generi mipmap.  In **Proprietà di configurazione**, **Pipeline contenuti immagine**, pagina **Generale** impostare la proprietà **Genera MIP** su **Sì \(\/generatemips\)**.  
  
4.  Scegliere il pulsante **OK**.  
  
 Quando si compila il progetto, la pipeline del contenuto di immagine converte l'immagine di origine dal formato di lavoro al formato di output specificato, inclusi livelli MIP, e il risultato viene copiato nella directory di output del progetto.