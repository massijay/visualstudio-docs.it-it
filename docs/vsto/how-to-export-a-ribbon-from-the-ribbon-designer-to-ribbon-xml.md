---
title: "Procedura: esportare una barra multifunzione dalla finestra di progettazione in un elemento XML della barra"
ms.custom: ""
ms.date: "02/02/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "office-development"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "barra multifunzione personalizzata, XML"
  - "personalizzazione della barra multifunzione, XML"
  - "esportazione della barra multifunzione"
  - "barra multifunzione [sviluppo per Office in Visual Studio], esportazione"
  - "barra multifunzione [sviluppo per Office in Visual Studio], XML"
  - "finestra di progettazione della barra multifunzione [sviluppo per Office in Visual Studio]"
  - "XML [sviluppo per Office in Visual Studio], barra multifunzione"
ms.assetid: 96e0e9ed-4392-4f45-ac33-b6f7c22ea321
caps.latest.revision: 37
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 33
---
# Procedura: esportare una barra multifunzione dalla finestra di progettazione in un elemento XML della barra
  L'elemento **Barra multifunzione \(finestra di progettazione visiva\)** non supporta tutti i possibili tipi di personalizzazione della barra multifunzione.  Per personalizzare la barra multifunzione in modalità avanzate è possibile esportare la barra multifunzione dalla finestra di progettazione nell'XML della barra multifunzione.  
  
> [!NOTE]  
>  Non tutti i valori delle proprietà sono presenti nel file XML della barra multifunzione.  Per ulteriori informazioni, vedere [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md).  
  
 [!INCLUDE[appliesto_ribbon](../vsto/includes/appliesto-ribbon-md.md)]  
  
### Per esportare una barra multifunzione dalla finestra di progettazione in un elemento XML della barra multifunzione  
  
1.  Fare clic con il pulsante destro del mouse sul file di codice della barra multifunzione in **Esplora soluzioni**, quindi scegliere **Visualizza finestra di progettazione**.  
  
2.  Fare clic con il pulsante destro del mouse sulla finestra di progettazione della barra multifunzione, quindi scegliere **Esporta barra multifunzione in XML**.  
  
     In Visual Studio viene aggiunto un file XML e un file di codice XML della barra multifunzione al progetto.  
  
3.  Nella classe del codice della barra multifunzione, trovare i commenti che iniziano con `TODO:.`  
  
4.  Copiare il blocco di codice in questi commenti nella classe **ThisAddin**, **ThisWorkbook** o **ThisDocument**, a seconda del tipo di soluzione che si sta sviluppando.  
  
     Questo codice consente all'applicazione di Microsoft Office di individuare e caricare la barra multifunzione personalizzata.  Per ulteriori informazioni, vedere [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md).  
  
5.  Nella classe **ThisAddin**, **ThisWorkbook** o **ThisDocument**, rimuovere il commento dal blocco di codice.  
  
     Dopo avere rimosso il commento dal codice, il risultato sarà simile all'esempio seguente.  In questo esempio la classe Ribbon è denominata `MyRibbon`.  
  
     [!code-csharp[Trin_Ribbon_Custom_Tab_XML#1](../snippets/csharp/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/CS/ThisAddIn.cs#1)]
     [!code-vb[Trin_Ribbon_Custom_Tab_XML#1](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_Ribbon_Custom_Tab_XML/VB/ThisAddIn.vb#1)]  
  
6.  Passare al file di codice XML della barra multifunzione e cercare l'area `Ribbon Callbacks`.  
  
     In questa area si scrivono i metodi di callback per gestire le azioni dell'utente, ad esempio la selezione di un pulsante tramite il mouse.  
  
7.  Creare un metodo di callback per ogni gestore eventi che si scrive nel codice della finestra di progettazione della barra multifunzione.  
  
8.  Spostare tutto il codice dai gestori eventi in questi metodi di callback e modificarlo in modo che utilizzi il modello di programmazione di estensibilità della barra multifunzione \(RibbonX\).  
  
     Per informazioni sulla scrittura dei metodi di callback e l'utilizzo del modello di programmazione RibbonX, vedere [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md).  
  
## Vedere anche  
 [Cenni preliminari sulla barra multifunzione](../vsto/ribbon-overview.md)   
 [Finestra di progettazione della barra multifunzione](../vsto/ribbon-designer.md)   
 [Elemento XML della barra multifunzione](../vsto/ribbon-xml.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata utilizzando la finestra di progettazione della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-the-ribbon-designer.md)   
 [Procedura dettagliata: creazione di una scheda personalizzata utilizzando l'elemento XML della barra multifunzione](../vsto/walkthrough-creating-a-custom-tab-by-using-ribbon-xml.md)  
  
  