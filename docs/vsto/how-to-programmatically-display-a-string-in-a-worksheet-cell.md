---
title: "Procedura: visualizzare una stringa in una cella del foglio di lavoro a livello di codice | Microsoft Docs"
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
  - "testo [sviluppo per Office in Visual Studio], aggiunta a fogli di lavoro"
  - "fogli di lavoro, visualizzazione di testo in celle"
ms.assetid: b19870ad-e132-49fd-994e-0a91710fa4c9
caps.latest.revision: 45
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 44
---
# Procedura: visualizzare una stringa in una cella del foglio di lavoro a livello di codice
  Con questo esempio viene illustrato come visualizzare testo in una cella a livello di codice.  Per visualizzare testo in una cella, utilizzare un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> oppure un oggetto intervallo nativo di Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Utilizzo di un controllo NamedRange  
 In questo esempio viene utilizzato un controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> denominato `message`.  Il controllo deve essere aggiunto in fase di progettazione a una personalizzazione a livello di documento.  Inserire il codice seguente in una classe Sheet, non nella classe `ThisWorkbook`.  
  
#### Per visualizzare testo in un controllo NamedRange  
  
1.  Impostare il valore del controllo <xref:Microsoft.Office.Tools.Excel.NamedRange> su **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#68](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#68)]
     [!code-vb[Trin_VstcoreExcelAutomation#68](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#68)]  
  
## Utilizzo di un intervallo nativo di Excel  
 Nel codice seguente viene creato un nuovo intervallo a livello di codice a cui viene poi assegnato un valore.  
  
#### Per visualizzare testo in un intervallo di Excel  
  
1.  Recuperare l'intervallo in corrispondenza della cella **A1** in `Sheet1` e impostare il valore su **Hello World**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#69](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#69)]
     [!code-vb[Trin_VstcoreExcelAutomation#69](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#69)]  
  
## Vedere anche  
 [Procedura dettagliata: raccolta di dati tramite Windows Form](../vsto/walkthrough-collecting-data-using-a-windows-form.md)   
 [Risoluzione dei problemi relativi alle soluzioni Office](../vsto/troubleshooting-office-solutions.md)   
 [Controllo NamedRange](../vsto/namedrange-control.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  