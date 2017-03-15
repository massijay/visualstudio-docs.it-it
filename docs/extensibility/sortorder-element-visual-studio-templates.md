---
title: "Elemento SortOrder (modelli di Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#SortOrder"
helpviewer_keywords: 
  - "<SortOrder> (elemento) [modelli di Visual Studio]"
  - "SortOrder (elemento) [modelli di Visual Studio]"
ms.assetid: 151932c1-f08a-4f78-a8d0-bd2f32211a9c
caps.latest.revision: 10
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 10
---
# Elemento SortOrder (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica un valore che viene utilizzato per disporre il modello, tra gli altri modelli della stessa categoria, come verrà visualizzato nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento**.  
  
## Sintassi  
  
```  
<SortOrder> ... </SortOrder>  
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
  
 Un `integer` che rappresenta il valore del criterio di ordinamento.  
  
## Note  
 `SortOrder` è un elemento facoltativo.  Il valore predefinito è 100 e tutti i valori devono essere multipli di 10.  
  
 L'elemento `SortOrder` viene ignorato nei modelli creati dall'utente.  Tutti i modelli creati dall'utente vengono disposti in ordine alfabetico.  
  
 I modelli con un valore basso per il criterio di ordinamento vengono visualizzati nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento** prima dei modelli con valori di ordinamento alti.  
  
## Esempio  
 Nell'esempio riportato di seguito vengono illustrati i metadati per un modello di classe standard di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)].  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class template.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <SortOrder>290</SortOrder>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 In questo esempio, l'elemento `SortOrder` è relativamente alto.  È probabile che altri modelli di elemento di [!INCLUDE[csprcs](../data-tools/includes/csprcs_md.md)] abbiano un valore `SortOrder` inferiore a `290` e quindi nella finestra di dialogo **Nuovo elemento** verranno visualizzati prima di questo modello.  
  
## Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)