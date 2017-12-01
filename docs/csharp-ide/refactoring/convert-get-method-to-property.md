---
title: "Convertire il metodo Get in proprietà - Refactoring (c#) | Documenti Microsoft"
ms.custom: 
ms.date: 11/27/2017
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
ms.devlang: csharp
author: kuhlenh
ms.author: kaseyu
manager: ghogen
f1_keywords: vs.csharp.refactoring.convertmethodtoproperty
dev_langs: csharp
ms.openlocfilehash: d034b8835caf0a5e56a9ef32599cf9197f1e3e16
ms.sourcegitcommit: 5f5587a1bcf4aae995c80d54a67b4b461f8695f3
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/29/2017
---
# <a name="convert-get-method-to-property--convert-property-to-get-method"></a>Convertire il metodo Get di proprietà / convertire il metodo Get di proprietà
## <a name="convert-get-method-to-property"></a>Convertire il metodo Get di proprietà
**Novità:** consente di convertire un metodo Get in una proprietà (e facoltativamente il metodo Set) e viceversa.

**Quando:** si ha un metodo Get che non contiene alcuna logica.

**Procedura:**

1. Posizionare il cursore nel nome del metodo Get.

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu **Replace (metodo) con la proprietà** nel popup di finestra di anteprima. Se si dispone di un metodo Set, è anche possibile convertire il metodo Set in questo momento selezionando **metodo sostituire Get e Set (metodo) con la proprietà**.
   * **Mouse**
     * Pulsante destro del mouse nel codice, selezionare il **azioni rapide e refactoring** dal menu **Replace (metodo) con la proprietà** nel popup di finestra di anteprima. Se si dispone di un metodo Set, è anche possibile convertire il metodo Set in questo momento selezionando **metodo sostituire Get e Set (metodo) con la proprietà**.

1. Se si è soddisfatti delle modifiche nell'anteprima del codice, premere **invio** o Correggi dal menu e le modifiche verranno salvate.

Esempio:

```csharp
private int MyValue;

// Before
public int GetMyValue()
{
    return MyValue;
}

// Replace 'GetMyValue' with property

// After
public int MyValue
{
    get { return MyValue; }
}
```

## <a name="convert-property-to-get-method"></a>Convertire il metodo Get di proprietà
**Novità:** consente di convertire una proprietà a un metodo Get

**Quando:** è presente una proprietà che prevede più di immediatamente impostazione e recupero di un valore 

**Procedura:**

1. Posizionare il cursore nel nome del metodo Get.

1. Successivamente, eseguire una delle operazioni seguenti:
   * **Tastiera**
     * Premere **Ctrl +.** Per attivare il **azioni rapide e refactoring** dal menu **sostituire proprietà con metodi** nel popup di finestra di anteprima.
   * **Mouse**
     * Pulsante destro del mouse nel codice, selezionare il **azioni rapide e refactoring** dal menu **sostituire proprietà con metodi** nel popup di finestra di anteprima.

1. Se si è soddisfatti delle modifiche nell'anteprima del codice, premere **invio** o Correggi dal menu e le modifiche verranno salvate.

## <a name="see-also"></a>Vedere anche  
[Refactoring (C#)](../refactoring-csharp.md)  
[Preview Changes](../../ide/preview-changes.md) (Visualizzare l'anteprima delle modifiche)