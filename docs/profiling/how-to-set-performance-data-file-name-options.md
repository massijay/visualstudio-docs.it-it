---
title: "Procedura: impostare le opzioni relative ai nomi file dei dati di profilatura | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-debug"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d7a8d6b9-ab23-46fb-98ed-774781157860
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Procedura: impostare le opzioni relative ai nomi file dei dati di profilatura
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Per impostazione predefinita, un file dei dati di profilo \(vsp\) viene salvato utilizzando la sintassi seguente:  
  
 *Percorso\\File\-VSP\\AAMMGG\(N\)* **.vsp**  
  
 È possibile modificare i parametri di denominazione nella pagina Generale della finestra di dialogo delle proprietà per la sessione di prestazioni.  
  
 **Requisiti**  
  
-   [!INCLUDE[vsUltLong](../code-quality/includes/vsultlong_md.md)], [!INCLUDE[vsPreLong](../code-quality/includes/vsprelong_md.md)], [!INCLUDE[vsPro](../code-quality/includes/vspro_md.md)]  
  
|||  
|-|-|  
|*Percorso*|Directory che contiene il rapporto.  Il percorso predefinito è la cartella della soluzione o il percorso predefinito per i progetti e le soluzioni dell'utente.|  
|*File\-VSP*|Nome del file dei dati di profilo.  Il nome predefinito è il nome della soluzione o dell'eseguibile profilato.|  
|*AAMMGG*|Indicatore di data che indica l'anno, il mese e il giorno della raccolta dei dati di profilo.|  
|*\(N\)*|Se esiste più di un file dei dati di profilo, un numero incrementato viene aggiunto al nome file tra parentesi.|  
  
### Per modificare la sintassi di denominazione dei file dei dati di profilo di una sessione di prestazioni  
  
1.  In **Esplora prestazioni**, fare clic con il pulsante destro del mouse sul nome della sessione di prestazioni, quindi scegliere **Proprietà**.  
  
2.  Scegliere **Generale**.  
  
3.  In **Rapporto**, modificare le impostazioni seguenti:  
  
    |||  
    |-|-|  
    |**Percorso rapporto**|Specificare una directory per archiviare i file dei dati di profilo.|  
    |**Nome rapporto**|Specificare un nome di base per i file.|  
    |**Aggiungere automaticamente nuovi rapporti alla sessione**|Selezionare la casella di controllo per aggiungere automaticamente il file di dati alla sessione di prestazioni.|  
    |**Accodare un numero incrementale ai rapporti generati**|Selezionare la casella di controllo per aggiungere un numero incrementale al nome file quando esiste più di un file con lo stesso nome.  Deselezionare la casella di controllo per sovrascrivere un file esistente.|  
    |**Utilizzare un timestamp per il numero**|Selezionare la casella di controllo per aggiungere un datestamp al nome file.|