---
title: "Elemento CommandPlacement | Microsoft Docs"
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
  - "Elemento CommandPlacements (VSCT XML schema)"
  - "Elementi dello schema XML VSCT, CommandPlacements"
ms.assetid: 2cbd7ac8-c55a-43d8-a26d-713b3d790016
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento CommandPlacement
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'elemento CommandPlacement consente pulsanti, gruppi e i menu da includere in più di un gruppo o un menu. Utilizzando l'elemento CommandPlacement, non è necessario ridefinire completamente questi elementi per modificare l'aspetto di un'interfaccia utente.  
  
 Per altre informazioni, vedere [Creazione di gruppi riutilizzabili di pulsanti](../extensibility/creating-reusable-groups-of-buttons.md).  
  
## Sintassi  
  
```  
<CommandPlacement guid=guidMyCommandSet" id="MyCommand" priority="0x001" >  
  <Parent>... </Parent>  
</CommandPlacement>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|GUID|Obbligatorio. Il guid del set di comandi, come definito nel [Elemento di simboli](../extensibility/symbols-element.md).|  
|ID|Obbligatorio. L'id del menu, gruppo o comando di essere distribuita, come definito nel `Symbols Element`.|  
|priority|Obbligatorio. Determina la posizione visiva dell'elemento nel relativo elemento padre.|  
|Condizione|Facoltativo. Vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|Padre|Obbligatorio. Il menu o un gruppo che ospita l'elemento da inserire.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento CommandPlacements](../extensibility/commandplacements-element.md)|Specifica i gruppi di elementi CommandPlacements e CommandPlacement.|  
  
## Esempio  
  
```  
<CommandPlacements> <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0300"> <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/> </CommandPlacement> </CommandPlacements>  
```  
  
## Vedere anche  
 [Elemento CommandPlacements](../extensibility/commandplacements-element.md)   
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)