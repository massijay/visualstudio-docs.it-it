---
title: "T4 Text Template Directives | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-tfs-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "text templates, import directive"
  - "text templates, include directive"
  - "text templates, assembly directive"
  - "text templates, output directive"
  - "text templates, directives"
  - "text templates, template directive"
ms.assetid: 6898ee02-ebb2-4635-a4e9-350774c13cf2
caps.latest.revision: 81
caps.handback.revision: 81
author: "alancameronwills"
ms.author: "awills"
manager: "douge"
---
# T4 Text Template Directives
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

Le direttive forniscono istruzioni al motore di trasformazione del modello di testo.  
  
 La sintassi per le direttive è la seguente:  
  
```  
<#@ DirectiveName [AttributeName = "AttributeValue"] ... #>  
```  
  
 Tutti i valori di attributo devono essere racchiusi tra virgolette doppie.  Se il valore stesso contiene virgolette, è necessario applicare loro il carattere di escape \\.  
  
 Le direttive sono in genere i primi elementi di un file modello o di un file incluso.  Tali elementi non devono essere inseriti in un blocco di codice `<#...#>`, né dopo un blocco della funzionalità di classe `<#+...#>`.  
  
 [T4 Template Directive](../modeling/t4-template-directive.md)  
 ```  
<#@ template [language="VB"] [hostspecific="true|TrueFromBase"] [debug="true"] [inherits="templateBaseClass"] [culture="code"] [compilerOptions="options"] [visibility="internal"] [linePragmas="false"] #>  
```  
  
 [T4 Parameter Directive](../modeling/t4-parameter-directive.md)  
 ```  
<#@ parameter type="Full.TypeName" name="ParameterName" #>  
```  
  
 [T4 Output Directive](../modeling/t4-output-directive.md)  
 ```  
<#@ output extension=".fileNameExtension" [encoding="encoding"] #>  
```  
  
 [T4 Assembly Directive](../modeling/t4-assembly-directive.md)  
 ```  
<#@ assembly name="[assembly strong name|assembly file name]" #>  
```  
  
 [T4 Import Directive](../modeling/t4-import-directive.md)  
 ```  
<#@ import namespace="namespace" #>  
```  
  
 [T4 Include Directive](../modeling/t4-include-directive.md)  
 ```  
<#@ include file="filePath" #>  
```  
  
 [Direttiva T4 CleanUpBehavior](../modeling/t4-cleanupbehavior-directive.md)  
 ```  
<#@ CleanupBehavior processor="T4VSHost" CleanupAfterProcessingtemplate="true" #>  
```  
  
 È inoltre possibile creare direttive personalizzate.  Per ulteriori informazioni, vedere [Creating Custom T4 Text Template Directive Processors](../modeling/creating-custom-t4-text-template-directive-processors.md).  Se si utilizza l'SDK di visualizzazione e modellazione per creare un linguaggio specifico di dominio \(DSL\), verrà generato un processore di direttiva come parte di tale linguaggio DSL.