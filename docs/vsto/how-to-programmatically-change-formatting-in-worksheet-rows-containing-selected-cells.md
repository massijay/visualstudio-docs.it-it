---
title: "Procedura: modificare la formattazione nelle righe di un foglio di lavoro contenenti celle selezionate a livello di codice | Microsoft Docs"
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
  - "formattazione [sviluppo per Office in Visual Studio]"
  - "righe [sviluppo per Office in Visual Studio]"
  - "fogli di lavoro, modifica della formattazione"
ms.assetid: c55cd488-98d1-46c6-9715-0e9212d178de
caps.latest.revision: 38
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 37
---
# Procedura: modificare la formattazione nelle righe di un foglio di lavoro contenenti celle selezionate a livello di codice
  È possibile modificare il tipo di carattere di un'intera riga contenente una cella selezionata per ottenere, ad esempio, testo in grassetto.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### Per visualizzare in grassetto la riga corrente e in stile normale la riga precedentemente visualizzata in grassetto  
  
1.  Dichiarare una variabile statica per tenere traccia della riga selezionata in precedenza.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#37](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#37)]
     [!code-vb[Trin_VstcoreExcelAutomation#37](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#37)]  
  
2.  Recuperare un riferimento alla cella corrente tramite la proprietà <xref:Microsoft.Office.Interop.Excel._Application.ActiveCell%2A>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#38](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#38)]
     [!code-vb[Trin_VstcoreExcelAutomation#38](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#38)]  
  
3.  Applicare lo stile in grassetto alla riga corrente tramite la proprietà <xref:Microsoft.Office.Interop.Excel.Range.EntireRow%2A> della cella attiva.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#39](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#39)]
     [!code-vb[Trin_VstcoreExcelAutomation#39](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#39)]  
  
4.  Assicurarsi che il valore corrente di `previousRow` non sia 0.  Uno 0 \(zero\) indica che si scorre per la prima volta questo codice.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#40](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#40)]
     [!code-vb[Trin_VstcoreExcelAutomation#40](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#40)]  
  
5.  Assicurarsi che la riga corrente sia diversa da quella precedente.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#41](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#41)]
     [!code-vb[Trin_VstcoreExcelAutomation#41](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#41)]  
  
6.  Recuperare un riferimento a un intervallo che rappresenta la riga selezionata in precedenza e impostare tale riga in modo che non sia in grassetto.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#42](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#42)]
     [!code-vb[Trin_VstcoreExcelAutomation#42](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#42)]  
  
7.  Archiviare la riga corrente in modo che possa diventare la riga precedente al successivo passaggio.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#43](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#43)]
     [!code-vb[Trin_VstcoreExcelAutomation#43](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#43)]  
  
 Nell'esempio riportato di seguito viene illustrato il metodo completo.  
  
## Esempio  
 [!code-csharp[Trin_VstcoreExcelAutomation#36](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#36)]
 [!code-vb[Trin_VstcoreExcelAutomation#36](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#36)]  
  
## Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: Applicare stili agli intervalli nei fogli di lavoro a livello di codice](../vsto/how-to-programmatically-apply-styles-to-ranges-in-workbooks.md)   
 [Procedura: copiare dati e formattazione nei fogli di lavoro a livello di codice](../vsto/how-to-programmatically-copy-data-and-formatting-across-worksheets.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)  
  
  