---
title: "API Reference for T4 Text Templates | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 63279da9-69ac-49ad-ac7d-43957c45e0ce
caps.latest.revision: 6
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 6
---
# API Reference for T4 Text Templates
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'API del modello di testo consente di invocare e personalizzare la trasformazione di [modelli di testo](../modeling/code-generation-and-t4-text-templates.md).  
  
## Spazi dei nomi  
  
|Spazio dei nomi|Scopo|  
|---------------------|-----------|  
|<xref:Microsoft.VisualStudio.TextTemplating>|Contiene le classi per la funzionalità di trasformazione del modello di testo.  Il motore di trasformazione del modello di testo è integrato in Visual Studio e trasforma i file modello di testo in file di output di testo generato.|  
|<xref:Microsoft.VisualStudio.TextTemplating.Modeling>|Fornisce funzionalità di trasformazione del testo correlate a modelli UML e linguaggi specifici di dominio, ad esempio l'accesso a ModelBus di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|  
|<xref:Microsoft.VisualStudio.TextTemplating.VSHost>|Fornisce l'accesso al servizio del modello di testo in [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].|