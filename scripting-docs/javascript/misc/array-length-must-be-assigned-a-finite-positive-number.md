---
title: "Alla lunghezza della matrice deve essere assegnato un numero positivo finito | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5030"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: c51c66a4-a543-4e95-b18d-2cfbcb3d1fdd
caps.latest.revision: 9
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 9
---
# Alla lunghezza della matrice deve essere assegnato un numero positivo finito
Nell'impostare la proprietà **length** di un oggetto **Array** esistente, è stata specificata una lunghezza della matrice che non era zero o un numero positivo.  Questo errore si verifica quando si assegna un valore alla proprietà **length** di un oggetto `Array` negativo o non numerico \(`NaN`\).  Si noti che [!INCLUDE[javascript](../../javascript/includes/javascript-md.md)] converte automaticamente i numeri frazionari in numeri interi.  
  
### Per correggere l'errore  
  
-   Assegnare un numero intero positivo alla proprietà length.  Non esiste un limite superiore per la dimensione di una matrice, eccetto il valore intero massimo \(circa 4 miliardi\).  Nell'esempio seguente viene illustrata la modalità corretta per impostare la proprietà **length** di un oggetto **Array**.  
  
    ```javascript  
    var my_array = new Array();  
    my_array.length = 99;  
    ```  
  
## Vedere anche  
 [Utilizzo di matrici](../../javascript/advanced/using-arrays-javascript.md)