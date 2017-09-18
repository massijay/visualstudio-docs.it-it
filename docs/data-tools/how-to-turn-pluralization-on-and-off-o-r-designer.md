---
title: "Procedura: attivare e disattivare la pluralizzazione (Progettazione relazionale oggetti) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9b693bc3-303a-40a9-97ee-9cef5ca3ae81
caps.latest.revision: 2
caps.handback.revision: 2
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: attivare e disattivare la pluralizzazione (Progettazione relazionale oggetti)
Per impostazione predefinita, quando si trascinano oggetti di database con nomi che terminano in s o ies da **Esplora server**\/**Esplora database** in [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md), i nomi delle classi di entità generate vengono modificati dal plurale al singolare.Questa modifica viene apportata per rappresentare in modo più preciso il fatto che viene eseguito il mapping della classe di entità, di cui è stata creata un'istanza, a un singolo record di dati.Ad esempio, l'aggiunta di una tabella Customers a [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] determina una classe di entità denominata Customer poiché conterrà dati relativi a un solo cliente.  
  
> [!NOTE]
>  La pluralizzazione viene attivata per impostazione predefinita solo nella versione in lingua inglese di Visual Studio.  
  
 [!INCLUDE[note_settings_general](../data-tools/includes/note_settings_general_md.md)]  
  
### Per attivare e disattivare la pluralizzazione  
  
1.  Scegliere **Opzioni** dal menu **Strumenti**.  
  
2.  Nella finestra di dialogo **Opzioni** espandere **Strumenti di database**.  
  
> [!NOTE]
>  Se il nodo **Strumenti di database** non è visibile, selezionare **Mostra tutte le impostazioni**.  
  
1.  Fare clic su **Progettazione relazionale oggetti**.  
  
2.  Impostare **Pluralizzazione di nomi** su **Abilitata** \= **False** per impostare [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] in modo che non modifichi i nomi di classe.  
  
3.  Impostare **Pluralizzazione di nomi** su **Abilitata** \= **True** per applicare le regole di pluralizzazione ai nomi di classe degli oggetti aggiunti a [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)].  
  
## Vedere anche  
 [Progettazione relazionale oggetti](../data-tools/linq-to-sql-tools-in-visual-studio2.md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Accesso ai dati in Visual Studio](../data-tools/accessing-data-in-visual-studio.md)