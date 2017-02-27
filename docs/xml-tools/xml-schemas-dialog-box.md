---
title: "Finestra di dialogo Schemi XML | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: 2
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 2
---
# Finestra di dialogo Schemi XML
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La finestra di dialogo **Schemi XML** consente di selezionare lo schema XSD \(XML Schema Definition Language\) da associare a un documento XML.È possibile selezionare uno schema dalla cache degli schemi oppure specificare uno schema che non si trova nella cache.Gli schemi selezionati vengono considerati parte di un set di schemi,che viene utilizzato per IntelliSense e per la convalida dei documenti XML.  
  
 Per accedere alla finestra di dialogo **Schemi XML** fare clic sul pulsante **Schemi** nella finestra delle proprietà del documento oppure scegliere **Schemi** dal menu **XML**.  
  
## Elenco UIElement  
 **Utilizza**  
 Consente di selezionare la modalità di utilizzo dello schema XML.  
  
-   **Automatico**.Questo schema non è utilizzato dal documento corrente ma è disponibile per l'associazione automatica.Se il documento XML dichiara uno spazio di nomi che corrisponde al `targetNamespace` di questo schema, lo schema viene automaticamente associato e incluso nel set di schemi.  
  
-   **Utilizza questo schema**.Questo schema è utilizzato dal documento corrente.L'utilizzo di questo schema è stato richiesto in modo esplicito selezionando questa colonna oppure lo schema è stato associato automaticamente in base a un `targetNamespace` corrispondente.  
  
-   **Non utilizzare gli schemi selezionati**.Questo schema non è utilizzato dal documento corrente anche se dispone di un `targetNamespace` corrispondente.Questa impostazione può essere utile per la risoluzione di conflitti nel caso in cui la cache dello schema o la soluzione contengano più versioni dello stesso schema.  
  
 **Spazio dei nomi di destinazione**  
 Consente di visualizzare lo spazio dei nomi di destinazione associato allo schema XML.  
  
 **Nome file**  
 Consente di visualizzare il nome del file dello schema XML.  
  
 **Aggiungi**  
 Viene visualizzata la finestra di dialogo **Apri schema XSD**, che consente di selezionare altri schemi da aggiungere al set di schemi.Quando si aggiunge uno schema al set di schemi il valore della colonna **Utilizza** è impostato su **Utilizza questo schema**.  
  
 **Rimuovi**  
 Consente di rimuovere lo schema attualmente selezionato dal set di schemi.L'operazione rimuove lo schema dalla cache degli schemi in memoria, ma non dal file system.  
  
## Vedere anche  
 [Componenti dell'editor XML](../xml-tools/xml-editor-components.md)   
 [Procedura: selezionare gli schemi XML da utilizzare](../xml-tools/how-to-select-the-xml-schemas-to-use.md)   
 [Cache degli schemi](../xml-tools/schema-cache.md)