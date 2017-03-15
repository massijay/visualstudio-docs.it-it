---
title: "CA1301: Evitare tasti di scelta rapida duplicati | Microsoft Docs"
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
  - "CA1301"
  - "AvoidDuplicateAccelerators"
helpviewer_keywords: 
  - "CA1301"
  - "AvoidDuplicateAccelerators"
ms.assetid: 20570a00-864b-459c-a1fa-a6e9db5f1001
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1301: Evitare tasti di scelta rapida duplicati
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|AvoidDuplicateAccelerators|  
|CheckId|CA1301|  
|Category|Microsoft.Globalization|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo estende <xref:System.Windows.Forms.Control?displayProperty=fullName> e contiene due o più controlli di primo livello con tasti di scelta identici archiviati in un file di risorse.  
  
## Descrizione della regola  
 Un tasto di scelta o tasto di scelta rapida consente l'accesso da tastiera a un controllo mediante ALT.  Quando più controlli presentano tasti di scelta duplicati, il comportamento del tasto di scelta non è ben definito.  È possibile che l'utente non sia in grado di accedere al controllo desiderato utilizzando il tasto di scelta e che attivi un controllo diverso.  
  
 L'implementazione attuale di questa regola ignora le voci di menu.  Le voci di menu presenti nello stesso sottomenu non devono, tuttavia, presentare tasti di scelta identici.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, definire tasti di scelta univoci per tutti i controlli.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrato un form minimo contenente due controlli con tasti di scelta identici.  I tasti sono archiviati in un file di risorse che non è indicato; i relativi valori, tuttavia, sono contenuti nelle righe impostate come commento di `checkBox.Text`.  Il comportamento dei tasti di scelta rapida duplicati può essere esaminato scambiando le righe di `checkBox.Text` con le parti corrispondenti impostate come commenti.  In questo caso, non verrà generato un avviso dalla regola.  
  
 [!code-cs[FxCop.Globalization.AvoidDuplicateAccels#1](../code-quality/codesnippet/CSharp/ca1301-avoid-duplicate-accelerators_1.cs)]  
  
## Vedere anche  
 <xref:System.Resources.ResourceManager?displayProperty=fullName>   
 [Risorse nelle applicazioni desktop](../Topic/Resources%20in%20Desktop%20Apps.md)