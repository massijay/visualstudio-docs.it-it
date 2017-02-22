---
title: "Propriet&#224; delle classi di dominio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, classe di dominio"
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: 21
caps.handback.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Propriet&#224; delle classi di dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le classi di dominio hanno le proprietà nella tabella seguente.  Per informazioni sulle classi di dominio, vedere [Informazioni su modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md).  per ulteriori informazioni su come utilizzare queste proprietà, vedere [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Proprietà|Descrizione|Predefinito|  
|---------------|-----------------|-----------------|  
|Modificatore Accesso|Il livello di accesso della classe di dominio \(`public` o  `internal`\).|`public`|  
|Attributi personalizzati|Utilizzato per aggiungere attributi al codice sorgente classe generata dalla classe di dominio.|\<nessuno\>|  
|genera il doppio derivato|se `True`, una classe base in una classe parziale \(per supportare la personalizzazione da un override\) vengono generate.  Per ulteriori informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Un costruttore personalizzato|se `True`, un costruttore personalizzato viene fornito nel codice sorgente.  Per ulteriori informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modificatore di ereditarietà|Viene descritto il tipo di ereditarietà delle classi di codice sorgente che viene generata dalla classe di dominio \(`none`,  `abstract` o  `sealed`\).|`none`|  
|Classe base|Se questa classe di dominio è derivata da, il nome della classe base.|\<nessuno\>|  
|Nome|il nome di questa classe di dominio.|nome corrente|  
|Spazio dei nomi|Lo spazio dei nomi della classe di dominio.|Spazio dei nomi corrente|  
|Note|Note informali associate a questa classe di dominio.|\<nessuno\>|  
|Descrizione|La descrizione utilizzata per documentare l'interfaccia utente della finestra di progettazione generata un'eccezione.|\<nessuno\>|  
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generata per questa classe di dominio.|\<nessuno\>|  
|Parola chiave della Guida|La parola chiave facoltativa utilizzata per indicizzare la Guida di questa classe di dominio.|\<nessuno\>|  
  
## Vedere anche  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/it-it/ca5e84cb-a315-465c-be24-76aa3df276aa)