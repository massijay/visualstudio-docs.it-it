---
title: "Enumerazione DOCUMENTNAMETYPE | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-script-interfaces"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "reference"
apiname: DOCUMENTNAMETYPE
apilocation: scrobj.dll
helpviewer_keywords: 
  - "Enumerazione DOCUMENTNAMETYPE"
ms.assetid: d36d550e-efb4-493d-8971-4de267005654
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Enumerazione DOCUMENTNAMETYPE
Viene descritto il tipo per ottenere per un documento.  
  
## Sintassi  
  
```  
typedef enum tagDOCUMENTNAMETYPE {  
   DOCUMENTNAMETYPE_APPNODE,  
   DOCUMENTNAMETYPE_TITLE,  
   DOCUMENTNAMETYPE_FILE_TAIL,  
   DOCUMENTNAMETYPE_URL,  
DOCUMENTNAMETYPE_UNIQUE_TITLE,  
} DOCUMENTNAMETYPE;  
```  
  
## Membri  
  
|Membro|Descrizione|  
|------------|-----------------|  
|DOCUMENTNAMETYPE\_APPNODE|Ottiene il nome visualizzato nella struttura ad albero dell'applicazione.|  
|DOCUMENTNAMETYPE\_TITLE|Ottiene il nome visualizzato nella barra del titolo del visualizzatore.|  
|DOCUMENTNAMETYPE\_FILE\_TAIL|Ottiene il nome file senza un percorso.|  
|DOCUMENTNAMETYPE\_URL|Ottiene l'URL del documento.|  
|DOCUMENTNAMETYPE\_UNIQUE\_TITLE|Ottiene il titolo aggiunto all'enumerazione per l'id.|  
  
## Vedere anche  
 [Costanti, enumerazioni e strutture del debugger di script ActiveX](../../winscript/reference/active-script-debugger-constants-enumerations-and-structures.md)