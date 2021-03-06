---
title: "Il membro &#39;&lt;nomemembro&gt;&#39; &#232; in conflitto con il membro &#39;&lt;nomemembro&gt;&#39; nel tipo di base &#39;&lt;nometipobase&gt;&#39;, quindi non deve essere dichiarato &#39;Overloads&#39; | Microsoft Docs"
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
  - "bc40021"
  - "vbc40021"
helpviewer_keywords: 
  - "BC40021"
ms.assetid: 2ec72726-ab0e-4545-9c1e-2409eb54482e
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Il membro &#39;&lt;nomemembro&gt;&#39; &#232; in conflitto con il membro &#39;&lt;nomemembro&gt;&#39; nel tipo di base &#39;&lt;nometipobase&gt;&#39;, quindi non deve essere dichiarato &#39;Overloads&#39;
Una proprietà o routine usa la parola chiave [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) per dichiarare nuovamente una proprietà o routine esistente con lo stesso nome, ma la proprietà o routine esistente si trova nella classe base.  
  
 L'overload viene usato per definire più versioni di una proprietà o routine tutte appartenenti alla stessa classe. Non è possibile definire un'ulteriore versione del membro di una classe base a meno che questo non specifichi già [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads).  
  
 Per impostazione predefinita, si tratta di un messaggio di avviso. Per altre informazioni su come nascondere gli avvisi o considerarli come errori, vedere [Configurazione degli avvisi in Visual Basic](../ide/configuring-warnings-in-visual-basic.md).  
  
 **ID errore:** BC40021  
  
### Per correggere l'errore  
  
-   Se si vuole definire un'ulteriore versione del membro di una classe base e accedere al codice sorgente della classe stessa, aggiungere la parola chiave [Overloads](/dotnet/visual-basic/language-reference/modifiers/overloads) alla definizione della classe base.  
  
-   Se non si hanno i diritti di accesso al codice sorgente della classe base, non è possibile eseguire l'overload del membro in una classe derivata. Rimuovere la parola chiave `Overloads`.  
  
-   Se si vuole sostituire il membro della classe base anziché definirne un'ulteriore versione, usare la parola chiave [Overrides](/dotnet/visual-basic/language-reference/modifiers/overrides)invece di `Overloads`.  
  
-   Se si vuole nascondere il membro della classe base con un nuovo membro nella classe derivata, usare la parola chiave [Shadows](/dotnet/visual-basic/language-reference/modifiers/shadows) invece di `Overloads`.  
  
## Vedere anche  
 [Procedure Overloading](/dotnet/visual-basic/programming-guide/language-features/procedures/procedure-overloading)   
 [Inheritance Basics](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)