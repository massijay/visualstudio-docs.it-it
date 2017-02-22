---
title: "Gruppi, menu e comandi definiti dall&#39;IDE | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "comandi, definito dall'ambiente"
  - "file. vsct, costanti definite dall'ambiente"
  - "gruppi di comandi definiti dall'ambiente"
ms.assetid: 86b3af13-7163-48c6-986b-7beeedbc26cc
caps.latest.revision: 27
caps.handback.revision: 27
ms.author: "gregvanl"
manager: "ghogen"
---
# Gruppi, menu e comandi definiti dall&#39;IDE
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Molti menu, comandi e i gruppi di comando sono già definiti per l'utilizzo di [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] IDE. Questi comandi sono disponibili per l'utilizzo anche quando si estende [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)].  
  
## Ricerca di comandi definiti dall'ambiente  
 I comandi di ambiente vengono definiti in un set di quattro file. vsct:  
  
-   SharedCmdDef.vsct  
  
-   SharedCmdPlace.vsct  
  
-   ShellCmdDef.vsct  
  
-   ShellCmdPlace.vsct  
  
 Questi file si trovano *\< percorso di installazione di Visual Studio SDK \>*\\VisualStudioIntegration\\Common\\Inc\\. Questi file forniscono le definizioni e i GUID dei gruppi che è possibile utilizzare nel comando tabella file di configurazione \(vsct\) il pacchetto Visual Studio come contenitori per i menu, gruppi e i comandi e menu.  
  
## Contenuto della sezione  
 [GUID e ID del menu di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-menus.md)  
 Fornisce i valori GUID e ID dei menu nella barra dei menu di Visual Studio e dei gruppi che contengono.  
  
 [GUID e ID delle barre degli strumenti di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-toolbars.md)  
 Fornisce i valori GUID e ID delle barre degli strumenti nell'IDE di Visual Studio e dei gruppi che contengono.  
  
 [I GUID e ID dei comandi di Visual Studio](../../extensibility/internals/guids-and-ids-of-visual-studio-commands.md)  
 Fornisce i valori GUID e ID di comandi definiti dall'IDE di Visual Studio.  
  
## Vedere anche  
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Comandi definiti dall'IDE per l'estensione di sistemi di progetto](../../extensibility/internals/ide-defined-commands-for-extending-project-systems.md)   
 [Come package VS aggiungere elementi dell'interfaccia utente](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)