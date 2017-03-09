---
title: "Uso inappropriato della parola chiave &#39;&lt;parolachiave&gt;&#39; in un modulo | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc42028"
  - "BC42028"
helpviewer_keywords: 
  - "BC42028"
ms.assetid: a9bc1e9d-ba2c-4a71-b147-0fb66f670316
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Uso inappropriato della parola chiave &#39;&lt;parolachiave&gt;&#39; in un modulo
I moduli non contengono istanze, non supportano l'ereditarietà, né implementano le interfacce. Per questo motivo, le parole chiave che seguono non sono applicabili alla dichiarazione di un modulo:  
  
-   [MustInherit](/dotnet/visual-basic/language-reference/modifiers/mustinherit)  
  
-   [NotInheritable](/dotnet/visual-basic/language-reference/modifiers/notinheritable)  
  
-   [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads)  
  
-   [Private](/dotnet/visual-basic/language-reference/modifiers/private)  
  
-   [Protected](/dotnet/visual-basic/language-reference/modifiers/protected)  
  
-   [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows)  
  
-   [Shared](/dotnet/visual-basic/language-reference/modifiers/shared)  
  
-   [Static](/dotnet/visual-basic/language-reference/modifiers/static)  
  
 Le uniche parole chiave supportate in un'[Module Statement](/dotnet/visual-basic/language-reference/statements/module-statement) sono [Public](/dotnet/visual-basic/language-reference/modifiers/public) e [Friend](/dotnet/visual-basic/language-reference/modifiers/friend).  
  
 Inoltre, non è possibile usare l'istruzione [Implements](/dotnet/visual-basic/language-reference/statements/implements-clause) o l'[Inherits Statement](/dotnet/visual-basic/language-reference/statements/inherits-statement) nel blocco di istruzioni del modulo.  
  
 Per impostazione predefinita, si tratta di un messaggio di avviso. Per altre informazioni su come nascondere gli avvisi o considerarli come errori, vedere [Configurazione degli avvisi in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID errore:** BC42028  
  
### Per correggere l'errore  
  
-   Se si vuole che questo elemento di programmazione sia un modulo, nella sua dichiarazione usare solo la parola chiave `Public` o `Friend`. Se non si specifica il livello di accesso di un modulo la sua impostazione predefinita sarà `Friend`.  
  
-   Se si vogliono creare delle istanze di questo elemento di programmazione, dichiararlo come classe. Successivamente sarà possibile usare le parole chiave che si applicano a una dichiarazione di classe.  
  
## Vedere anche  
 [Class Statement](/dotnet/visual-basic/language-reference/statements/class-statement)