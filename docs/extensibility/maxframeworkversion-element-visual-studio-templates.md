---
title: "Elemento MaxFrameworkVersion (modelli di Visual Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "<MaxFrameworkVersion> (elemento) (modelli di Visual Studio)"
  - "Elemento MaxFrameworkVersion (modelli di Visual Studio)"
ms.assetid: f732a9d3-fc29-405b-9298-01ea83fc58b8
caps.latest.revision: 9
ms.author: "gregvanl"
manager: "ghogen"
caps.handback.revision: 9
---
# Elemento MaxFrameworkVersion (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica la versione massima di .NET Framework richiesta dal modello.  Determina se il modello verrà visualizzato nella sezione **Modelli** della finestra di dialogo **Aggiungi nuovo progetto**, in base al valore selezionato nella casella **Versione di .NET Framework di destinazione** della finestra di dialogo **Aggiungi nuovo progetto**.  
  
## Sintassi  
  
```  
<MaxFrameworkVersion> ... </MaxFrameworkVersion>  
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
  
 Il valore del testo deve essere il numero della versione più recente di .NET Framework consentito dal modello.  
  
## Note  
 `MaxFrameworkVersion` è un elemento facoltativo.  L'elemento nella sezione `TemplateData` del file .vstemplate che funge da filtro per la sezione di **Modelli** della finestra di dialogo **Aggiungi nuovo progetto**.  Solo i modelli i cui requisiti .NET Framework sono inferiori ai valori dell'elemento `MaxFrameworkVersion` saranno visualizzati, in base al valore selezionato nella casella **Versione di .NET Framework di destinazione** della finestra di dialogo **Aggiungi nuovo progetto**.  L'elemento `MaxFrameworkVersion` deve essere omesso, a meno che non sia necessario, per fare sì che i modelli non vengano visualizzati inavvertitamente quando vengono utilizzati con le versioni più recenti di .NET Framework.  
  
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
        <MaxFrameworkVersion>3.5</MaxFrameworkVersion>  
        <DefaultName>MyClass</DefaultName>  
    </TemplateData>  
    <TemplateContent>  
        <ProjectItem>MyClass.cs</ProjectItem>  
    </TemplateContent>  
</VSTemplate>  
```  
  
 In questo esempio, la versione massima di .NET Framework richiesta dal modello, rappresentata da `MaxFrameworkVersion`, è la 3.5.  Il modello riportato sopra verrà visualizzato solo quando si seleziona 3.0 o 3.5 nella casella **Versione di .NET Framework di destinazione** nella finestra di dialogo **Aggiungi nuovo progetto**.  
  
## Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)