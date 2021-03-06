---
title: 'Procedura: Visualizzare i tipi esistenti (Progettazione classi) | Microsoft Docs'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: vs-ide-general
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vs.classdesigner.CannotShowBaseType
helpviewer_keywords:
- types [Visual Studio], visualizing
- types [Visual Studio], class diagrams
- class diagrams, types
ms.assetid: de110a4e-5b51-4a40-9dee-615df4d8f999
caps.latest.revision: "27"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 072962f0b699ad88cca8d3d0f10fa7fced926d3e
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: HT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-view-existing-types-class-designer"></a>Procedura: visualizzare i tipi esistenti (Progettazione classi)
Per visualizzare un tipo esistente con i relativi membri, aggiungere la forma a un diagramma classi.  
  
 È possibile vedere tipi locali e tipi a cui viene fatto riferimento. Un tipo locale è presente nel progetto aperto ed è in lettura/scrittura. Un tipo a cui viene fatto riferimento esiste in un altro progetto o in un assembly a cui viene fatto riferimento ed è in sola lettura.  
  
 Per progettare nuovi tipi nei diagrammi classi, vedere [How to: Create Types by using Class Designer](../ide/how-to-create-types-by-using-class-designer.md) (Procedura: Creare tipi tramite Progettazione classi).  
  
### <a name="to-see-types-in-a-project-on-a-class-diagram"></a>Per vedere i tipi di un progetto in un diagramma di classi  
  
1.  In un progetto in Esplora soluzioni aprire un file del diagramma di classi (.cd) esistente. In alternativa, se non sono disponibili diagrammi classi, aggiungerne uno nuovo al progetto. Vedere [How to: Add Class Diagrams to Projects (Class Designer)](../ide/how-to-add-class-diagrams-to-projects-class-designer.md) (Procedura: Aggiungere diagrammi classi ai progetti (Progettazione classi)).  
  
2.  Nel progetto in Esplora soluzioni trascinare un file di codice sorgente nel diagramma di classi.  
  
    > [!WARNING]
    >  Se la soluzione contiene un progetto che condivide il codice con più app, è possibile trascinare file o codice in un diagramma classi solo da queste origini:  
    >   
    >  -   Il progetto di app contenente il diagramma  
    > -   Un progetto condiviso importato dal progetto di app  
    > -   Un progetto a cui si fa riferimento  
    > -   Un assembly  
  
     Le forme che rappresentano i tipi definiti nel file di codice sorgente appariranno nel diagramma nella posizione in cui è stato trascinato il file.  
  
 È anche possibile visualizzare i tipi del progetto trascinando uno o più tipi dal nodo di progetto in Visualizzazione classi al diagramma classi.  
  
> [!TIP]
>  Se non è già visualizzata, aprire Visualizzazione classi dal menu **Visualizza**. Per altre informazioni sulla visualizzazione classi, vedere [Viewing Classes and Their Members](http://msdn.microsoft.com/en-us/71e9e8f3-261a-4e0c-87bf-5ec48b8bf333) (Visualizzazione delle classi e dei relativi membri).  
  
 Per visualizzare i tipi nelle posizioni predefinite del diagramma, selezionare uno o più tipi in Visualizzazione classi, fare clic con il pulsante destro del mouse sui tipi selezionati e scegliere **Visualizza diagramma classi**.  
  
> [!NOTE]
>  Se nel progetto esiste già un diagramma classi chiuso contenente il tipo, tale diagramma verrà aperto per visualizzare la forma del tipo. Se tuttavia nel progetto non sono disponibili diagrammi classi contenenti il tipo, nel progetto verrà creato un nuovo diagramma classi che verrà aperto per visualizzare il tipo.  
  
 La prima volta che viene visualizzato un tipo nel diagramma, la relativa forma appare compressa per impostazione predefinita. È possibile espanderla per visualizzarne il contenuto.  
  
### <a name="to-display-the-contents-of-a-project-in-a-class-diagram"></a>Per visualizzare il contenuto di un progetto in un diagramma classi  
  
1.  In Esplora soluzioni o Visualizzazione classi fare clic con il pulsante destro del mouse sul progetto e scegliere **Visualizzazione**, quindi scegliere **Visualizza diagramma classi**.  
  
     Verrà creato un diagramma classi compilato automaticamente.  
  
## <a name="see-also"></a>Vedere anche  
 [How to: View Inheritance Between Types (Class Designer)](../ide/how-to-view-inheritance-between-types-class-designer.md)  (Procedura: Visualizzare l'ereditarietà tra tipi (Progettazione classi))  
 [Procedura: Personalizzare i diagrammi classi (Progettazione classi)](../ide/how-to-customize-class-diagrams-class-designer.md)   
 [Visualizzazione dei tipi e delle relazioni (Progettazione classi)](../ide/viewing-types-and-relationships-class-designer.md)