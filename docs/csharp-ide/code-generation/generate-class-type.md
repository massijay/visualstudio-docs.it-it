---
title: 'Generare una classe o un tipo di generazione del codice (c#): | Documenti Microsoft'
ms.custom: 
ms.date: 11/16/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
ms.assetid: ebc361fe-d9b1-4c7a-ae28-5e71b5775460
author: gewarren
ms.author: gewarren
manager: ghogen
f1_keywords: vsl.GenerateFromUsage
dev_langs: csharp
ms.openlocfilehash: b6825be5447718e47f7145b0b3b16ec6d0ee076c
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="generate-a-class-or-type-in-c"></a>Generare una classe o un tipo in c# #
**Novità:** consente di generare immediatamente il codice per una classe o tipo. 

**Quando:** si introduce una nuova classe o tipo e si desidera dichiarare in modo corretto, automaticamente.  

**Motivo:** prima di utilizzarlo, tuttavia questa funzionalità verrà generare la classe o tipo automaticamente, è possibile dichiarare la classe o tipo. 

**Procedura:**

1. Posizionare il cursore sulla riga in cui è presente una sottolineatura ondulata rossa che indica una classe che non esiste ancora utilizzati.

   ![Codice evidenziato](media/class_highlight.png)

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** menu e selezionare una delle opzioni nel popup di finestra di anteprima.
   * **Mouse**
     * Mouse e scegliere il **azioni rapide e refactoring** menu e selezionare una delle opzioni nel popup di finestra di anteprima.
     * Passare il mouse sulla sottolineatura rossa e scegliere il ![Lampadina](media/bulb.png) icona che verrà visualizzata.
     * Fare clic sul pulsante ![Lampadina](media/bulb.png) icona che verrà visualizzata nel margine sinistro se il cursore di testo si trova già nella riga con la sottolineatura ondulata rossa.

   ![Generare l'anteprima di classe](media/class_preview.png)

   Selection | Descrizione
   --- | ---
   Generare una classe*TypeName*' nel nuovo file | Crea una classe denominata *TypeName* in un file denominato *TypeName*. cs o vb
   Generare una classe*TypeName*' | Crea una classe denominata *TypeName* nel file corrente.
   Generare una classe annidata*TypeName*' | Crea una classe denominata *TypeName* annidata nella classe corrente.
   Genera nuovo tipo... | Crea una nuova classe o struct con tutte le proprietà specificate.

   >[!TIP]
   >Utilizzare il [ **Anteprima modifiche** ](../../ide/preview-changes.md) collegamento nella parte inferiore della finestra di anteprima per visualizzare tutte le modifiche apportate prima di effettuare la selezione.

1. Se si seleziona il **Genera nuovo tipo...**  elemento, una finestra di dialogo viene visualizzata che consente di eseguire alcune operazioni aggiuntive.

   ![Generare il tipo](media/class_newtype.png)

   Selection | Descrizione
   --- | ---
   Accedi a | Impostare il tipo di *predefinito*, *interno* o *pubblica* accesso.
   Kind | Può essere impostata come *classe* o *struct*.
   Nome | Questo non può essere modificato e sarà il nome che già digitato.
   Progetto | Se sono presenti più progetti nella soluzione, è possibile scegliere il percorso di classe/struttura TTL.
   Nome file | È possibile creare un nuovo file oppure è possibile aggiungere il tipo a un file esistente.

1. La classe/struttura verrà creata automaticamente con il costruttore dedotto dal relativo utilizzo.

   ![Generare il risultato di classe](media/class_result.png)

## <a name="see-also"></a>Vedere anche  
[Code Generation (C#)](../code-generation-csharp.md) (Generazione di codice (C#))  
[Preview Changes](../../ide/preview-changes.md) (Visualizzare l'anteprima delle modifiche)