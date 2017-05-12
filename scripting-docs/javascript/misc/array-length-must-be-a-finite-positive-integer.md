---
title: "La lunghezza della matrice deve essere pari a un numero intero positivo finito | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT5029"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 1a467040-4702-4178-848f-418a5974e907
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# La lunghezza della matrice deve essere pari a un numero intero positivo finito
Il costruttore **Array** viene chiamato con un argomento che non corrisponde a un numero intero. I numeri interi sono costituiti da zero più il set di numeri interi positivi.  
  
### Per correggere l'errore  
  
-   Utilizzare i numeri interi positivi solo durante la creazione di un nuovo oggetto `Array`.  La creazione di una matrice con un singolo elemento che non rappresenta un numero intero costituisce una procedura in due fasi.  Creare innanzitutto una matrice con un elemento, quindi inserire il valore nel primo elemento \(array\[0\]\).  Di seguito viene illustrato un esempio che genera l'errore.  
  
    ```javascript  
    var piArray = new Array(3.14159);  
    ```  
  
     Nel seguente esempio viene illustrata la modalità corretta per specificare una matrice con un singolo elemento numerico.  
  
    ```javascript  
    var piArray = new Array(1);  
    piArray [0] = 3.14159;  
    ```  
  
     Non esiste un limite superiore per la dimensione di una matrice, eccetto il valore intero massimo \(circa 4 miliardi\).  
  
## Vedere anche  
 [Utilizzo di matrici](../../javascript/advanced/using-arrays-javascript.md)