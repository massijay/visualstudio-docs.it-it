---
title: "Impossibile assegnare a &#39;this&#39; | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5000"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: ba2b0a2b-f0f8-4698-b335-a4ab6c166671
caps.latest.revision: 7
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 7
---
# Impossibile assegnare a &#39;this&#39;
Si è tentato di assegnare un valore a **this**.  **this** è una parola chiave di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] che fa riferimento a uno dei seguenti elementi:  
  
-   l'oggetto che sta attualmente eseguendo un metodo;  
  
-   l'oggetto globale, se non vi è alcun metodo corrente o se il metodo non appartiene ad alcun altro oggetto.  
  
 Un metodo è una funzione [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] che viene richiamata tramite un oggetto.  All'interno di un metodo, la parola chiave **this** rappresenta un riferimento all'oggetto tramite il quale è stato richiamato il metodo, ovvero all'oggetto creato richiamando il costruttore della classe con l'operatore **new**.  
  
 All'interno di un metodo è possibile utilizzare **this** per fare riferimento all'oggetto corrente, ma non è possibile assegnare un nuovo valore a **this**.  
  
### Per correggere l'errore  
  
-   Non provare ad assegnare un valore a **this**.  Per accedere a una proprietà o a un metodo di un oggetto di cui è stata creata un'istanza, utilizzare l'operatore punto, ad esempio cerchio**.**raggio...  
  
    > [!NOTE]
    >  Non è possibile assegnare a una variabile creata dall'utente il nome **this**. Questa è infatti una parola riservata di [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)].  
  
## Vedere anche  
 [Istruzione this](../../javascript/reference/this-statement-javascript.md)   
 [Risoluzione dei problemi negli script](../../javascript/advanced/troubleshooting-your-scripts-javascript.md)