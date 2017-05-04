---
title: "Procedura: eliminare fogli di lavoro da una cartella di lavoro a livello di codice | Microsoft Docs"
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
  - "cartelle di lavoro, eliminazione di fogli di lavoro"
  - "fogli di lavoro, eliminazione"
ms.assetid: c5ae99f0-806d-4320-a29c-75ad444fb996
caps.latest.revision: 48
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 47
---
# Procedura: eliminare fogli di lavoro da una cartella di lavoro a livello di codice
  È possibile eliminare qualsiasi foglio di lavoro da una cartella di lavoro.  Per eliminare un foglio di lavoro, usare l'elemento host del foglio di lavoro o accedere al foglio di lavoro tramite la raccolta Sheets della cartella di lavoro.  
  
 [!INCLUDE[appliesto_xlalldocapp](../vsto/includes/appliesto-xlalldocapp-md.md)]  
  
## Uso dell'elemento host Worksheet  
 Se il foglio di lavoro è stato aggiunto in fase di progettazione in una personalizzazione a livello di documento, per eliminarlo usare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A>.  Il codice seguente elimina un foglio di lavoro da una cartella di lavoro facendo riferimento direttamente all'elemento host del foglio di lavoro.  
  
> [!IMPORTANT]  
>  Questo codice viene eseguito solo in progetti creati usando uno dei modelli di progetto seguenti:  
>   
>  -   Cartella di lavoro di Excel 2013  
> -   Modello di Excel 2013  
> -   Cartella di lavoro di Excel 2010  
> -   Modello di Excel 2010  
>   
>  Se si intende eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento all'assembly **Microsoft.Office.Interop.Excel** quindi è necessario usare le classi da tale assembly per aprire una cartella di lavoro ed eliminare un foglio di lavoro.  Per altre informazioni, vedere [Procedura: sviluppare applicazioni di Office mediante gli assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) e [Riferimento agli assembly di interoperabilità primari di Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
#### Per eliminare un foglio di lavoro mediante un elemento host del foglio di lavoro  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Tools.Excel.Worksheet.Delete%2A> di `Sheet1`.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#17](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#17)]
     [!code-vb[Trin_VstcoreExcelAutomation#17](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#17)]  
  
## Uso della raccolta Sheets della cartella di lavoro di Excel  
 Accedere ai fogli di lavoro mediante la raccolta <xref:Microsoft.Office.Interop.Excel.Sheets> di Microsoft Office Excel nei casi seguenti:  
  
-   Se si intende eliminare un foglio di lavoro in un componente aggiuntivo VSTO.  
  
-   Se il foglio di lavoro che si vuole eliminare è stato creato in fase di esecuzione in una personalizzazione a livello di documento.  
  
 Il codice riportato di seguito elimina un foglio da una cartella di lavoro facendo riferimento alla pagina mediante il numero di indice della raccolta **Sheets**.  Per questo codice si presume che sia già stato creato un nuovo foglio di lavoro a livello di codice.  
  
> [!IMPORTANT]  
>  Se si intende eseguire questa attività in qualsiasi altro tipo di progetto, è necessario aggiungere un riferimento all'assembly **Microsoft.Office.Interop.Excel** quindi è necessario usare le classi da tale assembly per aprire una cartella di lavoro ed eliminare un foglio di lavoro.  Per altre informazioni, vedere [Procedura: sviluppare applicazioni di Office mediante gli assembly di interoperabilità primari](../vsto/how-to-target-office-applications-through-primary-interop-assemblies.md) e [Riferimento agli assembly di interoperabilità primari di Excel 2010](http://go.microsoft.com/fwlink/?LinkId=189585).  
  
#### Per eliminare un foglio di lavoro mediante la raccolta Sheets della cartella di lavoro di Excel  
  
1.  Chiamare il metodo <xref:Microsoft.Office.Interop.Excel._Worksheet.Delete%2A> della raccolta <xref:Microsoft.Office.Interop.Excel.Sheets>.  
  
     [!code-csharp[Trin_VstcoreExcelAutomation#18](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/CS/Sheet1.cs#18)]
     [!code-vb[Trin_VstcoreExcelAutomation#18](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreExcelAutomation/VB/Sheet1.vb#18)]  
  
## Vedere anche  
 [Utilizzo dei fogli di lavoro](../vsto/working-with-worksheets.md)   
 [Procedura: Nascondere i fogli di lavoro a livello di codice](../vsto/how-to-programmatically-hide-worksheets.md)   
 [Procedura: Spostare fogli di lavoro all'interno di cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-move-worksheets-within-workbooks.md)   
 [Procedura: selezionare fogli di lavoro a livello di codice](../vsto/how-to-programmatically-select-worksheets.md)   
 [Procedura: Aggiungere nuovi fogli di lavoro alle cartelle di lavoro a livello di codice](../vsto/how-to-programmatically-add-new-worksheets-to-workbooks.md)   
 [Elemento host Worksheet](../vsto/worksheet-host-item.md)   
 [Accesso globale a oggetti nei progetti di Office](../vsto/global-access-to-objects-in-office-projects.md)   
 [Limitazioni a livello di codice degli elementi e dei controlli host](../vsto/programmatic-limitations-of-host-items-and-host-controls.md)  
  
  