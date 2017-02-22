---
title: "Propriet&#224; di diagrammi | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.dsltools.dsldesigner.dsldiagram"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, diagramma"
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: 25
caps.handback.revision: 25
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Propriet&#224; di diagrammi
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile impostare le proprietà che specificano come i diagrammi verranno visualizzate nella finestra di progettazione generata un'eccezione.  Ad esempio, è possibile specificare un colore predefinito per il testo nel diagramma.  
  
 Per ulteriori informazioni, vedere [Procedura: definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md).  per ulteriori informazioni su come utilizzare queste proprietà, vedere [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Nella tabella seguente sono elencate le proprietà dei diagrammi.  
  
|Proprietà|Descrizione|Predefinito|  
|---------------|-----------------|-----------------|  
|colore di riempimento|il colore di riempimento per il diagramma.|Bianco|  
|Colore del testo|Il colore del testo visualizzato nel diagramma.|Black|  
|Modificatore Accesso|Il modificatore di accesso della classe \(pubblico o interno\).|Public|  
|Attributi personalizzati|Utilizzato per aggiungere attributi a quello generato mediante la classe.|\<nessuno\>|  
|genera il doppio derivato|se `True`, una classe base in una classe parziale \(per supportare la personalizzazione da un override\) vengono generate.  Per ulteriori informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Un costruttore personalizzato|se `True`, un costruttore personalizzato viene fornito nel codice sorgente.  Per ulteriori informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificatore di ereditarietà|Viene descritto il tipo di ereditarietà delle classi di codice sorgente che viene generata dal diagramma \(`none`,  `abstract` o  `sealed`\).|Nessuno|  
|Schema di base|La classe base del diagramma.|\(nessuno\)|  
|Nome|Il nome del diagramma.|nome corrente|  
|Spazio dei nomi|Lo spazio dei nomi a cui affiliato con questo diagramma.|Spazio dei nomi corrente|  
|classe rappresentata|La classe di dominio radice che questo diagramma rappresenta.|classe radice corrente se applicabile|  
|Note|Note informali associate a questo elemento.|\<nessuno\>|  
|colore di riempimento di esposti come proprietà|se `True`, l'utente può impostare il colore di riempimento del diagramma della finestra di progettazione generata un'eccezione.  Per impostare scopo, fare clic con il pulsante destro del mouse sulla forma del diagramma e scegliere **aggiungere Explosed**.|False|  
|Colore del testo di esposti come proprietà|se `True`, l'utente può impostare il colore del testo del diagramma nella finestra di progettazione generata un'eccezione.  Per impostare scopo, fare clic con il pulsante destro del mouse sulla forma del diagramma e scegliere **aggiungere Explosed**.|False|  
|Descrizione|La descrizione utilizzata per documentare la finestra di progettazione generata un'eccezione.|\<nessuno\>|  
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generata per questo diagramma.|\<nessuno\>|  
|Parola chiave della Guida|La parola chiave utilizzata per indicizzare la Guida di questo diagramma.|\<nessuno\>|  
  
## Vedere anche  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/it-it/ca5e84cb-a315-465c-be24-76aa3df276aa)