---
title: "CA5350: non usare algoritmi di crittografia vulnerabili | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c51bb8a-fcfa-46aa-ab61-634be84c4a7a
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 11
---
# CA5350: non usare algoritmi di crittografia vulnerabili
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseWeakCryptographicAlgorithms|  
|CheckId|CA5350|  
|Categoria|Microsoft.Cryptography|  
|Modifica importante|Non importante|  
  
> [!NOTE]
>  Ultimo aggiornamento di questo avviso: novembre 2015.  
  
## Causa  
 Gli algoritmi di crittografia, ad esempio <xref:System.Security.Cryptography.TripleDES> e gli algoritmi di hash, ad esempio <xref:System.Security.Cryptography.SHA1> e <xref:System.Security.Cryptography.RIPEMD160> sono considerati vulnerabili.  
  
 Questi algoritmi di crittografia non assicurano la sicurezza tanto quanto le controparti più moderne. Gli algoritmi di hash crittografici <xref:System.Security.Cryptography.SHA1> e <xref:System.Security.Cryptography.RIPEMD160> forniscono meno resistenza ai conflitti rispetto agli algoritmi di hash più moderni. L'algoritmo di crittografia <xref:System.Security.Cryptography.TripleDES> fornisce un minor numero di bit di sicurezza rispetto ad algoritmi di crittografia più moderni.  
  
## Descrizione della regola  
 Oggi si usano algoritmi di crittografia e funzioni hash deboli per diversi motivi, ma non dovrebbero essere usati per garantire la riservatezza dei dati che proteggono.  
  
 La regola viene attivata quando trova algoritmi 3DES, SHA1 o RIPEMD160 nel codice e genera un avviso all'utente.  
  
## Come correggere le violazioni  
 Usare opzioni di crittografia più avanzate:  
  
-   Per la crittografia TripleDES, usare la crittografia <xref:System.Security.Cryptography.Aes>.  
  
-   Per le funzioni hash SHA1 o RIPEMD160, usare quelle nella famiglia [SHA\-2](https://msdn.microsoft.com/en-us/library/windows/desktop/aa382459.aspx) \(ad esempio <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384>, <xref:System.Security.Cryptography.SHA256>\).  
  
## Esclusione di avvisi  
 Escludere un avviso da questa regola quando il livello di protezione necessario per i dati non richiede una garanzia di sicurezza.  
  
## Esempio di pseudocodice  
 Al momento della stesura di questo articolo, l'esempio di pseudocodice seguente illustra il modello rilevato da questa regola.  
  
### Violazione di hash SHA\-1  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA1.Create();  
  
```  
  
### Soluzione  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA256.Create();  
  
```  
  
### Violazione di hash RIPEMD160  
  
```  
using System.Security.Cryptography; ... var hashAlg = RIPEMD160Managed.Create();  
  
```  
  
### Soluzione  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA256.Create();  
  
```  
  
### Violazione di crittografia TripleDES  
  
```  
using System.Security.Cryptography; ... using (TripleDES encAlg = TripleDES.Create()) { ... }  
```  
  
### Soluzione  
  
```  
using System.Security.Cryptography; ... using (AesManaged encAlg = new AesManaged()) { ... }  
```