---
title: "Procedura: sostituire i parametri di un modello | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "parametri di modelli, sostituzione"
  - "modelli di Visual Studio, utilizzo di parametri"
ms.assetid: a62924a7-4ba0-413d-b606-fdbe1fcf2807
caps.latest.revision: 14
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 14
---
# Procedura: sostituire i parametri di un modello
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile sostituire i parametri di modello, ad esempio gli spazi dei nomi e i nomi delle classi, quando viene creato un file basato su un modello.  Per un elenco completo dei parametri di modello, vedere [Parametri di template](../ide/template-parameters.md).  
  
## Routine  
 È possibile sostituire i parametri nei file di un modello ogni volta che viene creato un progetto basato su tale modello.  Questa procedura illustra come creare un modello che sostituisce il nome di uno spazio dei nomi con il nome di progetto sicuro quando viene creato un nuovo progetto con il modello.  
  
#### Per usare un parametro per sostituire il nome dello spazio dei nomi con il nome del progetto  
  
1.  Inserire il parametro in uno o più dei file di codice nel modello.  Ad esempio:  
  
    ```  
    namespace $safeprojectname$  
    ```  
  
    > [!NOTE]
    >  I parametri del modello vengono scritti nel formato $*parametro*$.  
  
2.  Nel file con estensione vstemplate del modello individuare l'elemento `ProjectItem` che include il file.  
  
3.  Impostare l'attributo `ReplaceParameters` su `true` per l'elemento `ProjectItem`.  Ad esempio:  
  
    ```  
    <ProjectItem ReplaceParameters="true">Class1.cs</ProjectItem>  
    ```  
  
## Vedere anche  
 [Creazione di un progetto e di modelli di elemento personalizzati](../ide/creating-project-and-item-templates.md)   
 [Parametri di template](../ide/template-parameters.md)   
 [Riferimenti allo schema dei modelli di Visual Studio](../extensibility/visual-studio-template-schema-reference.md)   
 [Elemento ProjectItem \(modelli di elementi di Visual Studio\)](../extensibility/projectitem-element-visual-studio-item-templates.md)