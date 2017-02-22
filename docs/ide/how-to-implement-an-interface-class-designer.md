---
title: "How to: Implement an Interface (Class Designer) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "vs-ide-general"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "interfaces [Visual Studio], implementing"
  - "interfaces [Visual Studio]"
ms.assetid: 81d2cf46-7f60-448c-83e3-1d16bb88ca36
caps.latest.revision: 16
caps.handback.revision: 16
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
---
# How to: Implement an Interface (Class Designer)
[!INCLUDE[vs2017banner](../code-quality/includes/vs2017banner.md)]

In Progettazione classi è possibile implementare un'interfaccia nel diagramma classi connettendola a una classe che fornisce il codice per i metodi di interfaccia.  Verrà generata un'implementazione dell'interfaccia e verrà visualizzata la relazione tra l'interfaccia e la classe come relazione di ereditarietà.  È possibile implementare un'interfaccia disegnando una linea di ereditarietà tra l'interfaccia e la classe oppure trascinando l'interfaccia da Visualizzazione classi.  
  
> [!TIP]
>  Per la creazione di interfacce è possibile seguire la stessa procedura utilizzata per la creazione di altri tipi.  Se l'interfaccia esiste ma non appare nel diagramma classi, è necessario innanzitutto visualizzarla.  Per ulteriori informazioni, vedere [How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md) e [How to: View Existing Types \(Class Designer\)](../Topic/How%20to:%20View%20Existing%20Types%20\(Class%20Designer\).md).  
  
### Per implementare un'interfaccia disegnando una linea di ereditarietà  
  
1.  Nel diagramma classi visualizzare l'interfaccia e la classe che la implementerà.  
  
2.  Disegnare una linea di ereditarietà dalla classe e dall'interfaccia.  
  
     Alla classe verrà collegato un simbolo, mentre un'etichetta con il nome dell'interfaccia identificherà la relazione di ereditarietà.  In Visual Studio vengono generati stub per tutti i membri di interfaccia.  
  
 Per ulteriori informazioni, vedere [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md).  
  
### Per implementare un'interfaccia dalla finestra Visualizzazione classi  
  
1.  Nel diagramma classi visualizzare la classe da utilizzare per l'implementazione dell'interfaccia.  
  
2.  Aprire Visualizzazione classi e individuare l'interfaccia.  
  
    > [!TIP]
    >  Se non è già visualizzata, aprire Visualizzazione classi dal menu **Visualizza**.  Per ulteriori informazioni su Visualizzazione classi, vedere [Viewing Classes and Their Members](http://msdn.microsoft.com/it-it/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333).  
  
3.  Trascinare il nodo di interfaccia sulla forma della classe nel diagramma.  
  
     Alla classe verrà collegato un simbolo, mentre un'etichetta con il nome dell'interfaccia identificherà la relazione di ereditarietà.  In Visual Studio vengono generati stub per tutti i membri di interfaccia. A questo punto, l'interfaccia risulterà implementata.  
  
## Vedere anche  
 [How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md)   
 [How to: View Existing Types \(Class Designer\)](../Topic/How%20to:%20View%20Existing%20Types%20\(Class%20Designer\).md)   
 [How to: Create Inheritance Between Types \(Class Designer\)](../ide/how-to-create-inheritance-between-types-class-designer.md)   
 [Refactoring Classes and Types \(Class Designer\)](../ide/refactoring-classes-and-types-class-designer.md)