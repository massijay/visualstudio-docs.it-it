---
title: "CA1308: Normalizzare le stringhe in lettere maiuscole | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA1308"
  - "NormalizeStringsToUppercase"
helpviewer_keywords: 
  - "NormalizeStringsToUppercase"
  - "CA1308"
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA1308: Normalizzare le stringhe in lettere maiuscole
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|NormalizeStringsToUppercase|  
|CheckId|CA1308|  
|Category|Microsoft.Globalization|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un'operazione normalizza una stringa in minuscolo.  
  
## Descrizione della regola  
 Le stringhe devono essere normalizzate in maiuscolo.  Esiste un piccolo gruppo di caratteri che in caso di conversione in lettere minuscole non è in grado di completare un round trip.  Per completamento di un round trip si intende la conversione dei caratteri da un set di impostazioni locali a un altro che rappresenta i dati di tipo carattere in modo diverso, quindi recuperare accuratamente i caratteri originali dai caratteri convertiti.  
  
## Come correggere le violazioni  
 Modificare le operazioni che convertono le stringhe a minuscole in modo tale da convertirle a maiuscole.  Cambiare ad esempio `String.ToLower(CultureInfo.InvariantCulture)` in `String.ToUpper(CultureInfo.InvariantCulture)`  
  
## Esclusione di avvisi  
 L'eliminazione di un messaggio di avviso è sicura quando non si prendono decisioni di sicurezza in base al risultato, ad esempio nei casi in cui l'avviso venga visualizzato nell'interfaccia utente.  
  
## Vedere anche  
 [Avvisi di globalizzazione](../code-quality/globalization-warnings.md)