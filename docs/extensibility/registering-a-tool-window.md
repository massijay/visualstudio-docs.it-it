---
title: "Registrazione di una finestra degli strumenti | Microsoft Docs"
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
  - "finestre degli strumenti, la registrazione di gestito"
  - "finestre degli strumenti, la registrazione"
ms.assetid: 8c8c4a24-3da4-497b-9db2-0ddd7cfbfdd2
caps.latest.revision: 14
caps.handback.revision: 14
ms.author: "gregvanl"
manager: "ghogen"
---
# Registrazione di una finestra degli strumenti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

È possibile registrare le finestre degli strumenti mediante <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> e  <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowVisibilityAttribute>  
  
## Esempio  
  
```c#  
  
      [ProvideToolWindow(typeof(PersistedWindowPane), Style = MsVsShell.VsDockStyle.Tabbed, Window = "3ae79031-e1bc-11d0-8f78-00a0c9110057")] [ProvideToolWindow(typeof(DynamicWindowPane), PositionX=250, PositionY=250, Width=160, Height=180, Transient=true)] [ProvideToolWindowVisibility(typeof(DynamicWindowPane), /*UICONTEXT_SolutionExists*/"f1536ef8-92ec-443c-9ed7-fdadf150da82")]  
[ProvideMenuResource(1000, 1)]  
[PackageRegistration(UseManagedResourcesOnly = true)]  
[Guid("01069CDD-95CE-4620-AC21-DDFF6C57F012")]  
public class PackageToolWindow : Package  
{  
```  
  
 Nel codice precedente, il <xref:Microsoft.VisualStudio.Shell.ProvideToolWindowAttribute> Registra le finestre degli strumenti PersistedWindowPane e DynamicWindowPane con Visual Studio. La finestra degli strumenti persistente è ancorata e schede con **Esplora**, e la finestra dinamica è stata assegnata un inizio posizione e le dimensioni predefinite. La finestra dinamica è temporanea, che indica che non viene creato all'avvio. Scrive un valore DontForceCreate nella chiave ToolWindows nel Registro di sistema. Per altre informazioni, vedere [Configurazione visualizzazione finestra dello strumento](../extensibility/tool-window-display-configuration.md).