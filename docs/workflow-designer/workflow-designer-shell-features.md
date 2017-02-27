---
title: "Caratteristiche della shell di Progettazione flussi di lavoro | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "WFDShellFeatures.UI"
ms.assetid: 14bfe312-9592-408e-92ce-e98585ad16e7
caps.latest.revision: 6
author: "ErikRe"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# Caratteristiche della shell di Progettazione flussi di lavoro
[!INCLUDE[wfd1](../workflow-designer/includes/wfd1_md.md)] è formato da tre principali aree dell'interfaccia utente, ovvero l'area della finestra di progettazione, la barra di navigazione al di sopra di essa e la shell al di sotto di essa.La barra di navigazione, posizionata nella parte superiore dello schermo, viene utilizzata per visualizzare l'elenco di predecessori dell'attività radice corrente.[!INCLUDE[crdefault](../test/includes/crdefault_md.md)][Procedura: utilizzare l'esplorazione tramite la barra di navigazione](../workflow-designer/how-to-use-breadcrumb-navigation.md).L'area della finestra di progettazione, posizionata al centro dello schermo, viene utilizzata per creare flussi di lavoro.La shell, posizionata nella parte inferiore dello schermo, contiene alcuni pulsanti per la gestione della visualizzazione corrente.  
  
## Caratteristiche della shell  
 La shell presenta dei pulsanti sul lato destro della barra che è possibile utilizzare per eseguire lo zoom avanti o indietro del flusso di lavoro, adattare il contenuto del flusso di lavoro alla dimensione dello schermo e mostrare o nascondere la carta panoramica.È possibile eseguire lo zoom avanti o indietro di un flusso di lavoro utilizzando i tasti di scelta rapida CTRL\+\+ e CTRL\+ \-.  
  
## Carta panoramica  
 Nella carta panoramica viene visualizzata una versione ridotta dell'intera attività alla radice della barra di navigazione corrente, inclusi tutti i relativi figli e figli espansi.Un riquadro di visualizzazione, ovvero un rettangolo con un bordo arancione, evidenzia la parte dell'attività attualmente visualizzata nell'editor.Trascinando il rettangolo attorno alla carta panoramica è possibile scorrere la finestra di progettazione del flusso di lavoro e modificare la visualizzazione dell'editor.  
  
> [!NOTE]
>  L'interfaccia utente di [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] è virtualizzata.Gli ActivityDesigner sono sottoposti a rendering solo se necessario.Se una parte del flusso di lavoro non è stata mai disegnata nell'area della finestra di progettazione, viene visualizzata come bianca sulla carta panoramica.Il flusso di lavoro viene disegnato scorrendo su tutta la carta panoramica.  
  
## Copia o salvataggio dei flussi di lavoro come immagini  
 I flussi di lavoro possono essere copiati in formato bitmap o salvati in formato bitmap o vettoriale.La copia o il salvataggio di un'immagine consente di esportare in un altro programma una visualizzazione dell'intera attività alla radice della barra di navigazione corrente, inclusi tutti i relativi figli e figli espansi.  
  
 Per eseguire la copia come immagine, fare clic con il pulsante destro del mouse in un punto qualsiasi della finestra di progettazione e selezionare **Copia come immagine**.Per eseguire il salvataggio come immagine, fare clic con il pulsante destro del mouse in un punto qualsiasi della finestra di progettazione e selezionare **Salva come immagine**.È possibile salvare i flussi di lavoro in formato JPG, PNG, GIF o XPS.Il formato viene selezionato nell'elenco a discesa **Tipo file:** situato nella parte inferiore della finestra di dialogo **Salva con nome**.  
  
## Tipi di carattere e colori  
 I tipi di carattere utilizzati in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] all'interno di [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] dipendono dal tipo di carattere dell'ambiente.I colori visualizzati in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)] cambiano se si utilizza una combinazione di colori di contrasto elevato per il tema del sistema operativo.Per rendere effettive le modifiche in [!INCLUDE[wfd2](../workflow-designer/includes/wfd2_md.md)], è necessario riavviare [!INCLUDE[vs2010](../modeling/includes/vs2010_md.md)] dopo aver modificato le impostazioni del tipo di carattere e del colore.