---
title: "MSBuild Error MSB3155 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MSBuild.GenerateBootstrapper.ProductNotFound"
helpviewer_keywords: 
  - "MSB3155"
ms.assetid: 59bf2293-ef13-4bb1-8f29-5d6966bbe313
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# MSBuild Error MSB3155
**Errore MSB3155 di MSBuild: impossibile trovare l'elemento '\<package\>' in '\<percorso\>'.**  
  
 Questo avviso viene visualizzato quando nella cache del programma di avvio automatico non viene individuato un package con la proprietà <xref:Microsoft.Build.Tasks.Deployment.Bootstrapper.Product.ProductCode%2A> specificata.  
  
> [!NOTE]
>  I componenti MDAC \(Microsoft Data Access Components\) non sono più inclusi come pacchetto di programma di avvio automatico.  Possono essere scaricati dal sito Web Microsoft [Microsoft Windows Update](http://go.microsoft.com/fwlink/?LinkId=86676).  
  
### Per correggere l'errore  
  
-   Rimuovere il package dall'elenco di package da installare o aggiungere il package alla cache.  Accertarsi inoltre che il manifesto sia formattato correttamente con tag XML validi.  
  
## Vedere anche  
 [Riferimenti dello schema di prodotti e package](../deployment/product-and-package-schema-reference.md)   
 [Elemento \<PackageFiles\>](../deployment/packagefiles-element-bootstrapper.md)   
 [Finestra di dialogo Prerequisiti](../ide/reference/prerequisites-dialog-box.md)   
 [Creazione di programmi di avvio automatico](../deployment/creating-bootstrapper-packages.md)