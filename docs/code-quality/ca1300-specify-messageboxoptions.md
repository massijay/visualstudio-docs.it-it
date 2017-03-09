---
title: "CA1300: Specificare MessageBoxOptions | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "SpecifyMessageBoxOptions"
  - "CA1300"
helpviewer_keywords: 
  - "SpecifyMessageBoxOptions"
  - "CA1300"
ms.assetid: 9357a724-026e-4a3d-a03a-f14635064ec6
caps.latest.revision: 19
caps.handback.revision: 19
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1300: Specificare MessageBoxOptions
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|SpecifyMessageBoxOptions|  
|CheckId|CA1300|  
|Category|Microsoft.Globalization|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un metodo chiama un overload del metodo <xref:System.Windows.Forms.MessageBox.Show%2A?displayProperty=fullName> che non accetta un argomento <xref:System.Windows.Forms.MessageBoxOptions?displayProperty=fullName>.  
  
## Descrizione della regola  
 Per visualizzare correttamente una finestra di messaggio per le impostazioni cultura che utilizzano un ordine di lettura da destra a sinistra, è necessario passare i membri <xref:System.Windows.Forms.MessageBoxOptions> e <xref:System.Windows.Forms.MessageBoxOptions> dell'enumerazione <xref:System.Windows.Forms.MessageBoxOptions> al metodo <xref:System.Windows.Forms.MessageBox.Show%2A>.  Esaminare la proprietà <xref:System.Windows.Forms.Control.RightToLeft%2A?displayProperty=fullName> del controllo contenitore per determinare se utilizzare un ordine di lettura da destra a sinistra.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, chiamare un overload del metodo <xref:System.Windows.Forms.MessageBox.Show%2A> che accetta un argomento <xref:System.Windows.Forms.MessageBoxOptions>.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura quando la libreria di codice non verrà localizzata per impostazioni cultura che utilizzano l'ordine di lettura da destra a sinistra.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un metodo che visualizza una finestra di messaggio con le opzioni appropriate per l'ordine di lettura delle impostazioni cultura.  Per compilare l'esempio è necessario un file di risorse che non è indicato.  Seguire i commenti riportati nell'esempio per compilare l'esempio senza un file di risorse e verificare la funzionalità da destra a sinistra.  
  
 [!code-vb[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/VisualBasic/ca1300-specify-messageboxoptions_1.vb)]
 [!code-cs[FxCop.Globalization.SpecifyMBOptions#1](../code-quality/codesnippet/CSharp/ca1300-specify-messageboxoptions_1.cs)]  
  
## Vedere anche  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [Risorse nelle applicazioni desktop](../Topic/Resources%20in%20Desktop%20Apps.md)