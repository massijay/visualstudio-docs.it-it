---
title: "Elemento menu | Microsoft Docs"
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
  - "Elementi dello schema XML VSCT, i menu"
  - "Elemento di menu (VSCT XML schema)"
ms.assetid: d825a99b-e05c-4dd9-8933-a180216d667a
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento menu
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definisce tutti i menu e barre degli strumenti che implementa un VSPackage.  
  
## Sintassi  
  
```  
<Menus>  
  <Menu>... </Menu>  
  <Menu>... </Menu>  
</Menus>  
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
|[Menus Element](../extensibility/menus-element.md)|Definisce tutti i menu e barre degli strumenti che implementa un VSPackage.|  
|[Elemento menu](../extensibility/menu-element.md)|Rappresenta un singolo menu o una barra degli strumenti.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento Commands](../extensibility/commands-element.md)|Rappresenta la raccolta di comandi in VSPackage.|  
  
## Esempio  
  
```  
<Commands package="guidMyPackage"> <Menus> <Menu Condition="'%(DEBUG)' != 'true'" guid="cmdSetGuidMyProductCommands" id="menuIDMainMenu" priority="0x0000" type="Menu"> <Annotation> <Documentation>this is an annotation</Documentation> <AppInfo> <CustomData> <CustomSubElement>Some data</CustomSubElement> </CustomData> </AppInfo> </Annotation> <CommandFlag>AlwaysCreate</CommandFlag> <Strings> <ButtonText>MainMenu</ButtonText> </Strings> </Menu> </Menus> <Commands>  
```  
  
## Vedere anche  
 [Come package VS aggiungere elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)