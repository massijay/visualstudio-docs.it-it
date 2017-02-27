---
title: "CA1726: Utilizzare termini preferiti | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-devops-test"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "UsePreferredTerms"
  - "CA1726"
helpviewer_keywords: 
  - "UsePreferredTerms"
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
caps.handback.revision: 23
---
# CA1726: Utilizzare termini preferiti
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|Category|Microsoft.Naming|  
|Breaking Change|Sostanziale \- Quando generato su assembly<br /><br /> Non sostanziale \- Quando generato su parametri di tipo|  
  
## Causa  
 Il nome di un identificatore visibile esternamente include un termine per il quale esiste un termine alternativo preferito.  In alternativa, il nome include il termine Flag o Flags.  
  
## Descrizione della regola  
 La regola analizza un identificatore in token.  Ogni singolo token e ogni combinazione di token duali contigui viene confrontata ai termini compilati nella regola e nella sezione Deprecato dei dizionari personalizzati.  Nella tabella riportata di seguito sono visualizzati i termini compilati nella regola e le alternative preferite.  
  
|Termine obsoleto|Termine preferito|  
|----------------------|-----------------------|  
|Arent|AreNot|  
|Cancelled|Canceled|  
|Cant|Cannot|  
|ComPlus|EnterpriseServices|  
|Couldnt|CouldNot|  
|Didnt|DidNot|  
|Doesnt|DoesNot|  
|Dont|DoNot|  
|Flag o Flags|Non è presente alcun termine di sostituzione.  Non utilizzare.|  
|Hadnt|HadNot|  
|Hasn't|HasNot|  
|Havent|HaveNot|  
|Indices|Indici|  
|Isnt|IsNot|  
|LogIn|LogOn|  
|LogOut|LogOff|  
|Shouldnt|ShouldNot|  
|SignOn|SignIn|  
|SignOff|SignOut|  
|Wasnt|WasNot|  
|Werent|WereNot|  
|Wont|WillNot|  
|Wouldnt|WouldNot|  
|Writeable|Writable|  
  
## Come correggere le violazioni  
 Per correggere una violazione di questa regola, sostituire il termine con il termine alternativo preferito.  
  
## Esclusione di avvisi  
 Escludere un avviso dalla regola solo se il nome dell'identificatore è intenzionale e correlato in maniera specifica al termine originale, invece che al termine preferito.  
  
## Regole correlate  
 [Avvisi di denominazione](../code-quality/naming-warnings.md)