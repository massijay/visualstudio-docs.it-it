---
title: "Elemento VisibilityConstraints | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VisibilityConstraints"
helpviewer_keywords: 
  - "Elementi dello schema XML VSCT, VisibilityConstraints"
  - "Elemento VisibilityConstraints (VSCT XML schema)"
ms.assetid: d6dcd314-6fe4-4693-a189-91fa026c7b34
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento VisibilityConstraints
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'elemento VisibilityConstraints determina la visibilità statica dei gruppi di comandi e barre degli strumenti. La visibilità viene controllata innanzitutto dal [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente di sviluppo integrato \(IDE\) senza caricare il VSPackage.  
  
## Sintassi  
  
```  
<VisibilityConstraints>  
  <VisibilityConstraint>... </VisibilityConstraint>  
  <VisibilityConstraint>... </VisibilityConstraint>  
</VisibilityConstraint>  
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
|[Elemento VisibilityItem](../extensibility/visibilityitem-element.md)|Determina la visibilità statica di comandi e barre degli strumenti.|  
|[VisibilityConstraints](../extensibility/visibilityconstraints-element.md)|Determina la visibilità statica dei gruppi di comandi e barre degli strumenti.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi \(ad esempio, le voci di menu, menu, barre degli strumenti e caselle combinate\) che fornisce un VSPackage all'IDE.|  
  
## Esempio  
  
```  
<VisibilityConstraints> <VisibilityItem guid="cmdSetGuidMyProductCommands"     id="cmdidAddWidget" context="guidNotViewSourceMode"/> </VisibilityConstraints>  
```  
  
## Vedere anche  
 [Elemento VisibilityItem](../extensibility/visibilityitem-element.md)   
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)