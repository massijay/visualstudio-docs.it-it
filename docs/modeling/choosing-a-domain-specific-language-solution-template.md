---
title: Scelta di un modello di soluzione di linguaggio specifico di dominio | Documenti di Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: 24
author: alancameronwills
ms.author: awills
manager: douge
translationtype: Machine Translation
ms.sourcegitcommit: fd26c504273cae739ccbeef5e406891def732985
ms.openlocfilehash: 2a1ad374c709b9575ff8e3d46bb3d2178a1c3f95
ms.lasthandoff: 02/22/2017

---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Scelta di un modello di soluzione per un linguaggio specifico di dominio
Per creare una soluzione di linguaggio specifico di dominio, scegliere uno dei modelli di soluzioni che sono disponibili nella finestra di progettazione guidata linguaggio specifico di dominio. Scegliendo il modello che rispecchia maggiormente la lingua che si desidera creare, è possibile ridurre le modifiche da apportare alla soluzione inizia.  
  
 I seguenti modelli di soluzioni sono disponibili nella finestra di progettazione guidata linguaggio specifico di dominio.  
  
|Modello|Funzionalità|Descrizione|  
|--------------|--------------|-----------------|  
|Diagrammi classi|-Forme raggruppamento<br />: Ereditarietà della classe<br />: Ereditarietà della relazione<br />-Ereditarietà forma<br />-Proprietà relazione|Utilizzare questo modello di soluzione se il linguaggio specifico di dominio include entità e relazioni che dispongono di proprietà. Questo modello consente di creare un linguaggio specifico di dominio che è simile a diagrammi classi UML. Le entità principali sono le classi e interfacce, con relazioni di associazione, generalizzazione e implementazione. Una classe o interfaccia viene visualizzata come una casella che contiene un elenco di attributi.|  
|Diagrammi dei componenti|-Porte|Utilizzare questo modello di soluzione se il linguaggio specifico di dominio include i componenti, ovvero parti di un sistema software. Questo modello consente di creare un linguaggio specifico di dominio che è simile a diagrammi dei componenti UML. Le entità principali sono i componenti e le porte, che vengono visualizzati come piccole forme all'esterno di componenti.|  
|Diagrammi di flusso attività|-Immagini e forme geometriche<br />-   *Corsie*|Utilizzare questo modello di soluzione se il linguaggio specifico di dominio include i flussi di lavoro, gli Stati o le sequenze. Questo modello consente di creare un linguaggio specifico di dominio che è simile a diagrammi attività UML. L'entità principale è un'attività e la relazione principale è una transizione tra le attività. Il modello include diversi altri elementi, ad esempio allo stato di avvio, stato finale e una barra di sincronizzazione.|  
|Linguaggio minimo|-Una classe e la forma<br />-Una relazione e connettore|Utilizzare questo modello di soluzione se il linguaggio specifico di dominio non assomiglia a altri modelli. Questo modello consente di creare un linguaggio specifico di dominio che dispone di una relazione, vengono rappresentati in e due classi di **della casella degli strumenti** come **casella** e **riga**. La classe e la relazione di disporre di una proprietà di stringa di esempio.|  
|Progettazione Windows Form minimo|-Un modello di piccole dimensioni.<br />-Un Windows Form che visualizza il modello.|Utilizzare questo modello se si desidera compilare un'applicazione in cui un linguaggio DSL è associato a un Windows Form, anziché una finestra di progettazione grafica.<br /><br /> Il modulo che funge da interfaccia utente per la lingua si trova nella cartella Dsl\UI.<br /><br /> È necessario compilare il progetto prima di aprire la finestra di progettazione form.<br /><br /> Per ulteriori informazioni, vedere [creazione di un linguaggio specifico di dominio Windows Forms-Based](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|  
|Minimo di WPF Designer|-Un modello di piccole dimensioni<br />-Un'interfaccia utente di Windows Presentation Foundation che visualizza il modello|Utilizzare questo modello se si desidera compilare un'applicazione in cui un linguaggio DSL è associato a un'interfaccia utente WPF, piuttosto che una finestra di progettazione grafica.<br /><br /> La finestra di progettazione per l'interfaccia utente si trova nella cartella Dsl\UI.<br /><br /> È necessario compilare il progetto prima di aprire la finestra di progettazione dell'interfaccia utente.<br /><br /> Per ulteriori informazioni, vedere [creazione di un linguaggio specifico di dominio WPF-Based](../modeling/creating-a-wpf-based-domain-specific-language.md).|  
|Libreria DSL|-Una raccolta minima|Utilizzare questo modello se si desidera creare una definizione DSL parziale che può essere importata in altre definizioni DSL.|  
  
## <a name="see-also"></a>Vedere anche  
 [Panoramica degli strumenti di linguaggio specifico di dominio](../modeling/overview-of-domain-specific-language-tools.md)

