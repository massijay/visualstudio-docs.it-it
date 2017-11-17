---
title: 'CA1504: Controllare i nomi dei campi fuorvianti | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ReviewMisleadingFieldNames
- CA1504
helpviewer_keywords:
- CA1504
- ReviewMisleadingFieldNames
ms.assetid: 94136ff1-4aaf-4dc2-9170-48c171ab7499
caps.latest.revision: "15"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: d03c07b48b2cfbfc19fcb9aa2ac4353ddf87a8a6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca1504-review-misleading-field-names"></a>CA1504: Controllare i nomi dei campi fuorvianti
|||  
|-|-|  
|TypeName|ReviewMisleadingFieldNames|  
|CheckId|CA1504|  
|Categoria|Microsoft.Maintainability|  
|Breaking Change|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Il nome di un campo di istanza inizia con "s _" o il nome di un `static` (`Shared` in [!INCLUDE[vbprvb](../code-quality/includes/vbprvb_md.md)]) campo inizia con "m _".  
  
## <a name="rule-description"></a>Descrizione della regola  
 I nomi dei campi che iniziano con "s _" sono associati a dati statici da molti utenti. Analogamente, i nomi dei campi che iniziano con "m _" sono associati ai dati di istanza (membro). Per semplificare la gestione del codice, i nomi devono seguire le convenzioni utilizzate in genere.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, rinominare il campo utilizzando il prefisso appropriato. In alternativa, in modo che il campo conforme al suffisso corrente aggiungendo o rimuovendo il `static` modificatore.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.