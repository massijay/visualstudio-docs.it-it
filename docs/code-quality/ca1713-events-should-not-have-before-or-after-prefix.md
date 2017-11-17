---
title: ': Non CA1713 eventi prefisso before o after | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- EventsShouldNotHaveBeforeOrAfterPrefix
- CA1713
helpviewer_keywords:
- CA1713
- EventsShouldNotHaveBeforeOrAfterPrefix
ms.assetid: 855772a4-aa9e-410b-88c1-c5fba1ca63da
caps.latest.revision: "14"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: c211d2f2cc65c12fd11782058c5e8b8a3aaf47b6
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca1713-events-should-not-have-before-or-after-prefix"></a>CA1713: Non utilizzare il prefisso Before o After negli eventi
|||  
|-|-|  
|TypeName|EventsShouldNotHaveBeforeOrAfterPrefix|  
|CheckId|CA1713|  
|Categoria|Microsoft. naming|  
|Breaking Change|Interruzione|  
  
## <a name="cause"></a>Causa  
 Il nome di un evento inizia con "Before" o "After".  
  
## <a name="rule-description"></a>Descrizione della regola  
 I nomi degli eventi deve descrivere l'azione che genera l'evento. Per denominare eventi correlati generati in una sequenza specifica, utilizzare i tempi verbali presente o passato per indicare la posizione relativa nella sequenza di azioni. Ad esempio, quando una coppia di eventi di denominazione che viene generato alla chiusura di una risorsa, si potrebbe denominarla "Closing" e "Closed" anziché "BeforeClose" e "AfterClose".  
  
 Convenzioni di denominazione forniscono un aspetto comune per librerie destinate a common language runtime. In questo modo si riduce la curva di apprendimento che è necessario per le nuove librerie software e aumenta la confidenza di clienti che la libreria è stata sviluppata da un utente che ha esperienza nello sviluppo di codice gestito.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Rimuovere il prefisso dal nome dell'evento, quindi provare a modificare il nome da utilizzare il presente o passato di un verbo.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola.