---
title: "Elemento CustomParameters (modelli di Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameters"
helpviewer_keywords: 
  - "CustomParameters (elemento) [modelli di progetto Visual Studio]"
ms.assetid: cf3efc91-1532-4022-bbb8-a18658424fee
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento CustomParameters (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Raggruppa i parametri personalizzati che devono essere passati alla creazione guidata modelli quando la procedura guidata effettua le sostituzioni di parametro.  
  
## Sintassi  
  
```  
<CustomParameters>  
    <CustomParameter/>  
    <CustomParameter/>  
</CustomParameters>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
 Nessuno.  
  
### Elementi figlio  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[CustomParameter](../extensibility/customparameter-element-visual-studio-templates.md)|Elemento facoltativo.<br /><br /> Contiene un nome di parametro personalizzato e il valore da utilizzare quando viene creato un progetto o un elemento dal modello. Possono esistere zero o più elementi `CustomParameter` in un elemento `CustomParameters`.|  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[TemplateContent](../extensibility/templatecontent-element-visual-studio-templates.md)|Specifica il contenuto del modello.|  
  
## Note  
  
## Esempio  
 Nell'esempio seguente viene illustrato come utilizzare diversi parametri personalizzati in un modello. Quando viene creato un progetto o un elemento da un modello con i seguenti parametri personalizzati, tutte le istanze di `$color1$` e `$color2$` nel modello di file verranno sostituiti con `Red` e `Blue`, rispettivamente.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## Vedere anche  
 [Elemento CustomParameter \(modelli di Visual Studio\)](../extensibility/customparameter-element-visual-studio-templates.md)   
 [Parametri di template](../ide/template-parameters.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)