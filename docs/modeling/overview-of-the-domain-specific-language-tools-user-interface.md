---
title: "Informazioni sull&#39;interfaccia utente degli strumenti di linguaggio specifico di dominio | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.editor"
helpviewer_keywords: 
  - "Strumenti del linguaggio specifico di dominio, interfaccia utente"
ms.assetid: 81ae6b35-6819-41d0-953b-6b4ed81f9227
caps.latest.revision: 25
caps.handback.revision: 25
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Informazioni sull&#39;interfaccia utente degli strumenti di linguaggio specifico di dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

La prima volta che si apre una soluzione degli strumenti di linguaggio specifico di dominio \(strumenti DSL\) in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], l'interfaccia utente sarà simile all'immagine seguente.  
  
 ![Progettazione DSL](../modeling/media/dsl_designer.png "dsl\_designer")  
  
 Nella tabella seguente viene spiegato come le parti dell'interfaccia utente vengono utilizzate.  
  
|**Elemento**|**Definizione**|  
|------------------|---------------------|  
|Diagramma|Il diagramma viene visualizzato il modello di dominio.<br /><br /> Il diagramma dispone di due lati.  Un lato definisce i tipi di elementi dei modelli.  L'altro lato definisce come i modelli visualizzati sullo schermo.|  
|Casella degli strumenti|Trascinare gli strumenti dalla casella degli strumenti per aggiungere classi di dominio e i tipi di forme del diagramma.  Per aggiungere le relazioni, connettori e mapping di forma, fare clic sullo strumento, quindi fare clic sul nodo di origine nel diagramma e quindi il nodo di destinazione.|  
|DSL Esplora Risorse|**DSL Esplora Risorse** viene visualizzato quando una definizione di modello DSL è la finestra attiva.  Indica il linguaggio DSL struttura ad albero.  Il modello DSL Esplora Risorse consente di modificare le funzionalità del modello che non vengono visualizzate nel diagramma.  Ad esempio, è possibile aggiungere gli elementi della casella degli strumenti e l'opzione nel processo di convalida utilizzando **DSL Esplora Risorse**.|  
|Il modello DSL la finestra dettagli|**Dettagli DSL** nella finestra vengono visualizzate le proprietà degli elementi del modello di dominio che consentono di controllare la modalità di visualizzazione degli elementi e come gli elementi vengono copiati ed eliminate.<br /><br /> -   per impostazione predefinita, **Dettagli DSL** la finestra viene visualizzato accanto a  **Elenco errori** e  **output** windows.|  
  
## Il diagramma del modello di dominio  
 Il diagramma del modello di dominio in due parti.  Un lato del diagramma mostra gli elementi e le relazioni nel modello.  Nell'altro lato del modello deve essere visualizzati e include le forme utilizzate per visualizzare gli elementi e le proprietà del diagramma di modello.  Nell'immagine seguente vengono mostrati gli elementi del diagramma.  
  
 ![Progettazione DSL con corsia](../modeling/media/dsl_desinger.png "dsl\_desinger")  
  
 Nella tabella seguente vengono descritti alcuni degli elementi del diagramma del modello di dominio.  
  
|**Termine**|**Definizione**|  
|-----------------|---------------------|  
|classe di dominio|Le classi di dominio sono tipi di elementi dei modelli.<br /><br /> Una classe di dominio può essere presente più volte in un diagramma, se è la destinazione di più di una relazione.<br /><br /> Per aggiungere una classe di dominio, trascinare lo strumento classi di dominio da **Casella degli strumenti** in  **classi e relazioni** lato del diagramma.|  
|relazione di dominio|Relazioni di dominio sono tipi di collegamenti tra elementi dei modelli.<br /><br /> *incorporare relazione* indica che l'elemento di destinazione è di proprietà o contenuto dall'elemento di origine e viene visualizzato come una linea continua.  Ogni elemento in un modello deve essere la destinazione di una relazione che utilizza, in modo che i form di modello una struttura ad albero.  In *relazione di riferimento* indica un collegamento generale tra elementi del modello e viene visualizzato come una linea tratteggiata.  Qualsiasi elemento può contenere qualsiasi numero di collegamenti di riferimento.<br /><br /> Creare una relazione facendo clic sullo strumento su **Casella degli strumenti**a tale scopo, fare clic sulla classe di dominio di origine e scegliere la classe di destinazione.|  
|Forme e i connettori|Le forme specificano come elementi del modello devono essere visualizzato in un diagramma DSL., connettori specificano le righe in un diagramma DSL che può essere utilizzato per visualizzare relazioni.<br /><br /> Per creare una forma o un connettore, trascinare lo strumento a **Elementi del diagramma** lato del diagramma.|  
|Mapping di forme|Una mappa di formato viene visualizzato come una linea nel diagramma del modello di dominio, collegante una forma alla classe di dominio visualizzato, o un connettore alla relazione di dominio visualizzati.|  
  
## Vedere anche  
 [Informazioni generali sugli strumenti di linguaggio specifico di dominio](../modeling/overview-of-domain-specific-language-tools.md)   
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/it-it/ca5e84cb-a315-465c-be24-76aa3df276aa)   
 [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md)