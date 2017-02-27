---
title: "Utilizzo del diagramma di definizione DSL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.diagram"
  - "vs.dsltools.dsldesigner.dsldiagram"
helpviewer_keywords: 
  - "Strumenti del linguaggio specifico di dominio, Bring Tree Here"
  - "Strumenti del linguaggio specifico di dominio, diagramma"
  - "Strumenti del linguaggio specifico di dominio, Show As Class"
  - "Strumenti del linguaggio specifico di dominio, Show Map Lines"
  - "Strumenti del linguaggio specifico di dominio, Split Tree"
ms.assetid: 1a4c7a58-e134-438e-848e-efd98f92bf10
caps.latest.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 21
---
# Utilizzo del diagramma di definizione DSL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Il diagramma di una definizione di [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] è uno strumento importante per la definizione del linguaggio specifico di dominio \(DSL\).  Consente di aggiungere elementi al modello di dominio e definire relazioni sul diagramma ed è possibile modificare il layout del diagramma per renderlo più leggibile.  
  
## Layout del diagramma  
 Il diagramma della definizione di [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] è costituito da due partizioni, la partizione **Classes and Relationships** e la partizione **Diagram Elements**.  Nella partizione **Classes and Relationships** sono visualizzate classi di dominio, relazioni di dominio ed ereditarietà. Nella partizione **Diagram Elements** sono visualizzate classi di forma, classi di connettore, classi di corsia e il diagramma della finestra di progettazione generato.  
  
 Le classi di dominio possono essere visualizzate in più posizioni all'interno delle partizioni **Classes and Relationships**.  In una definizione di classe di dominio viene visualizzato un albero di ereditarietà se si tratta della classe di base per altre classi di dominio e un albero delle relazioni se si tratta dell'origine delle relazioni di incorporamento o riferimento.  I segnaposto delle classi di dominio vengono visualizzati come le destinazioni delle relazioni di incorporamento o riferimento.  Per impostazione predefinita, gli elementi segnaposto sono visualizzati con il raggruppamento **Domain Properties** compresso.  Per questi elementi, non vengono mostrati l'ereditarietà o le relazioni di incorporamento o riferimento.  
  
 Quando si aggiunge una classe di dominio, questa viene visualizzata nella parte inferiore della partizione **Classes and Relationships**.  Quando si aggiunge una relazione di incorporamento o riferimento, questa viene posizionata a destra sotto la classe di dominio di origine.  
  
 Man mano che si aggiungono classi e relazioni di dominio, può risultare difficile individuare una classe di dominio specifica.  Per trovare una classe di dominio, fare clic con il pulsante destro del mouse su di essa in **DSL Explorer** e scegliere **Locate in Diagram**.  
  
 Nelle sezioni seguenti viene descritto come modificare l'aspetto del diagramma per renderlo più leggibile.  
  
## Copia di elementi  
 È possibile usare i comandi Copia, Taglia e Incolla sugli elementi nel diagramma della definizione DSL.  
  
## Zoom avanti o indietro sul diagramma  
 È possibile eseguire lo zoom avanti o indietro sul diagramma usando la barra degli strumenti di **DSL Designer** per impostare il livello di zoom.  
  
## Nascondere linee mappa  
 Le linee mappa sono linee tracciate tra una classe di dominio o una relazione di dominio e la forma o il connettore a cui è mappata.  È possibile nascondere le linee mappa facendo clic sul pulsante **Show Map Lines** sulla barra degli strumenti di **DSL Designer**.  Per visualizzare le linee, fare di nuovo clic sul pulsante.  
  
## Modifica del layout del diagramma  
 È possibile modificare il layout della partizione **Classes and Relationships** come indicato di seguito.  
  
### Expand\/Collapse  
 Per ridurre le dimensioni di un elemento forma di raggruppamento che rappresenta una classe di dominio o una forma fare clic con il pulsante destro del mouse su di esso e quindi scegliere **Collapse**.  Il raggruppamento **Domain Properties** della forma verrà nascosto.  Per visualizzare di nuovo il raggruppamento **Domain Properties**, fare clic con il pulsante destro del mouse sulla forma e scegliere **Expand**.  
  
### Move Up\/Move Down  
 Per spostare una classe di dominio o un elemento del diagramma verso l'alto o verso il basso nella partizione, fare clic con il pulsante destro del mouse sull'elemento e quindi scegliere **Move Up** o **Move Down**.  Se si sposta un elemento segnaposto visualizzato come destinazione di una relazione di incorporamento o riferimento, la relazione verrà spostata insieme all'elemento.  
  
### Expand\/Collapse Relationships Tree  
 Se una classe di dominio riveste il ruolo di origine in relazioni di incorporamento o riferimento con altre classi di dominio, per nascondere le relazioni fare clic con il pulsante destro del mouse sulla definizione della classe di dominio e quindi scegliere **Collapse Relationships Tree**.  Per visualizzare le relazioni, fare clic sull'elemento della definizione e quindi su **Expand Relationships Tree**.  
  
### Expand\/Collapse Inheritance Tree  
 Se una classe di dominio rappresenta la classe di base per altre classi di dominio, per nascondere l'albero di ereditarietà fare clic con il pulsante destro del mouse sulla definizione della classe di dominio e quindi scegliere **Collapse Inheritance Tree**.  Per visualizzare l'albero di ereditarietà, fare clic sull'elemento della definizione e quindi su **Expand Inheritance Tree**.  
  
### Bring Tree Here  
 Per consolidare il diagramma, fare clic con il pulsante destro del mouse su una classe di dominio segnaposto e quindi scegliere **Bring Tree Here**.  La classe di dominio segnaposto diventa un elemento della definizione e visualizza gli alberi di ereditarietà e delle relazioni.  L'elemento della definizione precedente diventa un elemento segnaposto se costituisce la destinazione di una relazione o l'elemento figlio in una relazione di ereditarietà; in caso contrario, non viene più visualizzato.  
  
### Split Tree  
 Per suddividere gli alberi di ereditarietà o delle relazioni, fare clic con il pulsante destro del mouse sulla definizione della classe di dominio in cui sono visualizzati e quindi scegliere **Split Tree**.  L'elemento della definizione diventa un elemento segnaposto e la classe di dominio della definizione, insieme ai relativi alberi di ereditarietà e delle relazioni, è ora visualizzata nella parte inferiore della partizione.  
  
### Show As Class  
 Se una relazione di dominio ha relazioni derivate o se ha relazioni di incorporamento o riferimento con altre relazioni di dominio, è possibile visualizzare la relazione come una classe. A questo scopo, fare clic con il pulsante destro del mouse sulla relazione e quindi scegliere **Show As Class**.  La relazione verrà visualizzata con un raggruppamento **Domain Properties** e mostrerà gli alberi di ereditarietà e delle relazioni.  
  
## Vedere anche  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/it-it/ca5e84cb-a315-465c-be24-76aa3df276aa)