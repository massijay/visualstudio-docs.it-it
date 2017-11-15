---
title: "Procedura: Creare ereditarietà tra tipi (Progettazione classi) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.classdesigner.inheritanceline
helpviewer_keywords:
- inheritance, relationship defining
- relationships, defining inheritance
ms.assetid: 3786a21c-8022-4bf5-9d13-740fd354e93c
caps.latest.revision: "30"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 72cb7612df9c0a80df131ee122df100dc6eeedbe
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-create-inheritance-between-types-class-designer"></a>Procedura: Creare ereditarietà tra tipi (Progettazione classi)
Per creare una relazione di ereditarietà tra due tipi in un diagramma classi usando Progettazione classi, connettere il tipo di base al tipo o ai tipi derivati corrispondenti. È possibile creare una relazione di ereditarietà tra due classi, tra una classe e un'interfaccia o tra due interfacce.  
  
### <a name="to-create-an-inheritance-between-types"></a>Per creare un'ereditarietà tra tipi  
  
1.  Dal progetto in Esplora soluzioni aprire un file del diagramma classi (con estensione cd).  
  
     Se non è disponibile alcun diagramma classi, crearne uno. Vedere [How to: Add Class Diagrams to Projects (Class Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md).  
  
2.  In **Progettazione classi** nella **Casella degli strumenti** fare clic su **Ereditarietà**.  
  
3.  Nel diagramma classi tracciare una linea di ereditarietà tra i tipi desiderati, come indicato di seguito:  
  
    -   Da una classe derivata a una classe di base  
  
    -   Da una classe di implementazione all'interfaccia implementata  
  
    -   Da un'interfaccia di estensione all'interfaccia estesa  
  
4.  Facoltativamente, quando è disponibile un tipo derivato da un tipo generico, fare clic sulla linea di ereditarietà. Nella finestra **Proprietà** impostare la proprietà **Argomenti di tipo** in modo che corrisponda al tipo da usare come tipo generico.  
  
    > [!NOTE]
    >  Se una classe astratta padre include almeno un membro astratto, tutti i membri astratti saranno quindi implementati come classi ereditanti non astratte.  
    >   
    >  Anche se è possibile visualizzare i tipi generici esistenti, non si possono creare nuovi tipi generici. Non si possono inoltre modificare i parametri di tipo per i tipi generici esistenti.  
  
## <a name="see-also"></a>Vedere anche  
 [Ereditarietà](/dotnet/csharp/programming-guide/classes-and-structs/inheritance)   
 [Nozioni fondamentali sull'ereditarietà](/dotnet/visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics)   
 [How to: View Inheritance Between Types (Class Designer)](../ide/how-to-view-inheritance-between-types-class-designer.md)  (Procedura: Visualizzare l'ereditarietà tra tipi (Progettazione classi))  
 [Classi Visual C++ in Progettazione classi](../ide/visual-cpp-classes-in-class-designer.md)