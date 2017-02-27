---
title: "CA5351: non usare algoritmi di crittografia interrotti | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 483f51b3-e186-4433-b48e-5ca24a9a9c94
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 12
---
# CA5351: non usare algoritmi di crittografia interrotti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DoNotUseBrokenCryptographicAlgorithms|  
|CheckId|CA5351|  
|Categoria|Microsoft.Cryptography|  
|Modifica importante|Non importante|  
  
> [!NOTE]
>  Ultimo aggiornamento di questo avviso: novembre 2015.  
  
## Causa  
 Le funzioni hash come <xref:System.Security.Cryptography.MD5> e gli algoritmi di crittografia come <xref:System.Security.Cryptography.DES> e <xref:System.Security.Cryptography.RC2> possono causare rischi significativi ed esporre le informazioni sensibili tramite semplici tecniche di attacco, come attacchi di forza bruta e collisioni hash.  
  
 Gli algoritmi di crittografia elencati di seguito sono soggetti ad attacchi crittografici noti. L'algoritmo hash di crittografia <xref:System.Security.Cryptography.MD5> è soggetto ad attacchi di collisione hash.  A seconda dell'utilizzo, la collisione hash può causare rappresentazione, manomissione o altri tipi di attacchi in sistemi che ricorrono all'output di crittografia univoco di una funzione hash. Gli algoritmi di crittografia <xref:System.Security.Cryptography.DES> e <xref:System.Security.Cryptography.RC2> sono soggetti ad attacchi crittografici che possono provocare la diffusione indesiderata dei dati crittografati.  
  
## Descrizione della regola  
 Gli algoritmi di crittografia interrotti non sono considerati sicuri e il loro uso non è consigliato. L'algoritmo hash MD5 è soggetto ad attacchi di collisione noti, anche se la vulnerabilità specifica varia a seconda del contesto d'uso.  Gli algoritmi hash usati per garantire l'integrità dei dati \(ad esempio una firma del file o un certificato digitale\) sono particolarmente vulnerabili.  In questo contesto gli autori di attacchi possono generare due serie di dati separati, in modo tale che i dati validi possano essere sostituiti da dati dannosi senza modificare il valore hash o invalidare una firma digitale associata.  
  
 Per gli algoritmi di crittografia:  
  
-   La crittografia <xref:System.Security.Cryptography.DES> contiene una chiave di piccole dimensioni, che può essere colpita da attacchi di forza bruta in meno di un giorno.  
  
-   La crittografia <xref:System.Security.Cryptography.RC2> è soggetta ad attacchi alle chiavi correlate, in cui l'autore dell'attacco trova le relazioni matematiche tra tutti i valori di chiave.  
  
 Questa regola viene attivata quando trova nel codice sorgente una delle funzioni di crittografia indicate sopra e genera un avviso all'utente.  
  
## Come correggere le violazioni  
 Usare opzioni di crittografia più avanzate:  
  
-   Per MD5, usare gli hash della famiglia [SHA\-2](https://msdn.microsoft.com/en-us/library/windows/desktop/aa382459.aspx), ad esempio <xref:System.Security.Cryptography.SHA512>, <xref:System.Security.Cryptography.SHA384> o <xref:System.Security.Cryptography.SHA256>.  
  
-   Per DES e RC2, usare la crittografia <xref:System.Security.Cryptography.Aes>.  
  
## Esclusione di avvisi  
 Non eliminare un avviso da questa regola, a meno che questa non venga esaminata da un esperto di crittografia.  
  
## Esempio di pseudocodice  
 L'esempio di pseudocodice seguente mostra il criterio rilevato da questa regola e le possibili alternative.  
  
### Violazione di hash MD5  
  
```  
using System.Security.Cryptography; ... var hashAlg = MD5.Create();  
  
```  
  
### Soluzione  
  
```  
using System.Security.Cryptography; ... var hashAlg = SHA256.Create();  
  
```  
  
### Violazione di crittografia RC2  
  
```  
using System.Security.Cryptography; ... RC2 encAlg = RC2.Create();  
  
```  
  
### Soluzione  
  
```  
using System.Security.Cryptography; ... using (AesManaged encAlg = new AesManaged()) { ... }  
```  
  
### Violazione di crittografia DES  
  
```  
using System.Security.Cryptography; ... DES encAlg = DES.Create();  
  
```  
  
### Soluzione  
  
```  
using System.Security.Cryptography; ... using (AesManaged encAlg = new AesManaged()) { ... }  
```