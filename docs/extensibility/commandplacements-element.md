---
title: "Elemento CommandPlacements | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CommandPlacements"
helpviewer_keywords: 
  - "Elemento CommandPlacements (VSCT XML schema)"
  - "Elementi dello schema XML VSCT, CommandPlacements"
ms.assetid: 78a5724a-3b9f-4c78-9c0d-8faa3924f81c
caps.latest.revision: 11
caps.handback.revision: 11
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento CommandPlacements
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'elemento CommandPlacements Raggruppa gli elementi CommandPlacement e altri raggruppamenti CommandPlacements.  
  
 L'elemento CommandPlacements è facoltativo. Se non i comandi, gruppi o i devono essere incluso in una posizione secondaria, non è necessario includere in questa sezione del file vsct.  
  
## Sintassi  
  
```  
<CommandPlacements>  
  <CommandPlacement>... </CommandPlacement>  
  <CommandPlacement>... </CommandPlacement>  
</CommandPlacements>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|Condizione|Facoltativo. Vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|CommandPlacements|Raggruppa gli elementi CommandPlacement e altri raggruppamenti CommandPlacements.|  
|[Elemento CommandPlacement](../extensibility/commandplacement-element.md)|Consente di pulsanti, gruppi e i menu da includere in più di un gruppo o un menu.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi.|  
  
## Esempio  
  
```  
<CommandPlacements> <CommandPlacement guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0300"> <Parent guid="cmdGuidWidgetCommands" id="menuIDEditWidget"/> </CommandPlacement> </CommandPlacements>  
```  
  
## Vedere anche  
 [Elemento CommandPlacement](../extensibility/commandplacement-element.md)   
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)