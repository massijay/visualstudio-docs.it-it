---
title: "La proprietà &lt;nome della proprietà&gt; non può essere eliminato | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 55873f74-7834-4ec1-8815-eeeb65618d87
caps.latest.revision: "2"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: b3a896e64e048a5104bca84b726c730d4d9d524a
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="the-property-ltproperty-namegt-cannot-be-deleted"></a>La proprietà &lt;nome della proprietà&gt; non può essere eliminato
La proprietà \<nome proprietà > non può essere eliminato perché è impostato come il **proprietà Discriminator** per l'ereditarietà tra \<nome classe > e \<nome classe >  
  
 La proprietà selezionata viene impostata come la **proprietà Discriminator** per l'ereditarietà tra le classi indicate nel messaggio di errore. Le proprietà non possono essere eliminate se partecipano alla configurazione dell'ereditarietà tra le classi di dati.  
  
 Impostare il **proprietà Discriminator** su una diversa proprietà della classe di dati per consentire la corretta eliminazione della proprietà desiderata.  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  In Progettazione relazionale oggetti selezionare la linea di ereditarietà che connette le classi di dati indicate nel messaggio di errore.  
  
2.  Impostare il **discriminatore** proprietà su una diversa proprietà.  
  
3.  Provare a eliminare nuovamente la proprietà.  
  
## <a name="see-also"></a>Vedere anche
[Messaggi O/R Designer](../data-tools/o-r-designer-messages.md)  
[Gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)