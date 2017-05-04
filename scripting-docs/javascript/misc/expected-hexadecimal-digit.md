---
title: "Prevista cifra esadecimale | Microsoft Docs"
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
  - "VS.WebClient.Help.SCRIPT1023"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
ms.assetid: 67a86df7-49f9-43cb-99c6-99b1a427827a
caps.latest.revision: 8
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 8
---
# Prevista cifra esadecimale
È stata creata una sequenza di escape Unicode errata.  Le sequenze di escape Unicode iniziano con \\u, seguito da esattamente quattro cifre esadecimali.  Le cifre esadecimali Unicode possono contenere solo i numeri da 0 a 9 e le lettere maiuscole e minuscole da A a F.  L'esempio seguente illustra una sequenza di escape Unicode in formato corretto.  
  
```javascript  
z = "\u1A5F";  
```  
  
### Per correggere l'errore  
  
-   Verificare che le cifre esadecimali Unicode inizino con \\u, contengano solo i numeri da 0 a 9 e le lettere maiuscole e minuscole da A a F e vengano raggruppate in quattro cifre.  
  
    > [!NOTE]
    >  Per utilizzare il testo letterale \\u in una stringa, inserire due barre rovesciate, \(\\\\u\), di cui una come carattere di escape per la prima.  
  
## Vedere anche  
 [Riepilogo dei tipi di dati](../../javascript/data-types-javascript.md)