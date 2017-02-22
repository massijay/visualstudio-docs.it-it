---
title: "CA2132: I costruttori predefiniti devono essere Critical almeno come i costruttori predefiniti del tipo base | Microsoft Docs"
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
  - "CA2132"
ms.assetid: e758afa1-8bde-442a-8a0a-bd1ea7b0ce4d
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2132: I costruttori predefiniti devono essere Critical almeno come i costruttori predefiniti del tipo base
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|DefaultConstructorsMustHaveConsistentTransparency|  
|CheckId|CA2132|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
> [!NOTE]
>  Questo avviso è applicato solo al codice che sta eseguendo CoreCLR \(la versione di CLR che è specifica delle applicazioni Web di Silverlight\).  
  
## Causa  
 L'attributo di trasparenza del costruttore predefinito di una classe derivata non è critico come la trasparenza della classe di base.  
  
## Descrizione della regola  
 I tipi e i membri con <xref:System.Security.SecurityCriticalAttribute> non possono essere utilizzati dal codice dell'applicazione Silverlight.  I tipi e i membri critici per la sicurezza possono essere utilizzati solo da codice attendibile nella libreria di classi .NET Framework per Silverlight.  Poiché una costruzione pubblica o protetta in una classe derivata deve disporre della trasparenza uguale o superiore alla classe di base, una classe in un'applicazione non può essere derivata da una classe contrassegnata come SecurityCritical.  
  
 Per il codice della piattaforma CoreCLR , se un tipo di base dispone di un costruttore predefinito non trasparente protetto o pubblico, il tipo derivato deve rispettare le regole di ereditarietà del costruttore predefinito.  Il tipo derivato deve disporre anche di un costruttore predefinito e quel costruttore deve essere almeno come costruttore predefinito critico del tipo di base.  
  
## Come correggere le violazioni  
 Per correggere la violazione, rimuovere il tipo o non derivare dal tipo non trasparente per la sicurezza.  
  
## Esclusione di avvisi  
 Non escludere gli avvisi da questa regola.  Violazioni di questa regola da parte di codice dell'applicazione comporteranno che CoreCLR rifiuti di caricare il tipo con un <xref:System.TypeLoadException>.  
  
### Codice  
 [!code-cs[FxCop.Security.CA2132.DefaultConstructorsMustHaveConsistentTransparency#1](../code-quality/codesnippet/CSharp/ca2132-default-constructors-must-be-at-least-as-critical-as-base-type-default-constructors_1.cs)]  
  
### Commenti