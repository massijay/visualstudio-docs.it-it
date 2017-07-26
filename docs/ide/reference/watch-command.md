---
title: Comando Espressioni di controllo | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- debug.watch
helpviewer_keywords:
- Watch command
- Debug.Watch command
ms.assetid: aa02e647-d9f5-4905-a651-52a8df595795
caps.latest.revision: 11
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
ms.sourcegitcommit: 5ea9179ad37514ffad4876177b05150eecc22def
ms.openlocfilehash: bf91686a212551ef4b760d5bb2740a14f8495a1b
ms.contentlocale: it-it
ms.lasthandoff: 05/24/2017

---
# <a name="watch-command"></a>Comando Watch
Crea e apre un'istanza specificata di una finestra **Espressione di controllo** . È possibile usare una finestra **Espressioni di controllo** per calcolare i valori di variabili, espressioni e registri, modificare i valori e salvare i risultati.  
  
## <a name="syntax"></a>Sintassi  
  
```  
Debug.Watch[index]  
```  
  
## <a name="arguments"></a>Argomenti  
 `index`  
 Obbligatorio. Il numero di istanza della finestra Espressioni di controllo.  
  
## <a name="remarks"></a>Note  
 `index` deve essere di tipo Integer. I valori validi sono 1, 2, 3 e 4.  
  
## <a name="example"></a>Esempio  
  
```  
>Debug.Watch1  
```  
  
## <a name="see-also"></a>Vedere anche  
 [Finestre Auto e Variabili locali](../../debugger/autos-and-locals-windows.md)   
 [Set a Watch on Variables using the Watch and QuickWatch Windows in Visual Studio](../../debugger/watch-and-quickwatch-windows.md)  (Impostare un'espressione di controllo per le variabili con le finestre Espressione di controllo e Controllo immediato in Visual Studio)  
 [Visual Studio Commands](../../ide/reference/visual-studio-commands.md)  (Comandi di Visual Studio)  
 [Command Window](../../ide/reference/command-window.md)  (Finestra di comando)  
 [Find/Command Box](../../ide/find-command-box.md)  (Casella Trova/Comando)  
 [Visual Studio Command Aliases](../../ide/reference/visual-studio-command-aliases.md) (Alias di comandi di Visual Studio)
