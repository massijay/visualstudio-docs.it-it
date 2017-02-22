---
title: "XML Schema Explorer | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 2fc39e98-b194-456b-a452-cfafb0a52d66
caps.latest.revision: 3
caps.handback.revision: 3
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# XML Schema Explorer
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

XML Schema Explorer è integrato con Microsoft Visual Studio e con l'editor XML per consentire di utilizzare gli schemi XML Schema Definition Language \(XSD\).Quando si apre un file XML Schema, il nodo **Set di schemi** viene visualizzato in XML Schema Explorer.In XML Schema Explorer vengono visualizzati anche tutti gli schemi inclusi, importati o ridefiniti per il file di destinazione e qualsiasi file a cui viene fatto riferimento tramite un'istruzione `include` o `import`.  
  
 XML Schema Explorer consente di effettuare le operazioni seguenti:  
  
-   Ottenere una rapida panoramica del set di schemi.  
  
-   Esplorare e spostarsi all'interno della struttura ad albero.  
  
-   Eseguire ricerche per parola chiave e specifiche dello schema.Per ulteriori informazioni, vedere [Ricerca del set di schemi](../xml-tools/searching-the-schema-set.md).  
  
-   Aggiungere i risultati della ricerca alla visualizzazione grafico o alla visualizzazione modello di contenuto  
  
-   Ordinare la struttura ad albero in base a nome, tipo o ordine dei documenti.Per ulteriori informazioni, vedere [Ordinamento, filtro e raggruppamento](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md).  
  
-   Aprire l'editor XML e passare ai percorsi del codice nel file XSD.Per ulteriori informazioni, vedere [Integrazione con l'editor XML](../xml-tools/integration-with-xml-editor.md).  
  
-   Generare codice XML di esempio per gli elementi globali.  
  
 XML Schema Explorer fornisce una visualizzazione gerarchica del set di schemi tramite una visualizzazione struttura ad albero.XML Schema Explorer offre inoltre funzionalità di ricerca, filtraggio, navigazione e ordinamento.Per accedere a XML Schema Explorer, eseguire una delle operazioni seguenti:  
  
-   Nella [visualizzazione iniziale](../xml-tools/start-view.md), fare clic sul collegamento **XML Schema Explorer**.  
  
-   Nella [visualizzazione grafico](../xml-tools/graph-view.md) o nella [visualizzazione modello di contenuto](../xml-tools/content-model-view.md), se si dispone di nodi nell'area di lavoro utilizzare il menu di scelta rapida per selezionare XML Schema Explorer.  
  
-   È anche possibile selezionare XML Schema Explorer dal menu **Visualizza**.  
  
-   È possibile accedere a XML Schema Explorer da un file .vb che dispone di un valore letterale XML di Visual Basic associato a un file .xsd.Per visualizzare il set di schemi in XML Schema Explorer, fare clic con il pulsante destro del mouse su un nodo XML in un'importazione di valore letterale XML o spazio dei nomi XML e selezionare il comando **Mostra in Schema Explorer**.Per ulteriori informazioni, vedere [Integrazione di valori letterali XML con XML Schema Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md).  
  
## Visualizzazione struttura ad albero  
 In XML Schema Explorer le informazioni sul set di schemi precompilati vengono visualizzate in una struttura ad albero.La struttura ad albero è organizzata come segue:  
  
-   Al livello principale è presente il nodo del set di schemi.  
  
-   Il secondo livello contiene gli spazi dei nomi.  
  
-   Nel terzo livello sono presenti i file.  
  
-   Il quarto livello contiene i nodi globalie può includere elementi, gruppi, tipi complessi, tipi semplici, attributi, gruppi di attributi e istruzioni `include`, `import` e `redefine`.  
  
 Di seguito viene riportato un esempio di struttura ad albero:  
  
 ![XML Schema Explorer](../xml-tools/media/xmlschemaexplorer.gif "XMLSchemaExplorer")  
  
## Selezione e attivazione  
 Per evidenziare e selezionare un nodo, fare clic una volta in Schema Explorer.  
  
 Per attivare un nodo, fare doppio clic su di esso o premere **Invio** quando il nodo è selezionato.  
  
-   L'attivazione di un nodo consente di aprire il file in cui questo nodo è definito \(se non è già aperto\) e di selezionare il nodo nel file.  
  
-   L'attivazione di un nodo di file consente di aprire il file selezionato \(se non è già aperto\) e di evidenziare il nodo `<schema>`.  
  
-   L'attivazione di un nodo set di schemi o spazio dei nomi non esegue alcuna operazione.  
  
## Trascinamento di nodi  
 È possibile trascinare nodi globali, nodi di file e nodi spazio dei nomi su una visualizzazione di Progettazione XSD.Se la visualizzazione corrente è la [visualizzazione iniziale](../xml-tools/start-view.md), il trascinamento di un nodo sulla visualizzazione consentirà di aprire la [visualizzazione grafico](../xml-tools/graph-view.md).Se la visualizzazione corrente è la [visualizzazione modello di contenuto](../xml-tools/content-model-view.md) o la visualizzazione grafico, la visualizzazione non cambierà quando un nodo viene trascinato su di essa.  
  
 Il rilascio di file sulla visualizzazione aggiungerà tutti i nodi globali contenuti nel file all'[area di lavoro di Progettazione XSD](../xml-tools/xml-schema-designer-workspace.md).Il rilascio degli spazi dei nomi sulla visualizzazione aggiungerà tutti i nodi globali contenuti nello spazio dei nomi all'area di lavoro.L'area di lavoro è condivisa da tutte le visualizzazioni.  
  
 Non è possibile trascinare nodi locali o importazioni.  
  
## In questa sezione  
  
-   [Ricerche nel set di schemi](../xml-tools/searching-the-schema-set.md)  
  
-   [Ordinamento, filtro e raggruppamento](../xml-tools/sorting-filtering-and-grouping-xml-schema-explorer.md)  
  
-   [Menu di scelta rapida](../xml-tools/context-menus-xml-schema-explorer.md)  
  
-   [Integrazione di valori letterali XML con XML Schema Explorer](../xml-tools/integration-of-xml-literals-with-xml-schema-explorer.md)  
  
## Vedere anche  
 [Procedura: aggiungere nodi all'area di lavoro da XML Schema Explorer](../xml-tools/how-to-add-nodes-to-the-workspace-from-the-xml-schema-explorer.md)