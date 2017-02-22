---
title: "Propriet&#224; delle forme di raggruppamento | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.compartmentshape"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, forma di raggruppamento"
ms.assetid: 9a9e112d-210d-413b-a44f-0e976a4a78bc
caps.latest.revision: 24
caps.handback.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Propriet&#224; delle forme di raggruppamento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le forme del raggruppamento è una delle forme che è possibile utilizzare per visualizzare una classe di dominio in un linguaggio specifico di dominio.  È possibile espandere e comprimere i raggruppamenti.  
  
 Per ulteriori informazioni, vedere [Procedura: definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md).  per ulteriori informazioni su come utilizzare queste proprietà, vedere [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Le forme di raggruppamento includono le proprietà elencate nella tabella seguente.  
  
|Proprietà|Descrizione|Predefinito|  
|---------------|-----------------|-----------------|  
|L'impostazione predefinita di espandere lo stato di compressione|se `Expanded`, i raggruppamenti sono indicati alla creazione.  se `Collapsed`, non lo sono.|Espanso|  
|colore di riempimento|Il colore di riempimento della forma.|Bianco|  
|Modalità di riempimento sfumato|La modalità di sfumatura riempimento della forma.|Horizontal|  
|Geometry|La geometria della forma \(rettangolo o rettangolo arrotondato\).|Rectangle|  
|Presenta punti di connessione predefiniti|se `True`, la forma utilizzerà superiore, inferiore, sinistro e i margini destro punti di connessione nella finestra di progettazione generata un'eccezione.|False|  
|È la stessa intestazione del raggruppamento visibile|se `False`e la forma ha un singolo raggruppamento, l'intestazione del raggruppamento non è visibile.|True|  
|Colore del contorno|Il colore della struttura della forma.|Black|  
|Stile del tratteggio della struttura|Lo stile del tratteggio della struttura della forma \(a tinta unita, trattino, un punto, DashDot, DashDotDot, personalizza\).|Tinta unita|  
|descrivere lo spessore|Lo spessore della struttura della forma.|0.03125|  
|Colore del testo|Il colore utilizzato per gli elementi Decorator di testo che sono associati alla forma.|Black|  
|Modificatore Accesso|Il livello di accesso della forma del raggruppamento \(`public` o  `internal`\).|Public|  
|Attributi personalizzati|Utilizzato per aggiungere attributi al codice sorgente venga generato da questa forma di raggruppamento|\<nessuno\>|  
|genera il doppio derivato|se `True`, una classe base in una classe parziale \(per supportare la personalizzazione da un override\) vengono generate.  Per ulteriori informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Un costruttore personalizzato|se `True`, un costruttore personalizzato viene fornito nel codice sorgente.  Per ulteriori informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificatore di ereditarietà|Viene descritto il tipo di ereditarietà delle classi di codice sorgente generata dalla forma di raggruppamento \(`none`,  `abstract` o  `sealed`\).|Nessuno|  
|Forma di base del raggruppamento|La classe base della forma.|\(nessuno\)|  
|Nome|Il nome della forma.|nome corrente|  
|Spazio dei nomi|Lo spazio dei nomi a cui affiliato con la forma.|Spazio dei nomi corrente|  
|tipo di descrizione comando|La descrizione comando è definita \(corretto, variabile, o nessuno\).  Se corretto, quindi il valore di `Fixed Tooltip Text` la proprietà viene utilizzata la descrizione comando; se la variabile, la descrizione comando è definita nel codice personalizzato.|nessuno|  
|Note|Note informali associate alla forma.|\<nessuno\>|  
|altezza iniziale|L'altezza iniziale della forma, nei pollici.  Per le forme di raggruppamento, si tratta dell'altezza della sezione di intestazione solo e non può essere ridimensionato.|1|  
|larghezza iniziale|La larghezza iniziale della forma, nei pollici.|1.5|  
|colore di riempimento esposto come proprietà<br /><br /> Modalità esposte di sfumatura riempimento<br /><br /> Colore esposto della struttura come proprietà<br /><br /> Stile del tratteggio esposto della struttura come proprietà<br /><br /> Spessore esposto dalla struttura come proprietà<br /><br /> Colore del testo di esposti|se `True`, l'utente può impostare la proprietà illustrata di una forma.  Per impostare scopo, fare clic con il pulsante destro del mouse sulla definizione della forma e fare clic su **aggiungere esposto**.|False|  
|Descrizione|Utilizzato per documentare la finestra di progettazione generata un'eccezione.|\<nessuno\>|  
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generata per la forma.|\<nessuno\>|  
|testo fisso di descrizione comando|Il testo utilizzato per una descrizione comando fissa.|\<nessuno\>|  
|Parola chiave della Guida|La parola chiave utilizzata per indicizzare la Guida della forma.|\<nessuno\>|  
  
## Vedere anche  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/it-it/ca5e84cb-a315-465c-be24-76aa3df276aa)