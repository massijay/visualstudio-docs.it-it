---
title: "Propriet&#224; delle corsie | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.swimlane"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, corsia"
ms.assetid: 47edbc2d-09e4-48ac-b4d1-5268a06a27e6
caps.latest.revision: 24
caps.handback.revision: 24
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Propriet&#224; delle corsie
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile aggiungere corsie a un diagramma.  La divisione fra di Corsie un diagramma in aree verticale o orizzontale.  È possibile definire altre forme da visualizzare in corsie.  Per ulteriori informazioni, vedere [Procedura: definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md).  per ulteriori informazioni su come utilizzare queste proprietà, vedere [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Corsie dispone delle proprietà elencate nella tabella seguente.  
  
|Proprietà|Descrizione|Predefinito|  
|---------------|-----------------|-----------------|  
|Colore di riempimento del corpo|Il colore di riempimento per il corpo di corsia.|Bianco|  
|Colore di riempimento di intestazione|Il colore di riempimento per l'intestazione di corsia.|grigio scuro|  
|Colore del separatore|Il colore delle linee di separazione.|grigio chiaro|  
|Stile della linea di separazione|Lo stile della linea di separazione \(`Solid`,  `Dash`,  `Dot`,  `DashDot`,  `DashDotDot`, o  `Custom`\).|`Dash`|  
|Spessore del separatore|Lo spessore di linea di separazione nei pollici.|0.03125|  
|Colore del testo|Il colore utilizzato per gli elementi Decorator di testo che sono associati a questo corsia.|Black|  
|Modificatore Accesso|Il livello di accesso della classe \(`public` o  `internal`\).|Public|  
|Attributi personalizzati|Utilizzato per aggiungere attributi al codice venga generato da questo corsia.|\<nessuno\>|  
|genera il doppio derivato|se `True`, una classe base in una classe parziale \(per supportare la personalizzazione da un override\) vengono generate.  Per ulteriori informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Un costruttore personalizzato|se `True`, un costruttore personalizzato viene fornito nel codice sorgente.  Per ulteriori informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificatore di ereditarietà|Viene descritto il tipo di ereditarietà delle classi di codice sorgente che viene generata da corsia \(`none`,  `abstract` o  `sealed`\).|nessuno|  
|Basare Corsia|La classe base del corsia.|\(nessuno\)|  
|Nome|Il nome di questo corsia.|nome corrente|  
|Spazio dei nomi|Lo spazio dei nomi a cui affiliato con questo corsia.|Spazio dei nomi corrente|  
|tipo di descrizione comando|La descrizione comando è definita \(`fixed`,  `variable`, o  `none`\).  se `fixed`, quindi il valore di  `Fixed Tooltip Text` la proprietà viene utilizzata; se  `variable`, la descrizione comando è definita nel codice personalizzato.|\<nessuno\>|  
|Note|Note informali associate a questo corsia.|\<nessuno\>|  
|Allineamento|allineamento orizzontale o verticale.|Verticale|  
|altezza iniziale|L'altezza iniziale di questo corsia, nei pollici.  Applicabile solo agli corsie orizzontali.|0|  
|larghezza iniziale|La larghezza iniziale di questo corsia, nei pollici.  Applicabile solo agli corsie verticali.|0|  
|Colore del testo di esposti|se `True`, l'utente può impostare il colore di uno corsia nella finestra di progettazione generata un'eccezione.  Per impostare scopo, fare clic con il pulsante destro del mouse sulla forma di corsia e fare clic su **aggiungere esposto**.|False|  
|Descrizione|Utilizzato per documentare la finestra di progettazione generata un'eccezione.|\<nessuno\>|  
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generata per fare riferimento a questa classe di corsia.|\<nessuno\>|  
|testo fisso di descrizione comando|Il testo utilizzato per una descrizione comando fissa.|\<nessuno\>|  
|Parola chiave della Guida|La parola chiave utilizzata per indicizzare la Guida di questo corsia.|\<nessuno\>|  
  
## Vedere anche  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/it-it/ca5e84cb-a315-465c-be24-76aa3df276aa)