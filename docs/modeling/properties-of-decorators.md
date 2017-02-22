---
title: "Propriet&#224; degli elementi Decorator | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, elementi Decorator"
ms.assetid: f6322fe5-dc08-4d32-a6b3-0bd18879136d
caps.latest.revision: 23
caps.handback.revision: 23
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# Propriet&#224; degli elementi Decorator
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gli elementi Decorator sono icone, un testo a, o espandono\/frecce di espansione compresso che possono essere visualizzati sulle forme o sui connettori nel diagramma.  Nelle tabelle riportate le proprietà per i tre tipi di elemento Decorator.  Alcune delle proprietà vengono visualizzati solo sugli elementi Decorator di forma o solo negli elementi Decorator del connettore.  
  
 Per ulteriori informazioni, vedere [Procedura: definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md).  per ulteriori informazioni su come utilizzare queste proprietà, vedere [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
## Espandere\/elemento Decorator di compressione  
  
|Proprietà|Descrizione|Predefinito|  
|---------------|-----------------|-----------------|  
|DisplayName|Il nome dell'elemento Decorator visualizzati nella finestra di progettazione generata un'eccezione.|Espandere l'elemento Decorator di compressione|  
|Nome|Il nome dell'elemento Decorator.|ExpandCollapseDecorator|  
|Note|Note informali associate a questo elemento Decorator.|\<nessuno\>|  
|HorizontalOffset|L'offset orizzontale, in corrispondenza della posizione predefinita dell'elemento Decorator, nei pollici.  \(Nelle forme solo\).|0|  
|VerticalOffset|L'offset verticale, rispetto alla posizione predefinita dell'elemento Decorator, nei pollici.  \(Nelle forme solo\).|0|  
|OffsetFromLine|L'offset dell'elemento Decorator dalla riga, relativo alla posizione predefinita, nei pollici.  \(Sui connettori solo\).|0|  
|OffsetFromShape|L'offset dell'elemento Decorator dalla forma, relativo alla posizione predefinita, nei pollici.  \(Sui connettori solo\).|0|  
|Position|Il percorso predefinito dell'elemento Decorator.|SourceTop|  
  
## Elemento Decorator icona  
  
|Proprietà|Descrizione|Predefinito|  
|---------------|-----------------|-----------------|  
|DefaultIcon|Il percorso icona o del file di immagine da visualizzare.|\<nessuno\>|  
|DisplayName|Il nome dell'elemento Decorator da visualizzare nella finestra di progettazione generata un'eccezione.|Elemento Decorator icona|  
|Nome|Il nome dell'elemento Decorator.|IconDecorator|  
|Note|Note informali associate all'elemento Decorator.|\<nessuno\>|  
|HorizontalOffset|L'offset orizzontale, in corrispondenza della posizione predefinita dell'elemento Decorator, nei pollici.  \(Nelle forme solo\).|0|  
|VerticalOffset|L'offset verticale, rispetto alla posizione predefinita dell'elemento Decorator, nei pollici.  \(Nelle forme solo\).|0|  
|OffsetFromLine|L'offset dell'elemento Decorator dalla riga, relativo alla posizione predefinita, nei pollici.  \(Sui connettori solo\).|0|  
|OffsetFromShape|L'offset dell'elemento Decorator dalla forma, relativo alla posizione predefinita, nei pollici.  \(Sui connettori solo\).|0|  
|Position|Il percorso predefinito dell'elemento Decorator.|SourceTop|  
  
## TextDecorator  
  
|Proprietà|Descrizione|Predefinito|  
|---------------|-----------------|-----------------|  
|DefaultText|Il testo predefinito da visualizzare.|Etichetta|  
|DisplayName|Il nome dell'elemento Decorator da visualizzare nella finestra di progettazione generata un'eccezione.|Etichetta|  
|FontSize|La dimensione dei caratteri del testo visualizzato nell'elemento Decorator.|8|  
|FontStyle|Stile del carattere per il testo visualizzato nell'elemento Decorator.|Regolare|  
|Nome|Il nome dell'elemento Decorator.|Etichetta|  
|Note|Note informali associate all'elemento Decorator.|\<nessuno\>|  
|HorizontalOffset|L'offset orizzontale, in corrispondenza della posizione predefinita dell'elemento Decorator, nei pollici.  \(Nelle forme solo\).|0|  
|VerticalOffset|L'offset verticale, rispetto alla posizione predefinita dell'elemento Decorator, nei pollici.  \(Nelle forme solo\).|0|  
|OffsetFromLine|L'offset dell'elemento Decorator dalla riga, relativo alla posizione predefinita, nei pollici.  \(Sui connettori solo\).|0|  
|OffsetFromShape|L'offset dell'elemento Decorator dalla forma, relativo alla posizione predefinita, nei pollici.  \(Sui connettori solo\).|0|  
|Position|Il percorso predefinito dell'elemento Decorator.|TargetBottom|  
  
## Vedere anche  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/it-it/ca5e84cb-a315-465c-be24-76aa3df276aa)