---
title: "Prevista &#39;)&#39; nell&#39;espressione regolare (JavaScript) | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5020"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 2087ba1d-9783-4d40-b609-e8542f579f7f
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Prevista &#39;)&#39; nell&#39;espressione regolare (JavaScript)
Si è tentato di creare un'acquisizione, un'asserzione o un gruppo di espressioni regolari senza includere la parentesi di chiusura.  Le parentesi hanno diversi scopi nelle espressioni regolari.  Principalmente, vengono utilizzate per acquisire sottoespressioni, specificare asserzioni o raggruppare modelli in modo da poter gestire gli elementi come una singola unità mediante \*, \+, ? e così via.  
  
### Per correggere l'errore  
  
-   Aggiungere le parentesi di chiusura più a destra.  
  
    > [!NOTE]
    >  Per creare la corrispondenza con una singola parentesi, impostarla come carattere di escape utilizzando una barra rovesciata \- \\\( \- in modo che non venga interpretata come carattere speciale da [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Vedere anche  
 [Oggetto Regular Expression](../../javascript/reference/regular-expression-object-javascript.md)   
 [Regular Expression Syntax \(JavaScript\)](http://msdn.microsoft.com/it-it/ab0766e1-7037-45ed-aa23-706f58358c0e)