---
title: "Elemento ProvideDefaultName (modelli di Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/developer/vstemplate/2005#ProvideDefaultName"
helpviewer_keywords: 
  - "ProvideDefaultName (elemento) [modelli di progetto Visual Studio]"
ms.assetid: 7b0e7b20-fd6b-42e2-81d0-e5100cea0528
caps.latest.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 12
---
# Elemento ProvideDefaultName (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica se il sistema del progetto di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] genererà un nome predefinito per il modello nella finestra di dialogo **Aggiungi nuovo elemento** o **Nuovo progetto**.  
  
## Sintassi  
  
```  
<ProvideDefaultName> true/false </ProvideDefaultName>  
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
  
 Il valore del testo deve essere `true` o `false`, ad indicare se nella finestra di dialogo **Aggiungi nuovo elemento** o **Nuovo progetto** verrà generato un nome predefinito per il modello.  
  
## Note  
 `ProvideDefaultName` è un elemento facoltativo.  Il valore predefinito è `true`.  
  
 Se l'elemento `ProvideDefaultName` è impostato su `false`, le caselle **Nome** nelle finestre di dialogo **Aggiungi nuovo elemento**  e **Nuovo progetto** conterranno il valore `<Immettere il nome>`.  
  
 Utilizzare l'elemento [DefaultName](../extensibility/defaultname-element-visual-studio-templates.md) per specificare il nome predefinito del progetto o dell'elemento nelle finestre di dialogo **Aggiungi nuovo elemento** e **Nuovo progetto**.  
  
## Esempio  
 Nel codice di esempio riportato di seguito, l'elemento `ProvideDefaultName` viene impostato su `false`.  
  
```  
<VSTemplate Type="Item" Version="3.0.0"  
    xmlns="http://schemas.microsoft.com/developer/vstemplate/2005">  
    <TemplateData>  
        <Name>MyClass</Name>  
        <Description>My custom C# class.</Description>  
        <Icon>Icon.ico</Icon>  
        <ProjectType>CSharp</ProjectType>  
        <ProvideDefaultName>false</ProvideDefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
## Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)