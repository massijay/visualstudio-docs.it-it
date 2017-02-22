---
title: "Elemento CustomDataSignature (modelli di Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<CustomDataSignature> (elemento) (modelli di Visual Studio)"
  - "Elemento CustomDataSignature (modelli di Visual Studio)"
ms.assetid: 8c3db51d-7014-4484-802a-15aa1353dbdb
caps.latest.revision: 6
caps.handback.revision: 6
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento CustomDataSignature (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica la firma del testo per individuare i dati personalizzati.  
  
## Sintassi  
  
```  
<CustomDataSignature>"string"</CustomDataSignature>  
```  
  
## Attributi ed elementi  
 Nelle sezioni seguenti vengono descritti gli attributi, gli elementi figlio e gli elementi padre.  
  
### Attributi  
 Nessuno.  
  
### Elementi figlio  
 Nessuno.  
  
### Elementi padre  
  
|Elemento|Descrizione|  
|--------------|-----------------|  
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Elemento obbligatorio.<br /><br /> Classifica il modello e definisce la modalità di visualizzazione per la finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento**.|  
  
## Valore di testo  
 È necessario specificare un valore di testo.  
  
 Il testo è una stringa che ha la firma necessaria per individuare i dati personalizzati.  
  
## Note  
 `CustomDataSignature` è un elemento facoltativo.  
  
## Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)