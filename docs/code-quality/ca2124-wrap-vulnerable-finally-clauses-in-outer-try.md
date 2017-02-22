---
title: "CA2124: Eseguire il wrapping delle clausole finally vulnerabili in un try esterno | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2124"
  - "WrapVulnerableFinallyClausesInOuterTry"
helpviewer_keywords: 
  - "CA2124"
  - "WrapVulnerableFinallyClausesInOuterTry"
ms.assetid: 82efd224-9e60-4b88-a0f5-dfabcc49a254
caps.latest.revision: 20
caps.handback.revision: 20
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2124: Eseguire il wrapping delle clausole finally vulnerabili in un try esterno
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|WrapVulnerableFinallyClausesInOuterTry|  
|CheckId|CA2124|  
|Category|Microsoft.Security|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Nelle versioni 1.0 e 1.1 di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], in un metodo pubblico o protetto è incluso un blocco `try`\/`catch`\/`finally`.  In apparenza il blocco `finally` reimposta lo stato di sicurezza e non è incluso in un blocco `finally`.  
  
## Descrizione della regola  
 La regola individua i blocchi `try`\/`finally` nel codice destinato alle versioni 1.0 e 1.1 di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)] che potrebbero essere vulnerabili a filtri di eccezione dannosi presenti nello stack di chiamate.  Se nel blocco try vengono eseguite operazioni quali la rappresentazione e viene generata un'eccezione, il filtro può essere eseguito prima del blocco `finally`.  Nell'esempio della rappresentazione, il filtro verrebbe eseguito come l'utente rappresentato.  I filtri sono attualmente implementabili solo in Visual Basic.  
  
> [!WARNING]
>  **Nota** Nelle versioni 2.0 e successive di [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)], il runtime consente di proteggere automaticamente un blocco `try`\/`catch`\/ `finally` da filtri di eccezioni dannose, se si verifica la reimpostazione direttamente all'interno del metodo che contiene il blocco di eccezioni.  
  
## Come correggere le violazioni  
 Inserire il blocco `try`\/`finally` privo di wrapper in un blocco try esterno.  Vedere il secondo esempio riportato di seguito  in cui viene forzata l'esecuzione del blocco `finally` prima del codice di filtro.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio di pseudo\-codice  
  
### Descrizione  
 Nello pseudo\-codice riportato di seguito viene illustrato il modello rilevato da questa regola.  
  
### Codice  
  
```  
try {  
   // Do some work.  
   Impersonator imp = new Impersonator("John Doe");  
   imp.AddToCreditCardBalance(100);  
}  
finally {  
   // Reset security state.  
   imp.Revert();  
}  
```  
  
## Esempio  
 Nello pseudo\-codice riportato di seguito viene illustrato il modello che è possibile utilizzare per proteggere il codice e soddisfare questa regola.  
  
```  
try {  
     try {  
        // Do some work.  
     }  
     finally {  
        // Reset security state.  
     }  
}  
catch()  
{  
    throw;  
}  
```