---
title: "CA2137: I metodi Transparent devono contenere solo IL verificabile | Microsoft Docs"
ms.custom: ""
ms.date: "12/13/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CA2137"
ms.assetid: cbaeb0e1-56b6-43b4-812a-596b2859c329
caps.latest.revision: 13
caps.handback.revision: 13
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CA2137: I metodi Transparent devono contenere solo IL verificabile
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|TransparentMethodsMustBeVerifiable|  
|CheckId|CA2137|  
|Category|Microsoft.Security|  
|Breaking Change|Breaking|  
  
## Causa  
 Un metodo contiene codice non verificabile o restituisce un tipo tramite riferimento.  
  
## Descrizione della regola  
 Questa regola viene attivata sui tentativi tramite codice trasparente per la sicurezza per eseguire MSIL \(Microsoft Intermediate Language\) non verificabile.  Tuttavia, la regola non contiene un verificatore di IL completo, ma utilizza invece regole euristiche per intercettare la maggior parte delle violazioni di verifica MSIL.  
  
 Per essere sicuro che il codice contiene solo MSIL verificabile, eseguire [Peverify.exe \(PEVerify Tool\)](../Topic/Peverify.exe%20\(PEVerify%20Tool\).md) sull'assembly.  Eseguire PEVerify con l'opzione **\/transparent** che limita l'output solo ai metodi trasparenti non verificabile che provocherebbero un errore.  Se l'opzione \/trasparent non viene utilizzata, PEVerify verifica anche i metodi critici che possono contenere codice non verificabile.  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, contrassegnare il metodo con l'attributo <xref:System.Security.SecurityCriticalAttribute> o <xref:System.Security.SecuritySafeCriticalAttribute> o rimuovere il codice non verificabile.  
  
## Esclusione di avvisi  
 Non escludere un avviso da questa regola.  
  
## Esempio  
 Il metodo nell'esempio seguente utilizza codice non verificabile e deve essere contrassegnato con <xref:System.Security.SecurityCriticalAttribute> o con l'attributo <xref:System.Security.SecuritySafeCriticalAttribute>.  
  
 [!code-cs[FxCop.Security.CA2137.TransparentMethodsMustBeVerifiable#1](../code-quality/codesnippet/CSharp/ca2137-transparent-methods-must-contain-only-verifiable-il_1.cs)]