---
title: "Le proprietà delle classi di dominio | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Domain-Specific Language, domain class
ms.assetid: a3993995-19e7-4761-a972-b1de89131a1b
caps.latest.revision: "21"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: e9bed31caa63a12677e7b9798e6cf72524500c21
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-domain-classes"></a>Proprietà delle classi di dominio
Classi di dominio includono le proprietà nella tabella seguente. Per informazioni sulle classi di dominio, vedere [informazioni sui modelli, classi e relazioni](../modeling/understanding-models-classes-and-relationships.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
|Proprietà|Descrizione|Impostazione predefinita|  
|--------------|-----------------|-------------|  
|Modificatore di accesso|Livello di accesso della classe di dominio (`public` o `internal`).|`public`|  
|Attributi personalizzati|Consente di aggiungere attributi alla classe di codice sorgente generato da questa classe di dominio.|\<Nessuno >|  
|Genera l'errore doppia derivato|Se `True`, verrà generate una classe di base sia una classe parziale (per supportare la personalizzazione tramite le sostituzioni). Per ulteriori informazioni, vedere [si esegue l'override ed estendere le classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Ha un costruttore personalizzato|Se `True`, verrà fornito un costruttore personalizzato nel codice sorgente. Per ulteriori informazioni, vedere [si esegue l'override ed estendere le classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|`False`|  
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generato dalla classe di dominio (`none`, `abstract` o `sealed`).|`none`|  
|Classe di base|Se questa classe di dominio è derivata, il nome della classe di base.|\<Nessuno >|  
|Nome|Il nome di questa classe di dominio.|Nome corrente|  
|Spazio dei nomi|Lo spazio dei nomi di questa classe di dominio.|Spazio dei nomi corrente|  
|Note|Note informale che sono associate a questa classe di dominio.|\<Nessuno >|  
|Descrizione|La descrizione che viene utilizzata per documentare l'interfaccia utente della finestra di progettazione generato.|\<Nessuno >|  
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generato per questa classe di dominio.|\<Nessuno >|  
|Parola chiave della Guida|La parola chiave facoltativa che viene utilizzata per l'indice della Guida F1 per questa classe di dominio.|\<Nessuno >|  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario di strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)