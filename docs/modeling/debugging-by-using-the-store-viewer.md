---
title: "Esecuzione del debug utilizzando il Visualizzatore di archivio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, archivio"
  - "Linguaggio specifico di dominio, visualizzatore di archivio"
ms.assetid: 0178db2e-ae99-4ed3-9b87-8620fa9fa8e4
caps.latest.revision: 17
caps.handback.revision: 17
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Esecuzione del debug utilizzando il Visualizzatore di archivio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Con il visualizzatore dell'archivio, è possibile esaminare lo stato di un oggetto archivio utilizzato da [!INCLUDE[dsl](../modeling/includes/dsl_md.md)].  Il visualizzatore dell'archivio visualizzare tutti gli elementi del modello di dominio in un archivio specifico, con le proprietà degli elementi e i collegamenti tra elementi.  
  
## Aprire il visualizzatore dell'archivio  
 Quando si esegue [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] la compilazione sperimentale, impedisce l'esecuzione di codice in un punto di interruzione in cui un'istanza dell'archivio contiene le informazioni sul modello. Quindi, aprire il visualizzatore dell'archivio digitando il comando seguente in  **immediato** finestra:  
  
```  
Microsoft.VisualStudio.Modeling.Diagnostics.StoreViewer.Show(mystore);  
```  
  
> [!NOTE]
>  È necessario sostituire `mystore` con il nome dell'istanza dell'archivio.  Inoltre, se si aggiunge lo spazio dei nomi al codice, è possibile digitare il comando per visualizzare il visualizzatore dell'archivio senza lo spazio dei nomi completo:  
>   
>  `using Microsoft.VisualStudio.Modeling.Diagnostics;`  
>   
>  `…`  
>   
>  `StoreViewer.Show(mystore);`  
  
 Il metodo `Show` dispone di diversi overload.  È possibile specificare un'istanza di un archivio o una partizione come parametro.  
  
 In alternativa, è possibile inserire la riga di codice in cui viene visualizzato il visualizzatore dell'archivio in qualsiasi punto del codice in cui il parametro passato a `Show` il metodo è sotto.  Questa azione consente di visualizzare il visualizzatore dell'archivio quando la riga di codice viene eseguito come snapshot del contenuto dell'archivio.  
  
### Utilizzando il visualizzatore dell'archivio  
 Quando il visualizzatore dell'archivio è aperto, una finestra non modale di Windows Form, come illustrato nella figura seguente.  
  
 ![](../modeling/media/storeviewer2.png "storeviewer2")  
Visualizzatore dell'archivio  
  
 Il visualizzatore dell'archivio dispone di tre riquadri: il riquadro sinistro, nel riquadro di destra superiore e inferiore del riquadro.  Il riquadro sinistro è una visualizzazione struttura ad albero dei tipi in `DomainDataDirectory` membro di un archivio.  Se si espande il nodo della partizione e si fa clic su un elemento, le proprietà dell'elemento verranno visualizzate nel riquadro di destra superiore.  Se l'elemento è collegato ad altri elementi, gli elementi aggiuntivi vengono visualizzati nel riquadro inferiore destro.  Se si fa doppio clic su un elemento nell'angolo inferiore destro riquadro, l'elemento verrà evidenziato nel riquadro sinistro.  
  
## Vedere anche  
 [Esplorazione e aggiornamento di un modello nel codice del programma](../modeling/navigating-and-updating-a-model-in-program-code.md)