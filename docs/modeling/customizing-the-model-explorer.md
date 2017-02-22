---
title: "Personalizzazione di Esplora modelli | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.explorerbehavior"
helpviewer_keywords: 
  - "Strumenti del linguaggio specifico di dominio, Esplora linguaggio specifico di dominio"
ms.assetid: d2926444-9408-41d8-a27e-3fd0c416f9ac
caps.latest.revision: 20
caps.handback.revision: 20
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Personalizzazione di Esplora modelli
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile modificare l'aspetto e il comportamento di per la finestra di progettazione del linguaggio specifico di dominio come segue:  
  
-   Modificare il titolo della finestra.  
  
-   Modificare l'icona della scheda.  
  
-   modificare le icone per i nodi.  
  
-   Nascondere nodi.  
  
## Modificare il titolo della finestra  
 Per modificare il titolo della finestra esplora soluzioni generato, selezionare **Comportamento di visualizzazione** in  **DSL Esplora Risorse**quindi  **proprietà** la finestra, impostare  **titolo** proprietà al titolo desiderato.  
  
## Modificare l'icona della scheda  
 Per modificare l'icona della scheda di esplora modelli scegliere da, utilizzare un'icona 16x16\-pixel in un file con estensione bmp.  Inserire il file icona in \\DslPackage\\Resources\\ folder, and then change the file name to ModelExplorerToolWindowBitmaps BMP.  Ad esempio, è possibile modificare [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] il file di icona di setup.ico al formato jpg e rinominato a DSLLanguageName \\DslPackage\\Resources\\ModelExplorerToolWindowBitmaps BMP.  La finestra di progettazione generata visualizzare questa icona nella scheda di quando è ancorata insieme a **Esplora soluzioni**.  
  
## Icone personalizzate per i nodi di esplora  
 È possibile personalizzare i nodi nell'esploratore utilizzando le impostazioni di navigazione del nodo.  Nella procedura riportata di seguito viene illustrato come aggiungere un'icona a un nodo.  
  
#### Per aggiungere un'icona a un nodo di esplorazione  
  
1.  Creare un oggetto [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] soluzione utilizzando il modello della soluzione flusso di attività.  
  
2.  Inserire un file jpg contenente un'icona 16x16\-pixel in **Dsl \\Resources** cartella della soluzione.  
  
3.  in **DSL Esplora Risorse**, fare clic con il pulsante destro del mouse  **Comportamento di visualizzazione** quindi scegliere  **Aggiungere nuove impostazioni di navigazione del nodo**.  
  
     **ExplorerNodeSettings** il nodo viene visualizzato sotto  **Impostazioni personalizzate del nodo** nodo.  
  
4.  selezionato **ExplorerNodeSettings**quindi  **proprietà** finestra, impostare  **classe** in  **attore**.  
  
5.  set **Icona da visualizzare** il percorso del file icona.  
  
6.  Trasformazione di tutti i modelli e quindi compilare ed eseguire la soluzione.  
  
7.  Nella finestra di progettazione generata, aprire il diagramma di esempio.  
  
     Esplora risorse deve mostrare tre **attore** nodi che dispongono dell'icona.  
  
> [!NOTE]
>  Se si imposta un'icona del nodo per qualsiasi elemento visualizzato nell'esploratore generato, tutti i nodi di esplora visualizzare l'icona.  Se nessuna icona è stata impostata, i nodi visualizzare l'icona predefinita.  
  
## Modificare il nome visualizzato su un nodo di esplorazione  
 È possibile modificare la modalità con cui i nomi degli elementi del modello vengono nell'esploratore.  Nella procedura riportata di seguito come visualizzare il nome dell'attività a cui viene fatto riferimento da un commento nel nodo di commento.  
  
#### Per visualizzare una proprietà  
  
1.  Aprire la soluzione creata nella procedura precedente.  
  
2.  Assicurarsi che il commento faccia riferimento a una sola classe di dominio impostare la molteplicità del ruolo con il nome proprietà **oggetti** a 0..1.  Il nome della proprietà deve diventare **oggetto**e il nome della relazione dovrebbe diventare  **CommentReferencesSubject**.  
  
3.  in **DSL Esplora Risorse**, fare clic con il pulsante destro del mouse  **Comportamento di visualizzazione** quindi scegliere  **Aggiungere nuove impostazioni di navigazione del nodo**.  
  
     **ExplorerNodeSettings** il nodo viene visualizzato sotto  **Impostazioni personalizzate del nodo** nodo.  
  
4.  selezionato **ExplorerNodeSettings**quindi  **proprietà** finestra, impostare  **classe** in  **commento**.  
  
5.  Fare clic con il pulsante destro del mouse **commento** il nodo e quindi fare clic su  **Aggiungere il nuovo percorso di proprietà**.  
  
     Un nuovo nodo viene visualizzato denominato **Proprietà di**.  
  
6.  selezionato **Proprietà di**quindi  **proprietà** la finestra, fare clic sul campo del valore di  **Percorso della proprietà**.  selezionato **commento**, quindi  **CommentReferencesSubject**, quindi  **Elemento del flusso**.  Il percorso risultante sarà simile a **CommentReferencesSubject.Subject\/\! oggetto**.  
  
7.  Nel campo del valore di **proprietà**selezionare,  **nome**.  
  
8.  Trasformazione di tutti i modelli e quindi compilare ed eseguire la soluzione.  
  
9. Nella finestra di progettazione generata, aprire il diagramma di esempio.  
  
10. Creare un elemento **connettore di commento** tra l'elemento di commento e  **Attività1** elemento del diagramma.  
  
     Il nodo di esplorazione comparirà il commento come **Attività1**.  
  
## Nascondere nodi  
 È possibile nascondere un nodo nell'esploratore aggiungendo il relativo percorso a **nodi nascosti** nodo per  **DSL Esplora Risorse**.  Nella procedura riportata di seguito viene illustrato come nascondere nodi di commento.  
  
#### Per nascondere un nodo di esplorazione  
  
1.  Aprire la soluzione creata nella procedura precedente.  
  
2.  in **DSL Esplora Risorse**, fare clic con il pulsante destro del mouse  **Comportamento di visualizzazione** quindi scegliere  **Aggiungere il nuovo percorso del dominio**.  
  
     In **Percorso del dominio** il nodo viene visualizzato sotto  **nodi nascosti**.  
  
3.  selezionato **Percorso del dominio**quindi  **proprietà** la finestra, fare clic sul campo del valore di  **definizione di percorso**.  selezionato **FlowGraph**, quindi  **FlowGraphHasComments**.  Il percorso risultante sarà simile a **FlowGraphHasComments.Comments**  
  
4.  Trasformazione di tutti i modelli e quindi compilare ed eseguire la soluzione.  
  
5.  Nella finestra di progettazione generata, aprire il diagramma di esempio.  
  
     In esplora modelli scegliere da deve mostrare solo **attori** il nodo e non deve mostrare  **Commenti** nodo.  
  
## Vedere anche  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/it-it/ca5e84cb-a315-465c-be24-76aa3df276aa)