---
title: "Elemento Group | Microsoft Docs"
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
  - "Elementi dello schema XML VSCT, gruppi"
  - "Elemento Groups (VSCT XML schema)"
ms.assetid: 69faee18-cbf4-470a-b952-c1919c583df8
caps.latest.revision: 9
caps.handback.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento Group
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definisce un gruppo di comando di VSPackage.  
  
## Sintassi  
  
```  
<Group guid="guidMyCommandSet" id="MyGroup" priority="0x101">  
  <Parent>... </Parent>  
</Group>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|GUID|Obbligatorio. GUID dell'identificatore di comando\/ID GUID.|  
|ID|Obbligatorio. ID dell'identificatore di comando\/ID GUID.|  
|priority|Facoltativo. Un valore numerico che specifica la priorità.|  
|Condizione|Facoltativo. Vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|Padre|Facoltativo. L'elemento padre del pulsante.|  
|Annotazione|Commento facoltativo.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento Groups](../extensibility/groups-element.md)|Contiene le voci che definiscono i gruppi di comando di un package VS.|  
  
## Esempio  
  
```  
<Group guid="cmdSetGuidWidgetCommands" id="groupIDFileEdit"> <Parent guid="guidSHLMainMenu" id="IDM_VS_TOOL_MAINMENU"/> </Group>  
```  
  
## Vedere anche  
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)