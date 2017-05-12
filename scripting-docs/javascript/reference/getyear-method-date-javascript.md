---
title: "Metodo getYear (Date) (JavaScript) | Microsoft Docs"
ms.custom: ""
ms.date: "01/18/2017"
ms.prod: "windows-client-threshold"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-javascript"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "getYear"
dev_langs: 
  - "JavaScript"
  - "TypeScript"
  - "DHTML"
helpviewer_keywords: 
  - "date, restituzione anno"
  - "GetYear (metodo)"
ms.assetid: 0e23e832-acd4-49a9-a175-515d0094f172
caps.latest.revision: 19
author: "mikejo5000"
ms.author: "mikejo"
manager: "ghogen"
caps.handback.revision: 19
---
# Metodo getYear (Date) (JavaScript)
Ottiene l'anno di oggetto `Date`.  
  
## Sintassi  
  
```  
  
dateObj.getYear()   
```  
  
#### Parametri  
 Il riferimento richiesto `dateObj` è un oggetto `Date`.  
  
## Valore restituito  
 Restituisce l'anno.  
  
## Note  
  
> [!IMPORTANT]
>  Questo metodo è obsoleto e viene fornito per compatibilità con le versioni precedenti di.  In alternativa, utilizzare il metodo `getFullYear`.  
  
 In [!INCLUDE[jsv1textspecific](../../javascript/reference/includes/jsv1textspecific-md.md)]quindi nelle versioni di Internet Explorer che iniziano con [!INCLUDE[jsv9textspecific](../../javascript/reference/includes/jsv9textspecific-md.md)], il valore restituito è l'anno archiviato meno 1900.  L'anno 1899, ad esempio, viene restituito come \-1 e l'anno 2000 come 100.  
  
 In [!INCLUDE[jsv3textspecific](../../javascript/reference/includes/jsv3textspecific-md.md)] con [!INCLUDE[jsv58textspecific](../../javascript/reference/includes/jsv58textspecific-md.md)], la formula dipende dall'anno.  Per gli anni 1900 fino al 1999, il valore restituito è un valore a due cifre che rappresenta l'anno archiviato meno 1900.  Per l'esterno di date compreso, anno esteso viene restituito.  Ad esempio, 1996 viene restituito come 96, ma 1825 e 2025 sono restituiti come è.  
  
## Requisiti  
 [!INCLUDE[jsv1](../../javascript/misc/includes/jsv1-md.md)]  
  
 **Applies To**: [Oggetto Date](../../javascript/reference/date-object-javascript.md)  
  
## Vedere anche  
 [Metodo getFullYear \(Date\)](../../javascript/reference/getfullyear-method-date-javascript.md)   
 [Metodo getUTCFullYear \(Date\)](../../javascript/reference/getutcfullyear-method-date-javascript.md)   
 [Metodo setFullYear \(Date\)](../../javascript/reference/setfullyear-method-date-javascript.md)   
 [Metodo setUTCFullYear \(Date\)](../../javascript/reference/setutcfullyear-method-date-javascript.md)   
 [Metodo setYear \(Date\)](../../javascript/reference/setyear-method-date-javascript.md)