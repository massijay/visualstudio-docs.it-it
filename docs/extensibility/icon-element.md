---
title: "Icona elemento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elementi dello schema XML VSCT, icona"
  - "Elemento Icon (VSCT XML schema)"
ms.assetid: 73c58fe3-d53c-4f4e-b025-29567c6cbb7c
caps.latest.revision: 5
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 5
---
# Icona elemento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

L'attributo del tag icona guid è il guid di una bitmap specificata.  L'attributo id consente di selezionare lo slot nella striscia di bitmap. Questo elemento è facoltativo.  Se questo elemento viene omesso il valore di **guidOfficeIcon:msotcidNoIcon** verrà implicita.  
  
## Sintassi  
  
```  
<Icon guid="guidImages" id="bmpPic1" />  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|GUID|Obbligatorio. Il guid di una bitmap specificata.|  
|ID|Obbligatorio. Seleziona lo slot nella striscia di bitmap.|  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|Nessuno.|Nessuno.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento di pulsanti](../extensibility/buttons-element.md)||  
  
## Vedere anche  
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)