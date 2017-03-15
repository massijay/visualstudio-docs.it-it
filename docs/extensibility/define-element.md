---
title: "Definire l&#39;elemento | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Elementi dello schema XML VSCT, definizione"
  - "Definire l'elemento (VSCT XML schema)"
ms.assetid: 5aee74e3-de41-4dc6-9618-93e158af56dd
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Definire l&#39;elemento
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Definisce una coppia di nome e il valore di simbolo. Questo simbolo può essere valutato dagli attributi condizionali. Per altre informazioni, vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md). Vedere anche il [Elemento di simboli](../extensibility/symbols-element.md).  
  
## Sintassi  
  
```  
<Define name="Mode" value="Standard" />  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|nome|Obbligatorio. Il nome del simbolo:<br /><br /> nome \= "Modalità"|  
|valore|Obbligatorio. Il valore del simbolo:<br /><br /> valore \= "Standard"|  
|Condizione|Facoltativo. Per altre informazioni, vedere [Attributi condizionali](../extensibility/vsct-xml-schema-conditional-attributes.md).|  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[Elemento CommandTable](../extensibility/commandtable-element.md)|Definisce tutti gli elementi che rappresentano i comandi che fornisce un VSPackage all'ambiente di sviluppo integrato \(IDE\). Ad esempio, le voci di menu, menu, barre degli strumenti e caselle combinate.|  
  
## Esempio  
  
```  
<Define name="DEMO_UI"/> <Define name="MODE" value="Standard"/>  
```  
  
## Vedere anche  
 [Tabella di comandi di Visual Studio \(. File Vsct\)](../extensibility/internals/visual-studio-command-table-dot-vsct-files.md)