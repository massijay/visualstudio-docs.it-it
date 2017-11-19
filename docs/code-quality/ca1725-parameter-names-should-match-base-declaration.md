---
title: 'CA1725: I nomi dei parametri devono corrispondere alla dichiarazione di base | Documenti Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-code-analysis
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ParameterNamesShouldMatchBaseDeclaration
- CA1725
helpviewer_keywords:
- CA1725
- ParameterNamesShouldMatchBaseDeclaration
ms.assetid: 9b657ab0-fe81-4f4c-9481-ba746988c922
caps.latest.revision: "11"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 3e8fc1a5f3623f989341f147ce8043449ee49165
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="ca1725-parameter-names-should-match-base-declaration"></a>CA1725: I nomi dei parametri devono corrispondere alla dichiarazione di base
|||  
|-|-|  
|TypeName|ParameterNamesShouldMatchBaseDeclaration|  
|CheckId|CA1725|  
|Categoria|Microsoft. naming|  
|Breaking Change|Interruzione|  
  
## <a name="cause"></a>Causa  
 Il nome di un parametro in un override del metodo visibile esternamente non corrispondere al nome del parametro nella dichiarazione di base del metodo o il nome del parametro nella dichiarazione del metodo di interfaccia.  
  
## <a name="rule-description"></a>Descrizione della regola  
 Una denominazione coerente dei parametri in una gerarchia di override aumenta la funzionalità degli override di metodo. Un nome di parametro in un metodo derivato diverso dal nome nella dichiarazione di base può provocare confusione sulla natura del metodo, ovvero se si tratta di un override del metodo di base o di un nuovo overload del metodo.  
  
## <a name="how-to-fix-violations"></a>Come correggere le violazioni  
 Per correggere una violazione di questa regola, rinominare il parametro in corrispondenza di dichiarazione di base. Per risolvere il problema è una modifica di rilievo per metodi visibili a COM.  
  
## <a name="when-to-suppress-warnings"></a>Esclusione di avvisi  
 Non escludere un avviso da questa regola, ad eccezione di metodi visibili a COM in librerie fornite in precedenza.