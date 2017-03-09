---
title: "CA2108: Controllare la sicurezza dichiarativa sui tipi di valori | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ReviewDeclarativeSecurityOnValueTypes"
  - "CA2108"
helpviewer_keywords: 
  - "CA2108"
  - "ReviewDeclarativeSecurityOnValueTypes"
ms.assetid: d62bffdd-3826-4d52-a708-1c646c5d48c2
caps.latest.revision: 16
caps.handback.revision: 16
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2108: Controllare la sicurezza dichiarativa sui tipi di valori
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|ReviewDeclarativeSecurityOnValueTypes|  
|CheckId|CA2108|  
|Categoria|Microsoft.Security|  
|Breaking Change|Non sostanziale|  
  
## Causa  
 Un tipo di valore pubblico o protetto è protetto da [Dati e modellazione](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md) o [Link Demands](../Topic/Link%20Demands.md).  
  
## Descrizione della regola  
 I tipi di valore vengono allocati e inizializzati dai relativi costruttori predefiniti prima dell'esecuzione di altri costruttori.  Se un tipo di valore è protetto da Demand o LinkDemand e il chiamante non dispone di autorizzazioni sufficienti per il controllo di sicurezza, qualsiasi costruttore diverso da quello predefinito avrà esito negativo e verrà generata un'eccezione di sicurezza.  Il tipo di valore non viene deallocato, ma viene lasciato nello stato impostato dal relativo costruttore predefinito.  Non presupporre che un chiamante che passa un'istanza del tipo di valore disponga dell'autorizzazione a creare o ad accedere all'istanza.  
  
## Come correggere le violazioni  
 Non è possibile correggere una violazione di questa regola se non rimuovendo il controllo di sicurezza dal tipo e utilizzando in sostituzione controlli di sicurezza a livello di metodo.  Si noti che questa correzione della violazione non impedisce ai chiamanti con autorizzazioni non adeguate di ottenere istanze del tipo di valore.  È necessario assicurarsi che un'istanza del tipo di valore, nello stato predefinito, non esponga informazioni riservate e non possa essere utilizzata in modo dannoso.  
  
## Esclusione di avvisi  
 È possibile escludere un avviso da questa regola se qualsiasi chiamante può ottenere istanze del tipo di valore nello stato predefinito senza causare una minaccia alla sicurezza.  
  
## Esempio  
 Nell'esempio riportato di seguito viene illustrata una libreria contenente un tipo di valore che viola questa regola.  Si noti che il tipo `StructureManager` presuppone che un chiamante che passa un'istanza del tipo di valore disponga dell'autorizzazione a creare o ad accedere all'istanza.  
  
 [!code-cs[FxCop.Security.DemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_1.cs)]  
  
## Esempio  
 Nella seguente applicazione vengono illustrati i punti deboli della libreria.  
  
 [!code-cs[FxCop.Security.TestDemandOnValueType#1](../code-quality/codesnippet/CSharp/ca2108-review-declarative-security-on-value-types_2.cs)]  
  
 Questo esempio produce l'output che segue.  
  
  **Structure custom constructor: Request failed.**  
**New values SecuredTypeStructure 100 100**  
**New values SecuredTypeStructure 200 200**   
## Vedere anche  
 [Link Demands](../Topic/Link%20Demands.md)   
 [Dati e modellazione](../Topic/Data%20and%20Modeling%20in%20the%20.NET%20Framework.md)