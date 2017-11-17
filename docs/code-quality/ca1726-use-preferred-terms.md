---
title: 'CA1726: Utilizzare termini preferiti | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- UsePreferredTerms
- CA1726
helpviewer_keywords: UsePreferredTerms
ms.assetid: 642b2acd-3a33-4d1f-b0a7-67073ae73be2
caps.latest.revision: "23"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 2ae02d0eb136d45bc2b8af7dde5f897765493050
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca1726-use-preferred-terms"></a>CA1726: Utilizzare termini preferiti
|||  
|-|-|  
|TypeName|UsePreferredTerms|  
|CheckId|CA1726|  
|Categoria|Microsoft. naming|  
|Breaking Change|Sostanziale - Quando generato su assembly<br /><br /> Non sostanziale - Quando generato su parametri di tipo|  
  
## <a name="cause"></a>Causa  
 Il nome di un identificatore visibile esternamente include un termine per il quale esiste un termine alternativo preferito. In alternativa, il nome include il termine Flag o flag.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Questa regola analizza un identificatore in token. Ogni singolo token e ogni combinazione di due token contigui viene confrontato con i termini che vengono compilati nella regola e nella sezione obsoleto dei dizionari personalizzati. La tabella seguente illustra i termini che vengono compilati nella regola e le alternative preferite.  
  
|Termine obsoleto|Termine preferito|  
|-------------------|--------------------|  
|non sono|Non|  
|Annullato|Annullato|  
|Impossibile|Non è possibile|  
|ComPlus|EnterpriseServices|  
|Couldnt|CouldNot|  
|Didnt|DidNot|  
|Doesnt|Non|  
|Non|Si|  
|Flag o Flags|Non vi è alcun termine di sostituzione. Non usare.|  
|non veniva|HadNot|  
|Non è ancora|HasNot|  
|non sono stati|HaveNot|  
|Indici|Indexes|  
|non è|IsNot|  
|Account di accesso|Accesso|  
|Disconnessione|Disconnessione|  
|Shouldnt|ShouldNot|  
|Sign-on|Accedi|  
|Conclusione|Disconnessione|  
|Wasnt|WasNot|  
|non sono stati|WereNot|  
|Non riuscita|Non|  
|Wouldnt|WouldNot|  
|Scrivibile|Scrivibile|  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, sostituire il termine con il termine alternativo preferito.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Escludere un avviso da questa regola solo se il nome dell'identificatore è intenzionale e riguarda in particolare il termine originale anziché il termine preferito.  
  
## <a name="related-rules"></a>Regole correlate  
 [Avvisi di denominazione](../code-quality/naming-warnings.md)