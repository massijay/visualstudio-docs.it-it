---
title: 'CA1809: Evitare un numero eccessivo di variabili locali | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1809
- AvoidExcessiveLocals
helpviewer_keywords:
- AvoidExcessiveLocals
- CA1809
ms.assetid: 5c81ea43-cb49-448f-980f-a1dd9764043c
caps.latest.revision: "19"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 0a96616d1ee0f7c63e8f36f56a18f234fa27a173
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca1809-avoid-excessive-locals"></a>CA1809: Evitare un numero eccessivo di variabili locali
|||  
|-|-|  
|TypeName|AvoidExcessiveLocals|  
|CheckId|CA1809|  
|Categoria|Microsoft. Performance|  
|Breaking Change|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un membro contiene più di 64 variabili locali, alcune delle quali potrebbe essere generato dal compilatore.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Un'ottimizzazione comune delle prestazioni consiste nell'archiviare un valore in un registro del processore anziché in memoria, è detto *registrazione* il valore. Common language runtime considera un massimo di 64 variabili locali per la registrazione. Le variabili non registrate vengono inserite nello stack e devono essere spostate in un registro prima della modifica. Per consentire la probabilità che tutte le variabili locali ottenere registrate, limitare il numero di variabili a 64.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, eseguire il refactoring dell'implementazione per utilizzare non più di 64 variabili locali.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È sicuro per escludere un avviso da questa regola o disabilitare la regola, se le prestazioni non è un problema.  
  
## <a name="related-rules"></a>Regole correlate  
 [CA1804: Rimuovere locali non usati](../code-quality/ca1804-remove-unused-locals.md)