---
title: "Procedura: creare un&#39;associazione (relazione) tra classi LINQ to SQL (Progettazione relazionale oggetti) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56133e65-81f3-44c3-bc28-ffdd0671a0d2
caps.latest.revision: 3
caps.handback.revision: 1
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procedura: creare un&#39;associazione (relazione) tra classi LINQ to SQL (Progettazione relazionale oggetti)
Le associazioni tra classi di entità in [!INCLUDE[vbtecdlinq](../data-tools/includes/vbtecdlinq_md.md)] sono analoghe alle relazioni tra tabelle in un database.È possibile creare associazioni tra classi di entità utilizzando la finestra di dialogo **Editor di associazione**.  
  
 Quando si utilizza la finestra di dialogo **Editor di associazione** per creare un'associazione, è necessario selezionare una classe padre e una classe figlio.La classe padre è la classe di entità che contiene la chiave primaria, mentre la classe figlio è la classe di entità che contiene la chiave esterna.Ad esempio, se vengono create classi di entità con mapping alle tabelle Customers e Orders di Northwind, la classe Customer rappresenta la classe padre e la classe Order rappresenta la classe figlio.  
  
> [!NOTE]
>  Quando si trascinano tabelle da **Esplora server**\/**Esplora database** in [!INCLUDE[vs_ordesigner_long](../data-tools/includes/vs_ordesigner_long_md.md)] \([!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)]\), le associazioni vengono create automaticamente in base alle relazioni di chiave esterna esistenti nel database.  
  
 Quando, dopo aver creato un'associazione, la si seleziona in Progettazione relazionale oggetti, nella finestra **Proprietà** è possibile configurare alcune proprietà\(l'associazione rappresenta la linea tra le classi correlate\). Nella tabella riportata di seguito vengono descritte le proprietà di un'associazione.  
  
|Proprietà|Descrizione|  
|---------------|-----------------|  
|**Cardinality**|Controlla se l'associazione è uno\-a\-molti o uno\-a\-uno.|  
|**Child Property**|Specifica se creare una proprietà nella chiave esterna dell'associazione nell'elemento padre, che è una raccolta o un riferimento a record figlio.Ad esempio, nell'associazione tra Customer e Order, se l'impostazione di **Child Property** è **True**, nella classe padre viene creata una proprietà denominata Orders.|  
|**Parent Property**|Proprietà nella classe figlio che fa riferimento alla classe padre associata.Ad esempio, nell'associazione tra Customer e Order, proprietà denominata Customer che fa riferimento al cliente associato per un ordine creato nella classe Order.|  
|**Proprietà partecipanti**|Vengono visualizzate le proprietà dell'associazione e viene fornito un pulsante con i **puntini di sospensione** \(...\) che consente di riaprire la finestra di dialogo **Editor di associazione**.|  
|**Univoco**|Specifica se le colonne esterne di destinazione presentano un vincolo di univocità.|  
  
### Per creare un'associazione tra classi di entità  
  
1.  Fare clic con il pulsante destro del mouse sulla classe di entità che rappresenta la classe padre nell'associazione, scegliere **Aggiungi**, quindi fare clic su **Associazione**.  
  
2.  Verificare che nella finestra di dialogo **Editor di associazione** sia selezionata la **Classe padre** corretta.  
  
3.  Nella casella combinata selezionare **Classe figlio**.  
  
4.  Selezionare le **Proprietà associazione** che mettono in relazione le classi.In genere, questa operazione consente di eseguire il mapping alla relazione di chiave esterna definita nel database.Ad esempio, nell'associazione tra Customers e Orders, le **Proprietà associazione** rappresentano il valore CustomerID per ogni classe.  
  
5.  Scegliere **OK** per creare l'associazione.  
  
## Vedere anche  
 [Cenni preliminari su Progettazione relazionale oggetti](../Topic/LINQ%20to%20SQL%20Tools%20in%20Visual%20Studio1.md)   
 [Procedura dettagliata: creazione di classi LINQ to SQL \(Progettazione relazionale oggetti\)](../Topic/Walkthrough:%20Creating%20LINQ%20to%20SQL%20Classes%20\(O-R%20Designer\).md)   
 [LINQ to SQL](../Topic/LINQ%20to%20SQL.md)   
 [Metodi DataContext \(Progettazione relazionale oggetti\)](../data-tools/datacontext-methods-o-r-designer.md)   
 [Procedura: rappresentare le chiavi primarie](../Topic/How%20to:%20Represent%20Primary%20Keys.md)