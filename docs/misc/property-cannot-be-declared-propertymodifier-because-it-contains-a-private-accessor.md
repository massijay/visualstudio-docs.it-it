---
title: "La propriet&#224; non pu&#242; essere dichiarata come &#39;&lt;modificatorepropriet&#224;&gt;&#39; perch&#233; contiene una funzione di accesso &#39;Private&#39; | Microsoft Docs"
ms.custom: ""
ms.date: "11/24/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbc31108"
  - "bc31108"
helpviewer_keywords: 
  - "BC31108"
ms.assetid: 74fb36f4-54cd-4fda-bcc6-e965b5c7c37b
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# La propriet&#224; non pu&#242; essere dichiarata come &#39;&lt;modificatorepropriet&#224;&gt;&#39; perch&#233; contiene una funzione di accesso &#39;Private&#39;
Una proprietà con una routine della proprietà `Private` \(`Get` o `Set`\) è contrassegnata come [Overridable](/dotnet/visual-basic/language-reference/modifiers/overridable).  
  
 Se una proprietà o una routine di classe base viene dichiarata [Private](/dotnet/visual-basic/language-reference/modifiers/private), una classe derivata non può eseguire l'override di quella proprietà o di quella routine in quanto non può accedervi. Per questo motivo, non è possibile usare `Private` in combinazione con `Overridable`. Questo riguarda non soltanto la proprietà stessa, ma anche le singole routine della proprietà.  
  
 **ID errore:** BC31108  
  
### Per correggere l'errore  
  
-   Rimuovere la parola chiave `Overridable` dall'[Property Statement](/dotnet/visual-basic/language-reference/statements/property-statement) oppure rimuovere la parola chiave `Private` dall'[Get Statement](/dotnet/visual-basic/language-reference/statements/get-statement) o dall'[Set Statement](/dotnet/visual-basic/language-reference/statements/set-statement).  
  
## Vedere anche  
 [Routine Property](/dotnet/visual-basic/programming-guide/language-features/procedures/property-procedures)   
 [How to: Declare a Property with Mixed Access Levels](../Topic/How%20to:%20Declare%20a%20Property%20with%20Mixed%20Access%20Levels%20\(Visual%20Basic\).md)