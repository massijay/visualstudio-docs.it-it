---
title: 'Procedura: visualizzare a livello di codice i commenti in un foglio di lavoro | Documenti Microsoft'
ms.custom: 
ms.date: 02/02/2017
ms.reviewer: 
ms.suite: 
ms.technology: office-development
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- worksheets, comments
- comments, worksheets
ms.assetid: f5ce5e7f-bae4-40b7-951c-0f15b140aaf2
caps.latest.revision: "43"
author: gewarren
ms.author: gewarren
manager: ghogen
ms.openlocfilehash: 20381a6db187536dc729c08bb046152a0489e6a1
ms.sourcegitcommit: f40311056ea0b4677efcca74a285dbb0ce0e7974
ms.translationtype: MT
ms.contentlocale: it-IT
ms.lasthandoff: 10/31/2017
---
# <a name="how-to-programmatically-display-worksheet-comments"></a>Procedura: Visualizzare commenti in un foglio di lavoro a livello di codice
  A livello di codice è possibile visualizzare e nascondere i commenti nei fogli di lavoro di Microsoft Office Excel.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
### <a name="to-display-all-comments-on-a-worksheet-in-a-document-level-customization"></a>Per visualizzare tutti i commenti in un foglio di lavoro in una personalizzazione a livello di documento  
  
1.  Impostare la proprietà <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> su **true** se si vogliono visualizzare i commenti, in caso contrario impostare su **false**. Questo codice deve essere inserito in una classe foglio, non nella classe `ThisWorkbook` .  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/CSharp/Trin_VstcoreExcelAutomationCS/Sheet1.cs#31)]
     [!code-vb[Trin_VstcoreExcelAutomation#31](../vsto/codesnippet/VisualBasic/Trin_VstcoreExcelAutomation/Sheet1.vb#31)]  
  
### <a name="to-display-all-comments-on-a-worksheet-in-an-application-level-vsto-add-in"></a>Per visualizzare tutti i commenti in un foglio di lavoro in un componente aggiuntivo VSTO a livello di applicazione  
  
1.  Impostare la proprietà <xref:Microsoft.Office.Interop.Excel.Comment.Visible%2A> su **true** se si vogliono visualizzare i commenti, in caso contrario impostare su **false**.  
  
     [!code-csharp[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/CSharp/trin_vstcoreexcelautomationaddin/ThisAddIn.cs#21)]
     [!code-vb[Trin_VstcoreExcelAutomationAddIn#21](../vsto/codesnippet/VisualBasic/trin_vstcoreexcelautomationaddin/ThisAddIn.vb#21)]  
  
## <a name="see-also"></a>Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: aggiungere a livello di codice ed eliminare commenti di foglio di lavoro](../vsto/how-to-programmatically-add-and-delete-worksheet-comments.md)   
 [Panoramica degli elementi e dei controlli host](../vsto/host-items-and-host-controls-overview.md)  
  
  