---
title: "Uno o più elementi selezionati contengono un tipo di dati che non è supportato dalla finestra di progettazione | Documenti Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71dcd4f9-2946-42c5-9ce4-99c819ea2785
caps.latest.revision: "4"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.technology: vs-data-tools
ms.openlocfilehash: 31e42bfcaf8904932d4ea864a608c943f638428c
ms.sourcegitcommit: ee42a8771f0248db93fd2e017a22e2506e0f9404
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 11/09/2017
---
# <a name="one-or-more-selected-items-contain-a-data-type-that-is-not-supported-by-the-designer"></a>Uno o più elementi selezionati contengono un tipo di dati non supportato dalla finestra di progettazione
Uno o più elementi trascinati da **Esplora Server**/**Esplora Database** sul [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] contiene un tipo di dati che non è supportato dal [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] (ad esempio, [Tipi CLR definiti dall'utente](http://msdn.microsoft.com/Library/9f70e0b0-3a0d-4eb1-b914-07a5d0c167c2)).  
  
### <a name="to-correct-this-error"></a>Per correggere l'errore  
  
1.  Creare una visualizzazione basata sulla tabella desiderata e che non includa il tipo di dati non supportato.  
  
2.  Trascinare la visualizzazione da **Esplora Server**/**Esplora Database** nella finestra di progettazione.  
  
## <a name="see-also"></a>Vedere anche
[Messaggi O/R Designer](../data-tools/o-r-designer-messages.md)  
[Gli strumenti di LINQ to SQL in Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)