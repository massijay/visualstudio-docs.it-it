---
title: "Propriet&#224; delle relazioni di dominio | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, relazioni di dominio"
ms.assetid: 9ccb3dc2-b80c-4585-932f-3c5f87bafbcd
caps.latest.revision: 20
caps.handback.revision: 20
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Propriet&#224; delle relazioni di dominio
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le proprietà nella tabella seguente sono associate a una relazione di dominio. Per informazioni sulle relazioni di dominio, vedere [informazioni sui modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md). Per ulteriori informazioni su come utilizzare queste proprietà, vedere [personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Proprietà|Descrizione|Predefinito|  
|--------------|-----------------|-------------|  
|Modificatore di accesso|Il livello di accesso della relazione di dominio (`public` o `internal`).|`public`|  
|Attributi personalizzati|Utilizzato per aggiungere attributi alla classe di codice sorgente generato della relazione di dominio.|\< none>|  
|Genera doppia derivato|Se `True`, viene generata una classe di base sia una classe parziale (per supportare la personalizzazione tramite le sostituzioni). Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Dispone di un costruttore personalizzato|Se `True`, indica che nel codice sorgente viene fornito un costruttore personalizzato. Per ulteriori informazioni, vedere [override ed estensione delle classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generato della relazione di dominio (`none`, `abstract` o `sealed`).|\< none>|  
|Consente i duplicati|Se `True`, possibile creare collegamenti duplicati della relazione di dominio tra i due elementi stesso.|`False`|  
|Relazioni di base|Se la relazione di dominio è derivata, la relazione di base della relazione di dominio.|\< none>|  
|È l'incorporamento|Se `True`, la relazione di dominio è una relazione di incorporamento. Se `False`, la relazione è una relazione di riferimento.|\< entrambi>|  
|Nome|Il nome della relazione di dominio.|Nome corrente|  
|Spazio dei nomi|Lo spazio dei nomi associato con la relazione di dominio.|Spazio dei nomi corrente|  
|Note|Note informali associati con la relazione di dominio.|\< none>|  
|Descrizione|La descrizione che viene utilizzata per documentare il codice e viene utilizzata nell'interfaccia Utente della finestra di progettazione generata.|\< none>|  
|Nome visualizzato|Il nome visualizzato nella finestra di progettazione generata per la relazione di dominio.|\< none>|  
|Parola chiave della Guida|La parola chiave facoltativa che viene utilizzata per indicizzare la Guida F1 per la relazione di dominio.|\< none>|  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario sugli strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/it-it/ca5e84cb-a315-465c-be24-76aa3df276aa)