---
title: Operatori di ricerca avanzati nelle espressioni di ricerca | Microsoft Docs
ms.custom: 
ms.date: 06/02/2017
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Help Viewer 2.0, searching for keywords
- Help Viewer 2.0, searching code
- Help Viewer 2.0, searching code by programming language
- Help Viewer 2.0, searching titles
- searching code [Help Viewer 2.0]
- searching titles [Help Viewer 2.0]
ms.assetid: 0cdc1746-8481-45ec-9c53-d0d89cdcbd5e
caps.latest.revision: 9
author: kempb
ms.author: kempb
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: 07ff2413503209d6ade252ac89dbfbe2589e7e85
ms.openlocfilehash: 7ad9c78134c337445a3e9180ad27234b7bcb07cc
ms.contentlocale: it-it
ms.lasthandoff: 06/02/2017

---
# <a name="advanced-search-operators-in-search-expressions"></a>Operatori di ricerca avanzati nelle espressioni di ricerca
Usando gli operatori di ricerca avanzati in Help Viewer, è possibile affinare la ricerca di contenuto creando espressioni di ricerca più complesse partendo da quelle più semplici. Come illustrato nella tabella seguente, questi operatori limitano il contesto in cui viene eseguita una query.  

> [!WARNING]
>  È necessario immettere gli operatori di ricerca avanzati seguiti da due punti senza spazio affinché il motore di ricerca li possa riconoscere.  

|Per cercare|Usare|Esempio|Risultato|  
|-------------------|---------|-------------|------------|  
|Un termine nel titolo dell'argomento|title:|title:binaryreader|Argomenti che contengono "binaryreader" nei titoli.|  
|Un termine in un esempio di codice|code:|code:readdouble|Argomenti che contengono "readdouble" in un esempio di codice.|  
|Un termine in un 'esempio di un linguaggio di programmazione specifico|code:vb:|code:vb:string|Argomenti che contengono "string" in un esempio di Visual Basic.|  
|Un argomento associato a una parola chiave di indice specifica|keyword:|keyword:readbyte|Argomenti associati alla parola chiave di indice "readbyte".|  

 È possibile usare l'operatore code: per trovare contenuti relativi a diversi linguaggi di programmazione. Restituisce tuttavia solo i risultati relativi al contenuto contrassegnato con un linguaggio di programmazione specifico. La tabella seguente elenca i linguaggi di programmazione supportati da questo operatore:  

|Linguaggio di programmazione|Usare|  
|--------------------------|---------|  
|Visual Basic|code:vb<br /><br /> o<br /><br /> code:visualbasic|  
|C#|code:c#<br /><br /> o<br /><br /> code:csharp|  
|C++|code:cpp<br /><br /> o<br /><br /> code:c++<br /><br /> o<br /><br /> code:cplusplus|  
|F#|code:f#<br /><br /> o<br /><br /> code:fsharp|  
|JavaScript|code:javascript<br /><br /> o<br /><br /> code:js|  
|XAML|: xaml|  

## <a name="see-also"></a>Vedere anche  
 [Operatori logici nelle espressioni di ricerca](../ide/logical-operators-in-search-expressions.md)   
 [Suggerimenti per la ricerca full-text](../ide/full-text-search-tips.md)

