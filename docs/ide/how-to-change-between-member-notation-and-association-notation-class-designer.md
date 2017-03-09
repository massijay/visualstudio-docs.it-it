---
title: 'Procedura: Passare dalla notazione membro alla notazione associazione (Progettazione classi) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- notation, member
- association notation
- member notation
- notation, association
ms.assetid: 65881c5a-d251-4a36-ad0d-73d088436092
caps.latest.revision: 21
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
translationtype: Human Translation
ms.sourcegitcommit: 5db97d19b1b823388a465bba15d057b30ff0b3ce
ms.openlocfilehash: 30bacff7a117cd1e6bdf7a234652177cbc50b0f2
ms.lasthandoff: 02/22/2017

---
# <a name="how-to-change-between-member-notation-and-association-notation-class-designer"></a>Procedura: passare dalla notazione membro alla notazione associazione (Progettazione classi)
In Progettazione classi è possibile modificare il modo in cui il diagramma classi rappresenta una relazione di associazione tra due tipi dalla notazione membro alla notazione associazione e viceversa. I membri visualizzati come linee di associazione spesso offrono una visualizzazione utile della correlazione tra tipi.  
  
> [!NOTE]
>  Le relazioni di associazione possono essere rappresentate come proprietà del membro o campo. Per passare dalla notazione membro alla notazione associazione, un tipo deve avere un membro di un altro tipo. Per passare dalla notazione associazione alla notazione membro, i due tipi devono essere collegati da una linea di associazione. Per altre informazioni, vedere [How to: Create Associations Between Types (Class Designer)](../ide/how-to-create-associations-between-types-class-designer.md) (Procedura: Creare associazioni tra tipi (Progettazione classi)) Se il progetto contiene più diagrammi di classi, le modifiche apportate al modo in cui un diagramma visualizza le relazioni di associazione influiscono solo tale diagramma. Per modificare il modo in cui un altro diagramma visualizza le relazioni di associazione, aprire o visualizzare tale diagramma ed seguire questi passaggi.  
  
### <a name="to-change-member-notation-to-association-notation"></a>Per passare dalla notazione membro alla notazione associazione  
  
1.  Dal nodo del progetto in Esplora soluzioni, aprire il file del diagramma classi (con estensione CD).  
  
2.  Nella forma tipo del diagramma classi, fare doppio clic su proprietà del membro o sul campo che rappresenta l'associazione e scegliere **Mostra come associazione**.  
  
    > [!TIP]
    >  Se non sono visibili campi o proprietà nella forma tipo, i raggruppamenti nella forma potrebbero essere compressi. Per espandere la forma tipo, fare doppio clic sul nome del raggruppamento o fare clic con il pulsante destro del mouse sulla forma tipo e scegliere **Espandi**.  
  
     Il membro scompare dal raggruppamento della forma tipo e viene visualizzata una linea di associazione per connettere i due tipi. La linea di associazione è contrassegnata con il nome della proprietà o del campo.  
  
### <a name="to-change-association-notation-to-member-notation"></a>Per passare dalla notazione associazione alla notazione membro  
  
-   Nel diagramma classi, fare clic con il pulsante destro del mouse sulla linea di associazione e scegliere **Mostra come proprietà** o **Mostra come campo**, come appropriato.  
  
     La linea di associazione scompare e la proprietà viene visualizzata nel raggruppamento appropriato all'interno della forma tipo nel diagramma.  
  
## <a name="see-also"></a>Vedere anche  
 [How to: Create Inheritance Between Types (Class Designer)](../ide/how-to-create-inheritance-between-types-class-designer.md)  (Procedura: Creare l'ereditarietà tra tipi (Progettazione classi))  
 [How to: View Inheritance Between Types (Class Designer)](../ide/how-to-view-inheritance-between-types-class-designer.md)  (Procedura: Visualizzare l'ereditarietà tra tipi (Progettazione classi))  
 [Viewing Types and Relationships (Class Designer)](../ide/viewing-types-and-relationships-class-designer.md)  (Visualizzazione dei tipi e delle relazioni (Progettazione classi))  
 [Procedura: Visualizzare un'associazione di raccolte (Progettazione classi)](../ide/how-to-visualize-a-collection-association-class-designer.md)
