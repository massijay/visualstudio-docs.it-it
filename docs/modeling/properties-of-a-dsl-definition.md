---
title: "Propriet&#224; di una definizione DSL | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Linguaggio specifico di dominio, file di definizione"
ms.assetid: 38debcfe-e1a6-4a3f-9d69-3ab07520f2b6
caps.latest.revision: 13
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
caps.handback.revision: 13
---
# Propriet&#224; di una definizione DSL
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

le proprietà di DslDefinition definiscono *linguaggio specifico di dominio* proprietà di definizione della numerazione di versione.  Le proprietà di DslDefinition vengono visualizzati in **proprietà** finestra quando si fa clic su uno spazio voce del diagramma in Finestra di progettazione del linguaggio specifico di dominio.  
  
 Per ulteriori informazioni, vedere [Procedura: definire un linguaggio specifico di dominio](../modeling/how-to-define-a-domain-specific-language.md).  per ulteriori informazioni su come utilizzare queste proprietà, vedere [Personalizzazione ed estensione di un linguaggio specifico di dominio](../modeling/customizing-and-extending-a-domain-specific-language.md).  
  
 DslDefinition dispone delle proprietà nella tabella seguente:  
  
|Proprietà|Descrizione|Predefinito|  
|---------------|-----------------|-----------------|  
|Modificatore Accesso|determina se il modificatore di accesso per la classe di dominio è pubblico o interno.|public|  
|Attributi personalizzati|attributi definiti personalizzati per la classe di dominio.<br /><br /> **nota** utilizzare il pulsante sfoglia per aggiungere un attributo.|\<nessuno\>|  
|Nome azienda|Il nome del nome della società corrente nel Registro di sistema.|Nome della società corrente|  
|Nome|il nome di questa classe di dominio.|nome corrente|  
|Spazio dei nomi|Lo spazio dei nomi affiliato con questa classe di dominio.|Spazio dei nomi corrente|  
|comprimere il GUID|Il GUID per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pacchetto generato per il linguaggio DSL.|\<nessuno\>|  
|Spazio dei nomi del pacchetto|Lo spazio dei nomi per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pacchetto generato per il linguaggio DSL.|\<nessuno\>|  
|Nome prodotto|Il nome del prodotto che verrà registrato per [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] pacchetto generato per il linguaggio DSL.|\<nessuno\>|  
|Note|Nota associato a questa classe di dominio.|\<nessuno\>|  
|Descrizione|Descrizione per la classe di dominio.|\<nessuno\>|  
|Nome visualizzato|Il nome che verrà visualizzato nella finestra di progettazione generata per questa classe di dominio.|\<nessuno\>|  
|Parola chiave della Guida|La parola chiave della Guida associata a questa classe di dominio.|\<nessuno\>|  
|Compila|Il numero di compilazione incrementale per la definizione di linguaggio specifico di dominio.|0|  
|Numero di versione principale|Il numero di compilazione principale incrementale per la definizione di linguaggio specifico di dominio.|1|  
|Numero di versione secondario|Il numero di compilazione secondario incrementale per la definizione di linguaggio specifico di dominio.|0|  
|revisione|Il numero di compilazione incrementale di revisione per la definizione di linguaggio specifico di dominio.|0|  
  
## Vedere anche  
 [Domain\-Specific Language Tools Glossary](http://msdn.microsoft.com/it-it/ca5e84cb-a315-465c-be24-76aa3df276aa)