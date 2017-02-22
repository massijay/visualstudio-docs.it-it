---
title: "Elemento TemplateGroupID (modelli di Visual Studio) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/developer/vstemplate/2005#TemplateGroupID"
helpviewer_keywords: 
  - "<TemplateGroupID> (elemento) [modelli di Visual Studio]"
  - "TemplateGroupID (elemento) [modelli di Visual Studio]"
ms.assetid: bce7b49a-90bc-4691-aff3-a87e209f6d83
caps.latest.revision: 18
caps.handback.revision: 18
ms.author: "gregvanl"
manager: "ghogen"
---
# Elemento TemplateGroupID (modelli di Visual Studio)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Specifica il tipo di progetto in cui verranno visualizzati i modelli di elemento.  Questo elemento è significativo quando [ShowByDefault \(modelli di Visual Studio\)](../extensibility/showbydefault-visual-studio-templates.md) è impostato su `false`.  Quando [ShowByDefault \(modelli di Visual Studio\)](../extensibility/showbydefault-visual-studio-templates.md) è impostato su `true`, un modello di elemento è disponibile in tutti i tipi di progetto.  
  
## Sintassi  
  
```  
<TemplateGroupID> ... </TemplateGroupID>  
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
|[TemplateData](../extensibility/templatedata-element-visual-studio-templates.md)|Classifica il modello in base alla categoria e definisce la modalità di visualizzazione nella finestra di dialogo **Nuovo progetto** o **Aggiungi nuovo elemento**.|  
  
## Valore di testo  
 È necessario specificare un valore di testo.  
  
 Il testo specifica un identificatore per una categoria di modelli di elemento.  
  
## Note  
 `TemplateGroupID` è un elemento.  
  
 Il valore dell'elemento `TemplateGroupID` viene usato con la registrazione del sistema di progetto \(HKEY\_LOCAL\_MACHINE\\SOFTWARE\\Microsoft\\VisualStudio\\*\< numero di versione \>*\\Projects\\\) per modelli di filtro che vengono visualizzati nella finestra di dialogo **Aggiungi nuovo elemento**.  
  
|Valore di Visual C\+\+|Significato|  
|----------------------------|-----------------|  
|VC\-Native|Usato nei progetti nativi.  È anche il valore predefinito se non è possibile determinare un tipo di progetto.|  
|VC\-Managed|Usato per i progetti \(\/clr\) gestiti|  
|VC\-Windows|Usato per tutti i progetti per la piattaforma Windows \(nativi\/gestiti\/Store\)|  
|WinRT\-Native\-UAP|Usato per i progetti Store di Windows 10|  
|CodeSharing\-Native|Usato per i progetti di elementi condivisi|  
|WinRT\-Native\-6.3|Usato per i progetti Store di Windows 8.1|  
|WinRT\-Native\-Phone\-6.3|Usato per i progetti Windows Phone 8.1|  
|WinRT\-Nativo|Usato per i progetti Store di Windows 8.0|  
|VC\-Android|Usato per i progetti Android|  
  
## Vedere anche  
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)