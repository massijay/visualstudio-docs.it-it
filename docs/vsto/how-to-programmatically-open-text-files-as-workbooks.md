---
title: "Procedura: aprire file di testo come cartelle di lavoro a livello di codice | Microsoft Docs"
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
  - "testo [sviluppo per Office in Visual Studio], testo (file)"
  - "testo (file), apertura come cartelle di lavoro"
  - "cartelle di lavoro, apertura di file di testo"
ms.assetid: 056ae3d0-7fe7-4c28-a2a5-5a948baee0e6
caps.latest.revision: 47
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 46
---
# Procedura: aprire file di testo come cartelle di lavoro a livello di codice
  Un file di testo può essere aperto come cartella di lavoro.  È necessario passare il nome del file di testo che si desidera aprire.  È possibile specificare diversi parametri facoltativi, ad esempio il numero di riga da cui iniziare l'analisi e il formato delle colonne dei dati all'interno del file.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Esempio  
 [!code-csharp[Trin_VstcoreExcelAutomation#80](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#80)]
 [!code-vb[Trin_VstcoreExcelAutomation#80](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#80)]  
  
## Compilazione del codice  
 Nell'esempio seguente vengono richiesti i componenti seguenti:  
  
-   Un file di testo delimitato da virgole denominato `Test.txt` che contenga almeno tre righe di testo.  
  
-   Il file di testo `Test.txt` da memorizzare nell'unità C.  
  
## Vedere anche  
 [Uso delle cartelle di lavoro](../vsto/working-with-workbooks.md)   
 [Procedura: aprire cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-open-workbooks.md)   
 [Procedura: creare nuove cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-create-new-workbooks.md)   
 [Procedura: salvare cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-save-workbooks.md)   
 [Procedura: Chiudere cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-close-workbooks.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  