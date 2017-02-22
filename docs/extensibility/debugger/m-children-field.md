---
title: "m_children campo | Microsoft Docs"
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
  - "campo m_children, ContingentProperties classe [motori di debug di .NET Framework]"
ms.assetid: 0a3b5653-7bc0-4a7a-8963-9020bc52b9cb
caps.latest.revision: 12
caps.handback.revision: 12
ms.author: "gregvanl"
manager: "ghogen"
---
# m_children campo
[!INCLUDE[vs2017banner](../../code-quality/includes/vs2017banner.md)]

L'elenco di attività figlio che sono registrati con questa attività.  
  
 **Spazio dei nomi:** <xref:System.Threading.Tasks?displayProperty=fullName>  
  
 **Assembly:** mscorlib \(in mscorlib. dll\)  
  
 Poiché è possibile accedere a questo membro interno di .NET Framework, la sintassi seguente viene fornita in comune Intermediate Language \(CIL\).  
  
## Sintassi  
  
```  
.field public class System.Collections.Generic.List`1<class System.Threading.Tasks.Task> m_children  
```  
  
## Note  
 Durante l'esecuzione dell'attività, solo il thread che esegue l'attività deve accedere a questa matrice.  
  
 Se l'attività è completata, altri thread possa accedere in questo campo, purché non aggiunge nulla al né rimuovere qualsiasi elemento da esso.  
  
## Vedere anche  
 [Classe ContingentProperties](../../extensibility/debugger/contingentproperties-class-internal-members.md)