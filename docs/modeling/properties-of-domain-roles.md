---
title: "Propriet&#224; dei ruoli di dominio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5a7bb18c-638e-45e8-9d79-9aa6a9e14b0e
caps.latest.revision: 9
caps.handback.revision: 9
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Propriet&#224; dei ruoli di dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le proprietà nella seguente tabella sono associate a un ruolo di dominio.  Per informazioni sui ruoli di dominio, vedere [Informazioni su modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md).  per ulteriori informazioni su come utilizzare queste proprietà, vedere [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Proprietà|Descrizione|Predefinito|  
|---------------|-----------------|-----------------|  
|tipo di raccolta|Se questo ruolo contiene molteplicità di 0. \* o 1. \*, questa proprietà consente di personalizzare il tipo generico utilizzato per archiviare la raccolta di collegamenti.|`(none)`\-  <xref:Microsoft.VisualStudio.Modeling.LinkedElementCollection%601> viene utilizzato|  
|Attributi personalizzati|Gli attributi specificati qui verranno aggiunti come attributi alla classe del codice generato.|\<nessuno\>|  
|È la proprietà visualizzabile|se `True`e se la molteplicità della relazione è 0..1 o 1..1, il ruolo della proprietà può essere visualizzato dall'utente in  **proprietà** finestra.  La proprietà viene visualizzato il nome dell'elemento all'altra estremità del collegamento della relazione.|`True`|  
|È il generatore della proprietà|se `True`, un ruolo della proprietà viene generato per il ruolo, che è possibile utilizzare per scorrere la relazione nel codice programma.  Se si imposta questo caso, è possibile utilizzare la relazione in modo meno efficiente utilizzando i metodi statici della relazione di dominio.|`True`|  
|Modificatore di accesso del metodo Get della proprietà|Il modificatore di accesso per il richiamo per la proprietà generata \(`public`,  `internal`,  `private`,  `protected`, o  `protected internal`\).|`public`|  
|Modificatore di accesso del metodo di impostazione delle proprietà|il modificatore di accesso per la funzione Set per la proprietà generata \(`public`,  `internal`,  `private`,  `protected`, o  `protected internal`\).|`public`|  
|Molteplicità|Il numero di elementi del modello che svolgono il ruolo opposto \(`0..1`,  `1..1`,  `0..*`, o  `1..*`\).  se la molteplicità è `0..*` o  `1..*`, la proprietà generata rappresenta una raccolta; in caso contrario, la proprietà generata rappresenta un singolo elemento del modello.|Dipende dal tipo di relazione e se questo è l'origine o il ruolo della relazione.|  
|Nome|Il nome del ruolo del dominio.  Questa proprietà non può contenere uno spazio vuoto.|Il nome della classe di dominio del giocatore di ruolo per il ruolo.|  
|copia di propagazioni|`DoNotPropagateCopy` \- Il giocatore di ruolo copiato non avrà copia del collegamento.<br /><br /> `PropagateCopyToLinkOnly` \- I punti copiati del collegamento a un oggetto esistente opposto al giocatore di ruolo.<br /><br /> `PropagateCopyToLinkAndOppositeRolePlayer`\- I punti copiati a una copia del giocatore di ruolo opposto.|`PropagateCopyToLinkAndOppositeRolePlayer` per i ruoli di origine dei precedenti.<br /><br /> `DoNotPropagateCopy` per altri ruoli.<br /><br /> Per ulteriori informazioni, vedere [Personalizzazione del comportamento di copia](../modeling/customizing-copy-behavior.md).|  
|Eliminazione di propagazioni|`True` per eliminare l'elemento che causa questo ruolo quando il collegamento associato viene eliminato.|`True` per la destinazione di un ruolo che utilizza.<br /><br /> `False` per altri ruoli.<br /><br /> Per ulteriori informazioni, vedere [Personalizzazione del comportamento di eliminazione](../modeling/customizing-deletion-behavior.md).|  
|Nome proprietà|Il nome della proprietà generata dal codice del giocatore di ruolo.  Questo nome non può contenere uno spazio vuoto.|Il nome del ruolo opposto se questo ruolo contiene a zero\-a\-u'o di una molteplicità uno\-a\-uno; in caso contrario, il nome pluralizzato del ruolo opposto.|  
|giocatore di ruolo|La classe di dominio dell'elemento che può fornire questo ruolo nella relazione.  Questa proprietà è in sola lettura.|La classe di dominio del giocatore di ruolo per il ruolo.|  
|Note|Note informali associate al ruolo del dominio.|\<nessuno\>|  
|Categoria|La categoria in cui la proprietà generata viene visualizzato in **proprietà** finestra nella finestra di progettazione generata un'eccezione.  Se questa proprietà è vuota, la proprietà generata viene visualizzata sotto **Varie** categoria|\<nessuno\>|  
|Descrizione|La descrizione utilizzata per documentare il codice e viene utilizzata nell'interfaccia utente della finestra di progettazione generata un'eccezione.<br /><br /> La descrizione viene visualizzato nella descrizione comando di Intellisense per la proprietà generata nella classe del giocatore di ruolo.|`Description for` *il nome completo del ruolo*|  
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generata per il ruolo del dominio.|Il valore di modificare la proprietà name.|  
|Parola chiave della Guida|La parola chiave facoltativa utilizzata per indicizzare la Guida del ruolo del dominio.|\<nessuno\>|  
|Nome visualizzato della proprietà|Il nome che verrà visualizzato nella finestra di progettazione generata per il ruolo generato della proprietà.|Il valore di modificare la proprietà name proprietà.|  
  
> [!NOTE]
>  Il valore predefinito di un nome visualizzato è basato sul valore della proprietà associata inserendo gli spazi prima di ogni carattere maiuscolo che è preceduto da un carattere minuscolo e che non è seguito da un altro carattere maiuscolo.  
  
## Vedere anche  
 [Proprietà delle relazioni di dominio](../modeling/properties-of-domain-relationships.md)