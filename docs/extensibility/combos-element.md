---
title: "Elemento casella combinata | Microsoft Docs"
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
  - "Elemento casella combinata (VSCT XML schema)"
  - "Elementi dello schema XML VSCT, casella combinata"
ms.assetid: ef48d2d2-0c47-4f93-8cfe-52026b6c463e
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento casella combinata
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Raggruppa gli elementi [Elemento casella combinata](../extensibility/combo-element.md).  
  
## Sintassi  
  
```  
<Combos>  
  <Combo>... </Combo>  
  <Combo>... </Combo>  
</Combos>  
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
|[Combos Element](../extensibility/combos-element.md)|Raggruppa gli elementi di casella combinata.|  
|[Elemento casella combinata](../extensibility/combo-element.md)|Definisce i comandi che vengono visualizzati in una casella combinata.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento Commands](../extensibility/commands-element.md)|Rappresenta la raccolta di comandi sulla barra degli strumenti VSPackage.|  
  
## Esempio  
  
```  
<Combos> <Combo guid="guidWidgetPackage" id="cmdidInsertOptions" defaultWidth="100" idCommandList="cmdidGetInsertOptionsList"> <CommandFlag>DynamicVisibility</CommandFlag> <Strings> <ButtonText>Select Insert Options</ButtonText> </Strings> </Combo> <Combo guid="guidWidgetPackage" id="cmdidInsertOptions" priority="0x0500" type="DropDownCombo" defaultWidth="100" idCommandList="cmdidGetInsertOptionsList"> <Parent guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <CommandFlag>DynamicVisibility</CommandFlag> <Strings> <ButtonText>Select Insert Options</ButtonText> </Strings> </Combo> </Combos>  
```  
  
## Vedere anche  
 [Come package VS aggiungere elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)