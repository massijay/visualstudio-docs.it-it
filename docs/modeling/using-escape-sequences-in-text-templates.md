---
title: Utilizzo di sequenze di Escape in modelli di testo | Documenti Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: text templates, escape sequences
ms.assetid: 36fff542-2f42-460f-a2d5-03fc76817f3b
caps.latest.revision: "29"
author: alancameronwills
ms.author: awills
manager: douge
ms.openlocfilehash: fdf062c9b33dd4a160f54bba83991a3cdda7f0d1
ms.sourcegitcommit: aadb9588877418b8b55a5612c1d3842d4520ca4c
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/27/2017
---
# <a name="using-escape-sequences-in-text-templates"></a>Utilizzo di sequenze di escape in modelli di testo
Nei modelli di testo per generare il tag di modello di testo e (nel codice c# solo), è possibile utilizzare le sequenze di escape di caratteri di escape di controllo e tra virgolette.  
  
 Per stampare i tag di apertura e chiusura di un blocco di codice standard per il file di output, escape i tag come indicato di seguito:  
  
```  
\<# ... \#>  
```  
  
 È possibile eseguire la stessa con gli altri tag blocco direttiva e il codice del modello di testo.  
  
 Se un blocco di testo include stringhe utilizzate per eseguire l'escape di tag di modello di testo, è possibile utilizzare le sequenze di escape seguenti:  
  
-   Se un tag di modello di testo è preceduto da un numero pari di escape (\\) il modello di caratteri parser verrà metà dei caratteri di escape e includere la sequenza come un tag di modello di testo. Ad esempio, se sono presenti quattro caratteri di escape nel modello di testo, verrà due "\\" caratteri nel file generato.  
  
-   Se il tag di modello di testo è preceduto da un numero dispari di escape (\\) caratteri, il parser del modello includerà metà del "\\" caratteri più il tag stesso (\<# o #>). Il tag non viene considerato come un tag di modello di testo.  
  
-   Se un carattere di escape (\\) carattere viene visualizzato altrove in qualsiasi sequenza diverso da in cui viene eseguito l'escape un carattere di controllo o una virgoletta (solo in c#), verrà restituito il carattere direttamente.  
  
## <a name="see-also"></a>Vedere anche  
 [Procedura: Generare modelli da modelli usando sequenze di escape](../modeling/how-to-generate-templates-from-templates-by-using-escape-sequences.md)