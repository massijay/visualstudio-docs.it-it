---
title: "Classe ContingentProperties - membri interni | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-sdk"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Classe ContingentProperties [motori di debug di .NET Framework]"
  - "motori di debug, ContingentProperties (classe) [.NET Framework]"
ms.assetid: c49d1362-ab1c-4b6d-9950-fcae40e0e66b
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# Classe ContingentProperties - membri interni
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

Contiene proprietà aggiuntive per un <xref:System.Threading.Tasks.Task> oggetto.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib \(in mscorlib. dll\)  
  
 Poiché è possibile accedere a questi membri interni di .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language \(CIL\).  
  
## Sintassi  
  
```  
.class auto ansi nested assembly beforefieldinit ContingentProperties  
       extends System.Object  
```  
  
## Membri  
  
### Campi  
  
|Nome|Descrizione|  
|----------|-----------------|  
|[m\_children](../../extensibility/debugger/m-children-field.md)|L'elenco di attività figlio che sono registrati con questa attività.|  
  
## Note  
 .NET Framework Inizializza i campi di questa classe solo quando sono necessari.  
  
## Vedere anche  
 [Elementi interni di estensione parallela per .NET Framework](../../extensibility/debugger/parallel-extension-internals-for-the-dotnet-framework.md)