---
title: "Menu di scelta rapida (XML Schema Explorer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 42ab17ca-b8c1-40d7-beda-d033f66fe874
caps.latest.revision: 2
caps.handback.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# Menu di scelta rapida (XML Schema Explorer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le seguenti voci di menu di scelta rapida sono utilizzate per eseguire ricerche specifiche dello schema nonché altre operazioni.  
  
## Tipo di nodo: set di schemi  
 Nella tabella seguente vengono descritte le opzioni disponibili per un nodo del set di schemi.  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**Mostra elementi radice più probabili**|Consente di individuare ed evidenziare tutti gli elementi globali ai quali non fanno riferimento gli altri elementi globali.|  
|**Mostra tipi globali**|Consente di individuare ed evidenziare tutti i tipi globali nel set di schemi.|  
|**Mostra elementi globali**|Consente di individuare ed evidenziare tutti gli elementi globali nel set di schemi.|  
|**Finestra Proprietà**|Consente di aprire la finestra **Proprietà** \(se non è già aperta\).In questa finestra verranno visualizzate le informazioni sul nodo.|  
  
## Tipo di nodo: spazio dei nomi  
 Nella tabella seguente vengono descritte le opzioni disponibili per un nodo dello spazio dei nomi.  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**Mostra tutti i riferimenti in ingresso**|Consente di individuare ed evidenziare i file che importano lo spazio dei nomi selezionato.|  
|**Mostra tutti i riferimenti in uscita**|Per ogni file presente nello spazio dei nomi selezionato, consente di individuare ed evidenziare gli elementi seguenti:<br /><br /> -   Tutti gli spazi dei nomi ai quali fanno riferimento istruzioni Import senza attributo `schemaLocation`.<br />-   Tutti i file in spazi di nomi diversi da quello selezionato che sono specificati nell'attributo `schemaLocation` di istruzioni Import e Include.|  
|**Mostra tipi globali**|Consente di individuare ed evidenziare tutti i tipi globali nello spazio di nomi selezionato.|  
|**Mostra elementi globali**|Consente di individuare ed evidenziare tutti gli elementi globali nello spazio di nomi selezionato.|  
|**Finestra Proprietà**|Consente di aprire la finestra **Proprietà** \(se non è già aperta\).In questa finestra verranno visualizzate le informazioni sul nodo.|  
  
## Tipo di nodo: file  
 Nella tabella seguente vengono descritte le opzioni disponibili per un nodo di file.  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**Mostra tutti i riferimenti in ingresso**|Consente di individuare ed evidenziare tutti i file che specificano il file selezionato negli attributi `schemaLocation` delle istruzioni Import e Include.|  
|**Mostra tutti i riferimenti in uscita**|Consente di individuare ed evidenziare gli elementi seguenti:<br /><br /> -   Tutti gli spazi dei nomi specificati negli attributi dello spazio dei nomi di tutte le istruzioni Import prive dell'attributo `schemaLocation`.<br />-   Tutti i file specificati negli attributi `schemaLocation` di ogni istruzione Import e Include.|  
|**Mostra tipi globali**|Consente di individuare ed evidenziare tutti i tipi globali in questo file.|  
|**Mostra elementi globali**|Consente di individuare ed evidenziare tutti gli elementi globali in questo file.|  
|**Visualizza codice**|Consente di aprire il file che contiene il nodo selezionato nell'editor XML.L'elemento selezionato in XML Schema Explorer sarà selezionato anche nell'editor XML.|  
|**Finestra Proprietà**|Consente di aprire la finestra **Proprietà** \(se non è già aperta\).In questa finestra verranno visualizzate le informazioni sul nodo.|  
  
## Tutti i tipi di nodo globali  
 Nella tabella seguente vengono descritte le opzioni disponibili per tutti i nodi globali.  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**Mostra in visualizzazione grafico**|Consente di aprire la visualizzazione grafico.Se il nodo selezionato non si trova nell'area di lavoro, aggiungerlo all'area di lavoro e selezionarlo.|  
|**Mostra nella visualizzazione modello di contenuto**|Consente di aprire la visualizzazione modello di contenuto.Se il nodo selezionato non si trova nell'area di lavoro, aggiungerlo all'area di lavoro e selezionarlo.|  
|**Visualizza codice**|Consente di aprire il file che contiene il nodo selezionato nell'editor XML.L'elemento selezionato in XML Schema Explorer sarà selezionato anche nell'editor XML.|  
|**Finestra Proprietà**|Consente di aprire la finestra **Proprietà** \(se non è già aperta\).In questa finestra verranno visualizzate le informazioni sul nodo.|  
  
