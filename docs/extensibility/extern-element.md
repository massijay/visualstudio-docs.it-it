---
title: "Elemento extern | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "Extern"
helpviewer_keywords: 
  - "Elementi dello schema XML VSCT, Extern"
  - "Elemento extern (VSCT XML schema)"
ms.assetid: db6c3ddd-a1ba-450a-897a-bb568a5377fc
caps.latest.revision: 15
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 15
---
# Elemento extern
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'elemento Extern fa riferimento a file esterni intestazione \(h\) per unire con il file vsct in fase di compilazione. I file da unire devono essere nel percorso di inclusione fornito al compilatore VSCT o a cui fa riferimento un [Elemento di inclusione](../extensibility/include-element.md). I file possono essere altri file. vsct o file di intestazione C\+\+.  
  
 Le definizioni nel file di intestazione devono essere nel formato "\#define \[simbolo\] \[valore\]" il valore può essere un altro simbolo, se è definito in precedenza. Le definizioni possono essere utilizzate nelle istruzioni condizionali di elementi di comando. Qualsiasi simbolo non sia utilizzato verrà rimosso.  
  
 CommandTable Element  
Extern Element  
  
## Sintassi  
  
```  
<Extern href="stdidcmd.h" />  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|href|Obbligatorio. Il percorso al file di intestazione:<br /><br /> href\="stdidcmd.h"|  
|Condizione|Facoltativo. Vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
|linguaggio|Facoltativo. La lingua predefinita del tutto [\< stringhe \>](../extensibility/strings-element.md) elementi della tabella di comando:<br /><br /> Language \= "en\-us"|  
  
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
<?xml version="1.0" encoding="utf-8"?> <CommandTable xmlns="http://schemas.microsoft.com/VisualStudio/2005-10- 18/CommandTable" xmlns:xs="http://www.w3.org/2001/XMLSchema"> <Extern href="C:\VSCore\vscommon\inc\vsshlids.h"/> … <Commands package="guidMyPackage"> </CommandTable>  
```  
  
## Vedere anche  
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)   
 [Come package VS aggiungere elementi dell'interfaccia utente](../extensibility/internals/how-vspackages-add-user-interface-elements.md)   
 [I comandi, menu e barre degli strumenti](../extensibility/internals/commands-menus-and-toolbars.md)