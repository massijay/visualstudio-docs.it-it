---
title: "CA2232: Contrassegnare i punti di ingresso del Windows Form con STAThread | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "MarkWindowsFormsEntryPointsWithStaThread"
  - "CA2232"
helpviewer_keywords: 
  - "CA2232"
  - "MarkWindowsFormsEntryPointsWithStaThread"
ms.assetid: a3c95130-8e7f-4419-9fcd-b67d077e8efb
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 16
---
# CA2232: Contrassegnare i punti di ingresso del Windows Form con STAThread
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|MarkWindowsFormsEntryPointsWithStaThread|  
|CheckId|CA2232|  
|Category|Microsoft.Usage|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un assembly fa riferimento allo spazio dei nomi <xref:System.Windows.Forms> e il relativo punto di ingresso non è contrassegnato con l'attributo <xref:System.STAThreadAttribute?displayProperty=fullName>.  
  
## Descrizione della regola  
 <xref:System.STAThreadAttribute> indica che il modello di threading COM per l'applicazione è apartment a thread singolo.  Questo attributo deve essere presente sul punto di ingresso di qualsiasi applicazione che utilizza Windows Form; se omesso è possibile che il componente Windows non funzioni correttamente.  Se l'attributo non è presente, l'applicazione utilizza il modello apartment multithreading, non supportato da Windows Form.  
  
> [!NOTE]
>  Per progetti [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)] che utilizzano il framework applicazione non è necessario contrassegnare il metodo **Main** con STAThread.  Tale operazione viene effettuata automaticamente dal compilatore [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)].  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, aggiungere l'attributo <xref:System.STAThreadAttribute> al punto di ingresso.  Se l'attributo <xref:System.MTAThreadAttribute?displayProperty=fullName> è presente, rimuoverlo.  
  
## Esclusione di avvisi  
 L'esclusione di un avviso da questa regola è sicura in caso di sviluppo per .NET Compact Framework, per cui l'attributo <xref:System.STAThreadAttribute> non è necessario e non è supportato.  
  
## Esempio  
 Negli esempi riportati di seguito viene illustrato l'utilizzo corretto di <xref:System.STAThreadAttribute>.  
  
 [!code-cs[FxCop.Usage.StaThread#1](../code-quality/codesnippet/CSharp/ca2232-mark-windows-forms-entry-points-with-stathread_1.cs)]
 [!code-vb[FxCop.Usage.StaThread#1](../code-quality/codesnippet/VisualBasic/ca2232-mark-windows-forms-entry-points-with-stathread_1.vb)]