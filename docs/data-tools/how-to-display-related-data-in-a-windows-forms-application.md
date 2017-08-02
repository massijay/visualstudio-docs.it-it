---
title: "Procedura: visualizzare dati correlati in un&#39;applicazione Windows Form | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "aspx"
helpviewer_keywords: 
  - "dati [Windows Form], visualizzazione"
  - "dati [Windows Form], correlati"
  - "visualizzazione di dati su form, dati correlati"
  - "visualizzazione di dati, dati correlati"
  - "visualizzazione di dati di tabelle"
  - "visualizzazione di informazioni di tabelle"
  - "visualizzazione di tabelle, dati correlati"
  - "dati correlati, visualizzazione"
  - "Windows Form, visualizzazione di dati"
ms.assetid: 60b1f1ec-6257-42ab-83f0-06d54ed364fd
caps.latest.revision: 16
caps.handback.revision: 16
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
robots: noindex,nofollow
---
# Procedura: visualizzare dati correlati in un&#39;applicazione Windows Form
Per visualizzare i dati correlati è possibile trascinare gli elementi che condividono lo stesso nodo principale della tabella dalla [Origini dati \(finestra\)](../Topic/Data%20Sources%20Window.md) nel form in uso.  Se ad esempio si dispone di un'origine dati in cui sono presenti una tabella `Customers` e una tabella correlata `Orders`, è possibile visualizzare entrambe le tabelle come nodi di livello principale nella visualizzazione ad albero all'interno della finestra **Origini dati**.  Espandendo il nodo `Customers` vengono visualizzate le colonne e si nota che l'ultima colonna dell'elenco è un nodo espandibile che rappresenta la tabella `Orders`.  Il nodo indica gli ordini relativi a un cliente.  Ciò significa che se si desidera creare un form che consenta di selezionare un cliente e quindi visualizzare un elenco di ordini relativi a tale cliente, sarà necessario trascinare gli elementi da visualizzare da questa singola gerarchia.  
  
 ![Finestra Origini dati con visualizzazione delle relazioni](~/docs/data-tools/media/datasources2.gif "DataSources2")  
Creazione di controlli associati a dati per la visualizzazione di record correlati  
  
 ![Collegamento a video](~/docs/data-tools/media/playvideo.gif "PlayVideo") Per una versione video di questo argomento, vedere [Procedure relative: Aggiornare le tabelle correlate](http://go.microsoft.com/fwlink/?LinkId=143527).  
  
### Per creare controlli per la visualizzazione di record correlati  
  
1.  Aprire il form in [Windows Forms Designer](http://msdn.microsoft.com/it-it/3c3d61f8-f36c-4d41-b9c3-398376fabb15).  
  
2.  Aprire la finestra **Origini dati**.  Per ulteriori informazioni, vedere [Procedura: Aprire la finestra Origini dati](../data-tools/how-to-open-the-data-sources-window.md).  
  
3.  Espandere il nodo che rappresenta la tabella padre nella relazione \(la tabella padre è quella sul lato "uno" di una relazione uno\-a\-molti\).  
  
4.  Trascinare tutti gli elementi della tabella padre da visualizzare dalla finestra **Origini dati** nel form in uso.  
  
5.  Le tabelle figlio correlate vengono visualizzate come nodi espandibili alla fine dell'elenco di colonne della tabella padre.  Trascinare gli elementi da visualizzare da un nodo correlato nel form in uso.  
  
    > [!NOTE]
    >  Trascinando un elemento da un nodo di livello principale si crea un [componente BindingSource](../Topic/BindingSource%20Component.md) separato non correlato che non semplifica lo spostamento nei record correlati.  Per associare i dati correlati, selezionare le tabelle dallo stesso nodo gerarchico.  
  
## Vedere anche  
 [Procedure dettagliate relative ai dati](../Topic/Data%20Walkthroughs.md)   
 [Procedura dettagliata: visualizzazione di dati in un Windows Form](../data-tools/walkthrough-displaying-data-on-a-windows-form.md)   
 [Cenni preliminari sugli oggetti TableAdapter](../data-tools/tableadapter-overview.md)   
 [Creazione e modifica di dataset tipizzati](../data-tools/creating-and-editing-typed-datasets.md)   
 [Cenni preliminari sulle origini dati](../data-tools/add-new-data-sources.md)   
 [Procedura: connettersi ai dati di un database](../data-tools/how-to-connect-to-data-in-a-database.md)   
 [Convalida dei dati](../Topic/Validating%20Data.md)   
 [Procedura: esplorare i dati con il controllo BindingNavigator Windows Form](../Topic/How%20to:%20Navigate%20Data%20with%20the%20Windows%20Forms%20BindingNavigator%20Control.md)