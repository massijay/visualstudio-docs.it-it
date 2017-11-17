---
title: 'CA1308: Normalizzare le stringhe in lettere maiuscole | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- CA1308
- NormalizeStringsToUppercase
helpviewer_keywords:
- NormalizeStringsToUppercase
- CA1308
ms.assetid: 7e9a7457-3f93-4938-ac6f-1389fba8d9cc
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 8c9746d150fb2a47b1ce874ad003afd86d178e9a
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca1308-normalize-strings-to-uppercase"></a>CA1308: Normalizzare le stringhe in lettere maiuscole
|||  
|-|-|  
|TypeName|NormalizeStringsToUppercase|  
|CheckId|CA1308|  
|Categoria|Microsoft.Globalization|  
|Breaking Change|Non sostanziale|  
  
## <a name="cause"></a>Causa  
 Un'operazione normalizza stringa in caratteri minuscoli.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Le stringhe devono essere normalizzate in maiuscolo. Un piccolo gruppo di caratteri, quando vengono convertiti in caratteri minuscoli, non è possibile completare un round trip. Per completare un round trip mezzi per convertire i caratteri da una delle impostazioni locali a un altro che rappresenta i dati di tipo carattere in modo diverso, quindi in modo accurato recuperano i caratteri originali dai caratteri convertiti.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Modificare le operazioni che convertono le stringhe in caratteri minuscoli in modo che le stringhe vengono convertite in caratteri maiuscoli invece. Ad esempio, modificare `String.ToLower(CultureInfo.InvariantCulture)` a `String.ToUpper(CultureInfo.InvariantCulture)`.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 È possibile eliminare un messaggio di avviso quando si fanno decisione relativa alla sicurezza in base al risultato (ad esempio, quando si visualizza nell'interfaccia utente).  
  
## <a name="see-also"></a>Vedere anche  
 [Avvisi di globalizzazione](../code-quality/globalization-warnings.md)