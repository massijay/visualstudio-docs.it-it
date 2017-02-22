---
title: "Elemento di pulsanti | Microsoft Docs"
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
  - "Elemento pulsanti (VSCT XML schema)"
  - "Elementi dello schema XML VSCT, pulsanti"
ms.assetid: 9f2cf94d-dec5-4776-a836-9a89c75f0c87
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento di pulsanti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Gruppi [pulsante](../extensibility/button-element.md) che rappresentano singoli comandi.  
  
## Sintassi  
  
```  
<Buttons>  
  <Button>... </Button>  
  <Button>... </Button>  
</Buttons>  
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
|[Buttons Element](../extensibility/buttons-element.md)|Raggruppa gli elementi Button.|  
|[Elemento Button](../extensibility/button-element.md)|Definisce un comando che l'utente può interagire con.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento Commands](../extensibility/commands-element.md)|Rappresenta la raccolta di comandi sulla barra degli strumenti VSPackage.|  
  
## Esempio  
  
```  
<Buttons> <Button guid="guidMenuAndCommandsCmdSet" id="cmdidMyCommand"     priority="0x100" type="Button"> <Parent guid="guidMenuAndCommandsCmdSet" id="MyMenuGroup"/> <Icon guid="guidGenericCmdBmp" id="bmpArrow"/> <Strings> <ButtonText>C# Command Sample</ButtonText> </Strings> </Button> </Buttons>  
```  
  
## Vedere anche  
 [Come package VS aggiungere elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)