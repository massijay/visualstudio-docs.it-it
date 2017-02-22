---
title: "Elemento KeyBindings | Microsoft Docs"
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
  - "KeyBindings"
helpviewer_keywords: 
  - "Elementi dello schema XML VSCT, KeyBindings"
  - "Elemento KeyBindings (VSCT XML schema)"
ms.assetid: 26a15d5c-ddea-4977-af7f-d795ff09c7ad
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento KeyBindings
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'elemento KeyBindings Raggruppa gli elementi dell'oggetto KeyBinding e altri raggruppamenti KeyBindings.  
  
## Sintassi  
  
```  
<KeyBindings>  
  <KeyBinding>... </KeyBinding>  
  <KeyBinding>... </KeyBinding>  
</KeyBindings>  
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
|[Elemento dell'oggetto KeyBinding](../extensibility/keybinding-element.md)|Specifica i tasti di scelta rapida per i comandi.|  
|[KeyBindings](../extensibility/keybindings-element.md)|Raggruppa gli elementi dell'oggetto KeyBinding e altri raggruppamenti KeyBindings.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi.|  
  
## Esempio  
  
```  
<KeyBindings> <KeyBinding guid="guidWidgetPackage" id="cmdidUpdateWidget" editor="guidWidgetEditor" key1="VK_F5"/> <KeyBinding guid="guidWidgetPackage" id="cmdidRunWidget" editor="guidWidgetEditor" key1="VK_F5" mod1="Control"/> </KeyBindings>  
```  
  
## Vedere anche  
 [Elemento dell'oggetto KeyBinding](../extensibility/keybinding-element.md)   
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)