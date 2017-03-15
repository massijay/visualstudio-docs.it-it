---
title: "Elemento CustomParameter (modelli di Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#CustomParameter"
helpviewer_keywords: 
  - "CustomParameters (elemento) [modelli di progetto Visual Studio]"
ms.assetid: 743c4489-74ac-403a-bbaa-eed7d785a3ac
caps.latest.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 6
---
# Elemento CustomParameter (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Contiene il nome e il valore di un parametro personalizzato da utilizzare quando dal modello viene creato un progetto o un elemento.  
  
## Sintassi  
  
```  
<CustomParameter Name="name" Value="value">  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
  
|Attributo|Descrizione|  
|---------------|-----------------|  
|`Name`|Necessario.  Nome del parametro.  Il formato per i parametri è $*name*$.|  
|`Value`|Necessario.  Il valore di sostituzione per il parametro.|  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[CustomParameters](../extensibility/customparameters-element-visual-studio-templates.md)|Raggruppa i parametri personalizzati che dovranno essere passati alla creazione guidata modelli quando la creazione guidata effettua la sostituzione dei parametri.|  
  
## Note  
 Quando un modello contiene elementi `CustomParameter`, ogni istanza dell'attributo `Name` verrà sostituita con l'attributo `Value` nei file creati per il progetto o per l'elemento.  
  
## Esempio  
 Nell'esempio riportato di seguito viene mostrato come utilizzare in un modello più parametri personalizzati.  Quando un progetto o un elemento viene creato da un modello con i seguenti parametri personalizzati, tutte le istanze di `$color1$` e `$color2$` nei file del modello verranno sostituite rispettivamente da `Red` e `Blue`.  
  
```  
<CustomParameters>  
    <CustomParameter Name="$color1$" Value="Red"/>  
    <CustomParameter Name="$color2$" Value="Blue "/>  
</CustomParameters>  
```  
  
## Vedere anche  
 [Elemento CustomParameters \(modelli di Visual Studio\)](../extensibility/customparameters-element-visual-studio-templates.md)   
 [Parametri di template](../ide/template-parameters.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)