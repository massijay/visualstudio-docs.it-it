---
title: "Novit&#224; di origine controllo plug-in API versione 1.3 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "controllo del codice sorgente plug-in, quali sono le novità in API v 1.3"
  - "che cos'è nuovo [Visual Studio SDK], origine plug-in del controllo"
ms.assetid: 7dfb2227-6e1d-4028-bce9-f8967456a993
caps.latest.revision: 13
caps.handback.revision: 13
ms.author: "gregvanl"
manager: "ghogen"
---
# Novit&#224; di origine controllo plug-in API versione 1.3
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

La versione 1,3 di plug\-in controllo del codice sorgente API vengono introdotte le nuove funzioni seguenti per fornire il controllo più avanzato.  
  
## modifiche  
 Le funzioni seguenti sono nuove la versione 1,3 di plug\-in controllo del codice sorgente API:  
  
|Funzione|Panoramica|  
|--------------|----------------|  
|[SccGetExtendedCapabilities](../../extensibility/sccgetextendedcapabilities-function.md)|Consente i bit di capacità aggiuntivi da segnalare|  
|[SccEnumChangedFiles](../../extensibility/sccenumchangedfiles-function.md)|Consente la revisione dei file che dispongono di versioni più recenti nel database di controllo della versione che sul disco locale|  
|[SccQueryChanges](../../extensibility/sccquerychanges-function.md)|Consente l'analisi dello stato di modifiche al nome \(rinomina, le aggiunte e eliminazioni\) per i file specificati|  
|[SccPopulateDirList](../../extensibility/sccpopulatedirlist-function.md)|Allows examination of directories and files in the version control database|  
|[SccAddFilesFromSCC](../../extensibility/sccaddfilesfromscc-function.md)|Aggiunge un elenco specificato di file dal database di controllo della versione per il progetto corrente|  
|[SccBackgroundGet](../../extensibility/sccbackgroundget-function.md)|Esegue un silent “get„ di file specificato \(nessuna interfaccia utente viene mostrata\)|  
|[SccGetUserOption](../../extensibility/sccgetuseroption-function.md)|Consente l'accesso alle opzioni specifiche dell'utente|  
  
## Vedere anche  
 [Introduzione](../../extensibility/internals/getting-started-with-source-control-plug-ins.md)   
 [Novità di origine controllo plug\-in API versione 1.2](../../extensibility/internals/what-s-new-in-the-source-control-plug-in-api-version-1-2.md)