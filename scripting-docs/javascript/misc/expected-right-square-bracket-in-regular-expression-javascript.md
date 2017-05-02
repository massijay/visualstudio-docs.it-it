---
title: "Prevista &#39;]&#39; nell&#39;espressione regolare (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "javascript"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS.WebClient.Help.SCRIPT5019"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1ca2079a-44dd-479f-a1e3-e04a14d0739e
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Prevista &#39;]&#39; nell&#39;espressione regolare (JavaScript)
Si è tentato di creare una classe di caratteri per la corrispondenza di un'espressione regolare senza includere la parentesi quadra di destra.  Le singole combinazioni di caratteri letterali possono essere assemblate in classi di caratteri posizionandole tra parentesi quadre.  Una classe di caratteri trova la corrispondenza con un carattere contenuto.  Ad esempio, \/\[abc\]\/ corrisponde a una delle lettere "a", "b" o "c".  
  
### Per correggere l'errore  
  
-   Aggiungere la parentesi quadra di destra all'espressione regolare.  
  
    > [!NOTE]
    >  Per creare la corrispondenza con una singola parentesi quadra, impostarla come carattere di escape utilizzando una barra rovesciata \- \\\[ \- in modo che non venga interpretata come carattere speciale da [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Vedere anche  
 [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/it-it/ab0766e1-7037-45ed-aa23-706f58358c0e)