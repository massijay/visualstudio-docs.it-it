---
title: Condizioni di MSBuild | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-sdk
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- MSBuild, conditions
- conditions [MSBuild]
ms.assetid: 9d7aa308-b667-48ed-b4c9-a61e49eb0a85
caps.latest.revision: "14"
author: kempb
ms.author: kempb
manager: ghogen
ms.openlocfilehash: f3e4590a2623d05b78f4c62e877b0ff3783ceec9
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="msbuild-conditions"></a>Condizioni di MSBuild
[!INCLUDE[vstecmsbuild](../extensibility/internals/includes/vstecmsbuild_md.md)] supporta un set specifico di condizioni che possono essere applicate dove è consentito un attributo `Condition`. La tabella seguente illustra tali condizioni.  
  
|Condizione|Descrizione|  
|---------------|-----------------|  
|'`stringA`' == '`stringB`'|Restituisce `true` se `stringA` è uguale a `stringB`.<br /><br /> Ad esempio:<br /><br /> `Condition="'$(CONFIG)'=='DEBUG'"`<br /><br /> Le virgolette non sono necessarie per stringhe alfanumeriche semplici o valori booleani. Sono tuttavia obbligatorie per i valori vuoti.|  
|'`stringA`' != '`stringB`'|Restituisce `true` se `stringA` non è uguale a `stringB`.<br /><br /> Ad esempio:<br /><br /> `Condition="'$(CONFIG)'!='DEBUG'"`<br /><br /> Le virgolette non sono necessarie per stringhe alfanumeriche semplici o valori booleani. Sono tuttavia obbligatorie per i valori vuoti.|  
|\<, >, \<=, >=|Restituisce i valori numerici degli operandi. Restituisce `true` se la valutazione relazionale è true. Gli operandi devono restituire un numero decimale o esadecimale. I numeri esadecimali devono iniziare con "0x". **Nota:** in XML i caratteri `<` e `>` devono essere preceduti da un carattere di escape. Il simbolo `<` viene rappresentato come `<`. Il simbolo `>` viene rappresentato come `>`.|  
|Exists('`stringA`')|Restituisce `true` se esiste un file o una cartella con il nome `stringA`.<br /><br /> Ad esempio:<br /><br /> `Condition="!Exists('$(builtdir)')"`<br /><br /> Le virgolette non sono necessarie per stringhe alfanumeriche semplici o valori booleani. Sono tuttavia obbligatorie per i valori vuoti.|  
|HasTrailingSlash('`stringA`')|Restituisce `true` se la stringa specificata contiene un carattere di barra (/) o di barra rovesciata (\\) finale.<br /><br /> Ad esempio:<br /><br /> `Condition="!HasTrailingSlash('$(OutputPath)')"`<br /><br /> Le virgolette non sono necessarie per stringhe alfanumeriche semplici o valori booleani. Sono tuttavia obbligatorie per i valori vuoti.|  
|!|Restituisce `true` se l'operando restituisce `false`.|  
|E|Restituisce `true` se entrambi gli operandi restituiscono `true`.|  
|Or|Restituisce `true` se almeno uno degli operandi restituisce `true`.|  
|()|Meccanismo di raggruppamento che restituisce `true` se le espressioni contenute all'interno restituiscono `true`.|  
|$if$ ( %expression% ), $else$, $endif$|Controlla se l'oggetto `%expression%` specificato corrisponde al valore stringa del parametro di modello personalizzato passato. Se la condizione `$if$` restituisce `true`, le istruzioni vengono eseguite. In caso contrario, viene controllata la condizione `$else$`. Se la condizione `$else$` è `true`, le istruzioni vengono eseguite. In caso contrario, la condizione `$endif$` termina la valutazione dell'espressione.<br /><br /> Per esempi di utilizzo, vedere [Visual Studio Project/Item Template Parameter Logic](http://stackoverflow.com/questions/6709057/visual-studio-project-item-template-parameter-logic) (Logica dei parametri dei modelli di elemento/progetto di Visual Studio).|  
  
## <a name="see-also"></a>Vedere anche  
 [Informazioni di riferimento su MSBuild](../msbuild/msbuild-reference.md)   
 [Costrutti condizionali](../msbuild/msbuild-conditional-constructs.md)   
 [Procedura dettagliata: creazione di un nuovo file di progetto MSBuild](../msbuild/walkthrough-creating-an-msbuild-project-file-from-scratch.md)