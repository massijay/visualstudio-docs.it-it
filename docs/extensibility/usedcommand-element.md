---
title: "Elemento UsedCommand | Microsoft Docs"
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
  - "Elemento UsedCommands (VSCT XML schema)"
  - "Elementi dello schema XML VSCT, UsedCommands"
ms.assetid: 99cd05d3-644a-42ff-b289-8458cd1b20c0
caps.latest.revision: 10
caps.handback.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento UsedCommand
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Consente un VSPackage per accedere a un comando che viene definito in un altro file. vsct. Ad esempio, se il pacchetto Visual Studio utilizza lo standard **Copia** comando, che viene definito il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] shell, per aggiungere il comando a un menu o una barra degli strumenti senza implementare nuovamente il.  
  
## Sintassi  
  
```  
<UsedCommand guid="guidMyCommandGroup" id="MyCommand" />  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|GUID|Obbligatorio. Il GUID della coppia ID GUID che identifica il comando.|  
|ID|Obbligatorio. L'ID della coppia ID GUID che identifica il comando.|  
|Condizione|Facoltativo. Vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|None||  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento UsedCommands](../extensibility/usedcommands-element.md)|Raggruppa gli elementi UsedCommand e altri raggruppamenti UsedCommands.|  
  
## Note  
 Mediante l'aggiunta di un comando per il `<UsedCommands>` elemento, un VSPackage informa il [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] ambiente che VSPackage richiede che il comando. È necessario aggiungere un `<UsedCommand>` \(elemento\) per qualsiasi comando è necessario che il pacchetto potrebbe non essere incluse in tutte le versioni e le configurazioni di Visual Studio. Ad esempio, se il pacchetto chiama un comando che è specifico di Visual C\+\+, il comando non sarà disponibile per gli utenti di Visual Web Developer, a meno di non includere un `<UsedCommand>` \(elemento\) per il comando.  
  
## Esempio  
  
```  
<UsedCommands> <UsedCommand guid="guidVSStd97" id="cmdidCut"/> <UsedCommand guid="guidVSStd97" id="cmdidCopy"/> <UsedCommand guid="guidVSStd97" id="cmdidPaste"/> </UsedCommands>  
```  
  
## Vedere anche  
 [Elemento UsedCommands](../extensibility/usedcommands-element.md)   
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)