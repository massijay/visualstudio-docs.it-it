---
title: "T4 Import Directive | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 713ca975-b9aa-4210-bf6d-b7660f5b193b
caps.latest.revision: 3
caps.handback.revision: 3
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# T4 Import Directive
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Nei blocchi di codice di un modello di testo T4 di [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], la direttiva `import` consente di fare riferimento agli elementi in un altro spazio dei nomi senza fornire un nome completo.  È l'equivalente di `using` in C\# o di `imports` in [!INCLUDE[vb_current_short](../debugger/includes/vb_current_short_md.md)].  
  
 Per cenni preliminari sulla scrittura dei modelli di testo T4, vedere [Writing a T4 Text Template](../modeling/writing-a-t4-text-template.md).  
  
## Utilizzo della direttiva Import  
  
```  
<#@ import namespace="namespace" #>  
```  
  
 In questo esempio, il codice del modello può omettere uno spazio dei nomi esplicito per i membri di System.IO:  
  
```  
<#@ import namespace="System.IO" #>  
<#   
   string fileContent = File.ReadAllText("C:\x.txt"); // System.IO.File  
#>   
The file contains: <#=  fileContent #>  
```  
  
## Importazioni standard  
 Lo spazio dei nomi seguente viene importato automaticamente, in modo che non sia necessario scrivere una direttiva di importazione:  
  
-   `System`  
  
 Inoltre, se si utilizza una direttiva personalizzata, il processore di direttiva potrebbe importare alcuni spazi dei nomi automaticamente.  
  
 Ad esempio, se si scrivono modelli per un linguaggio specifico di dominio \(DSL\), non è necessario scrivere direttive di importazione per gli spazi dei nomi seguenti:  
  
-   `Microsoft.VisualStudio.Modeling`  
  
-   Lo spazio dei nomi del linguaggio DSL  
  
## Vedere anche  
 [T4 Assembly Directive](../modeling/t4-assembly-directive.md)