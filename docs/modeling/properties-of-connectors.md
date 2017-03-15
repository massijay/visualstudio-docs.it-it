---
title: "Propriet&#224; dei connettori | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, connettori"
ms.assetid: b1f24e8d-cdd7-4a5d-af37-1038f43b45c7
caps.latest.revision: 21
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 21
---
# Propriet&#224; dei connettori
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

I connettori rappresentano le relazioni di dominio in una finestra di progettazione generata un'eccezione.  
  
 Per ulteriori informazioni, vedere [Procedura: definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md).  per ulteriori informazioni su come utilizzare queste proprietà, vedere [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 I connettori delle proprietà elencate nella tabella seguente.  
  
|Proprietà|Descrizione|Predefinito|  
|---------------|-----------------|-----------------|  
|Colore|Il colore del connettore.|Black|  
|Stile del tratteggio|Lo stile del tratteggio per la riga per il connettore \(a tinta unita, trattino, un punto, DashDot, DashDotDot, o personalizza\).|Tinta unita|  
|Stile di entità finale di origine|Lo stile dell'entità finale di origine per il connettore \(HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond, o nessuno\).|Nessuno|  
|Stile di entità finale di destinazione|Lo stile dell'entità finale di destinazione per il connettore \(HollowArrow, EmptyArrow, FilledArrow, EmptyDiamond, FilledDiamond, o nessuno\).|Nessuno|  
|Colore del testo|Il colore utilizzato per gli elementi Decorator di testo associate al connettore.|Black|  
|Thickness|Lo spessore di linea per il connettore, misurata nei pollici.|0.03125|  
|Modificatore Accesso|Il livello di accesso della classe \(`public` o  `internal`\).|Public|  
|Attributi personalizzati|Utilizzato per aggiungere attributi al codice sorgente classe generata dal connettore.|\<nessuno\>|  
|genera il doppio derivato|se `True`, una classe base in una classe parziale \(per supportare la personalizzazione da un override\) vengono generate.  Per ulteriori informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Un costruttore personalizzato|se `True`, un costruttore personalizzato viene fornito nel codice sorgente.  Per ulteriori informazioni, vedere [Override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Modificatore di ereditarietà|Viene descritto il tipo di ereditarietà delle classi di codice sorgente che viene generata dal connettore \(`none`,  `abstract` o  `sealed`\).|nessuno|  
|connettore di base|La classe base del connettore.|\(nessuno\)|  
|Nome|Il nome del connettore.|nome corrente|  
|Spazio dei nomi|Lo spazio dei nomi a cui affiliato con il connettore.|Spazio dei nomi corrente|  
|tipo di descrizione comando|La descrizione comando è definita \(corretto, variabile, o nessuno\).  Se corretto, quindi il valore di `Fixed Tooltip Text` la proprietà viene utilizzata la descrizione comando; se la variabile, la descrizione comando è definita nel codice personalizzato.|\<nessuno\>|  
|Note|Note informali associate al connettore.|\<nessuno\>|  
|stile di routing|Lo stile utilizzato per indirizzare il connettore.  In `Rectilinear` il connettore vengono disattiva retti come obbligatorio, in  `Straight` il connettore contrario.|rettilineo|  
|colore esposto come proprietà<br /><br /> Stile del tratteggio esposto come proprietà<br /><br /> spessore esposto come proprietà<br /><br /> Colore del testo di esposti|se `True`, l'utente può impostare la proprietà illustrata di una forma.  Per impostare scopo, fare clic con il pulsante destro del mouse sulla definizione della forma e fare clic su **aggiungere esposto**.|False|  
|Descrizione|Utilizzato per documentare la finestra di progettazione generata un'eccezione.|\<nessuno\>|  
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generata per il connettore.|\<nessuno\>|  
|testo fisso di descrizione comando|Il testo utilizzato per una descrizione comando fissa.|\<nessuno\>|  
|Parola chiave della Guida|La parola chiave utilizzata per indicizzare la Guida di questo elemento.|\<nessuno\>|  
  
## Vedere anche  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/it-it/ca5e84cb-a315-465c-be24-76aa3df276aa)