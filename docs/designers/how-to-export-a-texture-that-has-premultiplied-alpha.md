---
title: "Procedura: esportare una trama con alfa premoltiplicati | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 05348afa-f079-4f53-a05b-ecd91d13adab
caps.latest.revision: 4
caps.handback.revision: 4
author: "BrianPeek"
ms.author: "brpeek"
manager: "ghogen"
---
# Procedura: esportare una trama con alfa premoltiplicati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La pipeline del contenuto di immagine può generare trame alfa premoltiplicate da un'immagine di origine.  Possono risultare più semplici da utilizzare e più affidabili rispetto alle trame che non contengono valori alfa premoltiplicati.  
  
 In questo documento vengono illustrate queste attività:  
  
-   La configurazione dell'immagine di origine deve essere elaborata dalla pipeline del contenuto di immagine.  
  
-   Configurazione della pipeline del contenuto di immagine perché generi l'alfa premoltiplicato.  
  
## Alfa premoltiplicato  
 questo valore offre diversi vantaggi rispetto al valore alfa tradizionale non premoltiplicato, perché rappresenta meglio l'interazione reale della luce con i materiali fisici mediante la separazione del contributo di colore di texel \(il colore aggiunto alla scena\) dalla relativa traslucidità \(la quantità di colore sottostante di cui consente il passaggio\).  Alcuni vantaggi dei valori alfa premoltiplicati sono:  
  
-   La sfumatura con il valore alfa premoltiplicato è un'operazione associativa; il risultato della sfumatura di più trame semitrasparenti è lo stesso, indipendentemente dall'ordine in cui le trame vengono sfumate.  
  
-   A causa della natura associativa della sfumatura con il valore alfa premoltiplicato, il rendering a più passaggi degli oggetti semitrasparenti viene semplificato.  
  
-   Tramite il valore alfa premoltiplicato, sia la sfumatura aggiuntiva pura \(impostando alfa su zero\) che la sfumatura linearmente interpolata possono essere archiviate simultaneamente.  Ad esempio, in un sistema di particelle, una particella di fuoco sfumata in modo additivo può diventare una particella di fumo trasparente che viene sfumata utilizzando l'interpolazione lineare.  Senza valori alfa premoltiplicati, è necessario disegnare le particelle di fuoco separatamente dalle particelle di fumo e modificare lo stato di rendering tra le chiamate di disegno.  
  
-   La compressione delle trame che utilizzano i valori alfa premoltiplicati risulta di qualità superiore rispetto a quelle che non la utilizzano. Inoltre, queste trame e non presentano l'effetto di alone che può verificarsi quando si fondono trame che non utilizzano i valori alfa premoltiplicati.  
  
#### Per creare una trama che utilizza valori alfa premoltiplicati  
  
1.  Iniziare con una trama di base.  Caricare un file di immagine esistente oppure crearne uno, come descritto in [Procedura: Creare una trama di base](../Topic/How%20to:%20Create%20a%20Basic%20Texture.md).  
  
2.  Configurare il file di trama in modo che venga elaborato dalla pipeline del contenuto di immagine.  In **Esplora soluzioni** aprire il menu di scelta rapida per il file di trama, quindi scegliere **Proprietà**.  In **Proprietà di configurazione**, nella pagina **Generale**, impostare la proprietà **Tipo di elemento** su **Pipeline contenuti immagine**.  Assicurarsi che la proprietà **Contenuto** sia impostata su **Sì** e **Escludi da compilazione** sia impostata su **No**, quindi scegliere il pulsante **Applica**.  Viene visualizzata la pagina delle proprietà di configurazione **Pipeline contenuto immagine**.  
  
3.  Configurare la pipeline del contenuto di immagine perché generi l'alfa premoltiplicato.  In **Proprietà di configurazione**, **Pipeline contenuti immagine**, pagina **Generale**, impostare la proprietà **Converti in formato alpha premoltiplicato** su **Sì \(\/generatepremultipliedalpha\)**.  
  
4.  Scegliere il pulsante **OK**.  
  
 Quando si compila il progetto, la pipeline del contenuto di immagine converte l'immagine di origine dal formato di lavoro al formato di output specificato, inclusa la conversione dell'immagine in formato alfa premoltiplicato, e il risultato viene copiato nella directory di output del progetto.