## Tipo di nodo: elemento  
 Oltre alle opzioni del nodo globale descritte in precedenza, il menu di scelta rapida per i nodi dell'elemento dispone delle opzioni seguenti:  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**Vai a definizione di tipo**|Consente di passare alla definizione di tipo dell'elemento selezionato.È applicabile quando per l'elemento viene utilizzato un tipo globale.|  
|**Vai all'elemento originale**|Per i riferimenti agli elementi consente di passare alla definizione effettiva dell'elemento.|  
|**Mostra tutti i riferimenti**|Per gli elementi globali, consente di individuare ed evidenziare tutti i riferimenti all'elemento selezionato \(elementi con `ref="selectedElement"`\).|  
|**Mostra membri del gruppo di sostituzione**|Per intestazioni di un gruppo di sostituzione, consente di inviduare ed evidenziare tutti gli elementi membri del gruppo di sostituzione di cui l'elemento selezionato è membro.Mostra i partecipanti diretti e indiretti.|  
|**Mostra intestazioni del gruppo di sostituzione**|Per gli elementi globali membri di un gruppo di sostituzione, consente di inviduare ed evidenziare tutte le intestazioni dirette e indirette per l'elemento selezionato, come le seguenti:<br /><br /> -   Intestazione del gruppo di sostituzione specificata nell'elemento selezionato.<br />-   Intestazione del gruppo di sostituzione specificata nell'elemento Head.|  
|**Genera XML di esempio**|Disponibile solo per elementi globali.Consente di generare un file XML di esempio per l'elemento globale.|  
  
## Tipo di nodo: tipi globali  
 Oltre alle opzioni del nodo globale descritte in precedenza, il menu di scelta rapida per i nodi del tipo globale dispone delle opzioni seguenti:  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**Mostra tipo di base**|Se il tipo selezionato è derivato da un tipo globale, consente di passare al tipo di base del tipo selezionato.|  
|**Mostra tutti i riferimenti**|Consente di inviduare ed evidenziare tutti i riferimenti al tipo selezionato,inclusi gli elementi e attributi del tipo selezionato e i tipi derivati dal tipo selezionato.|  
|**Mostra tutti i tipi derivati**|Consente di individuare ed evidenziare tutti i tipi che sono direttamente e indirettamente derivati dal tipo selezionato.|  
|**Mostra tutti i predecessori**|Mostra tutti i tipi padre \(di base\).|  
  
## Tipo di nodo: attributo  
 Oltre alle opzioni del nodo globale descritte in precedenza, il menu di scelta rapida per i nodi dell'attributo dispone delle opzioni seguenti:  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**Vai a definizione di tipo**|Se per l'attributo è utilizzato un tipo globale, consente di passare alla definizione di tipo dell'attributo selezionato.|  
|**Vai all'attributo originale**|Per i riferimenti agli attributi consente di passare alla definizione effettiva dell'attributo.|  
|**Mostra tutti i riferimenti**|Per gli attributi globali, consente di individuare ed evidenziare tutti i riferimenti \(altri attributi con `ref="selectedAttribute"`\) all'attributo selezionato.|  
  
## Tipo di nodo: gruppo di attributi  
 Oltre alle opzioni del nodo globale descritte in precedenza, il menu di scelta rapida per i nodi del gruppo di attributi dispone delle opzioni seguenti:  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**Vai a definizione**|Per i riferimenti consente di passare alla definizione effettiva dell'attributo.|  
|**Mostra tutti i membri**|Consente di individuare ed evidenziare tutti i membri del gruppo di attributi.|  
|**Mostra tutti i riferimenti**|Consente di individuare ed evidenziare tutti i riferimenti \(gruppi di attributi con `ref="selectedAttributeGroup"`\) al gruppo di attributi selezionato.|  
  
## Tipo di nodo: gruppo denominato  
 Oltre alle opzioni del nodo globale descritte in precedenza, il menu di scelta rapida per i nodi del gruppo denominato dispone delle opzioni seguenti:  
  
|Opzione|Descrizione|  
|-------------|-----------------|  
|**Vai a definizione**|Per i riferimenti consente di passare alla definizione effettiva dell'attributo.|  
|**Mostra tutti i membri**|Consente di individuare ed evidenziare tutti i membri del gruppo denominato.|  
|**Mostra tutti i riferimenti**|Consente di individuare ed evidenziare tutti i riferimenti \(gruppi con `ref="selectedGroup"`\) al gruppo selezionato.|  
  
## Vedere anche  
 [XML Schema Explorer](../xml-tools/xml-schema-explorer.md)   
 [Ricerche nel set di schemi](../xml-tools/searching-the-schema-set.md)