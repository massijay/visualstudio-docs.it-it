---
title: "Elemento di inclusione | Microsoft Docs"
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
  - "Include"
helpviewer_keywords: 
  - "Includere l'elemento (VSCT XML schema)"
  - "Elementi dello schema XML VSCT, inclusione"
ms.assetid: c923dfe6-084a-4105-aec1-f0a3f8399c54
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento di inclusione
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'elemento Include specifica un file che può essere individuato fornito il percorso per l'inserimento nel file corrente.  Tutti i simboli e i tipi definiti diventerà parte del risultato compilato.  
  
## Sintassi  
  
```c#  
<Include href="stdidcmd.h" />  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|href|Obbligatorio. Il percorso al file di intestazione:<br /><br /> href\="stdidcmd.h"|  
|Condizione|Facoltativo. Vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|Nessuno.|Nessuno.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi, ovvero voci di menu, menu, barre degli strumenti e caselle combinate, che fornisce un VSPackage all'IDE.|  
  
## Esempio  
  
```  
<Include href="PackagePlacements.vsct"/>  
```  
  
## Vedere anche  
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)