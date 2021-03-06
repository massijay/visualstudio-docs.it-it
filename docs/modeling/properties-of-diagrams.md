---
title: "Proprietà dei diagrammi | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.dsltools.dsldesigner.dsldiagram
helpviewer_keywords: Domain-Specific Language, diagram
ms.assetid: 00bba4b8-6aa6-4027-96cb-4f4c41a77d3c
caps.latest.revision: "25"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: fcd30a30bdae896be5aceb9dc685a5fb762ee4af
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="properties-of-diagrams"></a>Proprietà di diagrammi
È possibile impostare le proprietà che specificano come diagrammi verranno visualizzato nella finestra di progettazione generato. Ad esempio, è possibile specificare un colore predefinito per il testo nel diagramma.  
  
 Per ulteriori informazioni, vedere [come definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md). Per ulteriori informazioni sull'utilizzo di queste proprietà, vedere [personalizzare ed estendere un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 Nella tabella seguente sono elencate le proprietà dei diagrammi.  
  
|Proprietà|Descrizione|Impostazione predefinita|  
|--------------|-----------------|-------------|  
|Colore riempimento|Il colore di riempimento per il diagramma.|Vuoto|  
|Colore del testo|Il colore del testo che viene visualizzato nel diagramma.|Nero|  
|Modificatore di accesso|Il modificatore di accesso della classe (interna o pubblica).|Public|  
|Attributi personalizzati|Consente di aggiungere attributi alla classe il codice generato.|\<Nessuno >|  
|Genera l'errore doppia derivato|Se `True`, verrà generate una classe di base sia una classe parziale (per supportare la personalizzazione tramite le sostituzioni). Per ulteriori informazioni, vedere [si esegue l'override ed estendere le classi generate](../modeling/overriding-and-extending-the-generated-classes.md).|False|  
|Ha un costruttore personalizzato|Se `True`, verrà fornito un costruttore personalizzato nel codice sorgente. Per ulteriori informazioni, vedere [si esegue l'override ed estendere le classi generate](../modeling/overriding-and-extending-the-generated-classes.md)...|False|  
|Modificatore di ereditarietà|Descrive il tipo di ereditarietà della classe di codice sorgente generato dal diagramma (`none`, `abstract` o `sealed`).|Nessuno|  
|Diagramma di base|Classe di base di questo diagramma.|(nessuno)|  
|Nome|Il nome di questo diagramma.|Nome corrente|  
|Spazio dei nomi|Lo spazio dei nomi che è associato a questo diagramma.|Spazio dei nomi corrente|  
|Classe rappresentata|La classe di dominio radice che rappresenta questo diagramma.|Classe radice corrente, se applicabile|  
|Note|Note informale che sono associate a questo elemento.|\<Nessuno >|  
|Colore di riempimento espone come proprietà|Se `True`, l'utente può impostare il colore di riempimento del diagramma della finestra di progettazione generato. Per impostare questo, fare clic con il pulsante destro la forma di diagramma e fare clic su **Explosed aggiungere**.|False|  
|Espone il colore del testo come proprietà|Se `True`, l'utente può impostare il colore del testo del diagramma nella finestra di progettazione generato. Per impostare questo, fare clic con il pulsante destro la forma di diagramma e fare clic su **Explosed aggiungere**.|False|  
|Descrizione|La descrizione che viene utilizzata per la finestra di progettazione generato del documento.|\<Nessuno >|  
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generato per il diagramma.|\<Nessuno >|  
|Parola chiave della Guida|La parola chiave che viene utilizzata per l'indice della Guida F1 per questo diagramma.|\<Nessuno >|  
  
## <a name="see-also"></a>Vedere anche  
 [Glossario di strumenti di linguaggio specifico di dominio](http://msdn.microsoft.com/en-us/ca5e84cb-a315-465c-be24-76aa3df276aa)