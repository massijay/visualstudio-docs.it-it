---
title: "Associazione tardiva nelle soluzioni Office | Microsoft Docs"
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
  - "oggetti [sviluppo per Office in Visual Studio], cast"
  - "tipi [sviluppo per Office in Visual Studio], cast"
  - "automazione [sviluppo per Office in Visual Studio], cast di oggetti"
  - "cast, oggetto a tipo specifico"
ms.assetid: 80b0d23e-df68-4ea9-a02b-238aee8ca9c0
caps.latest.revision: 49
author: "kempb"
ms.author: "kempb"
manager: "ghogen"
caps.handback.revision: 48
---
# Associazione tardiva nelle soluzioni Office
  Alcuni tipi nei modelli a oggetti di applicazioni di Office forniscono una funzionalità disponibile tramite le funzionalità di associazione tardiva.  Ad esempio, alcuni metodi e proprietà possono restituire diversi tipi di oggetti in base al contesto dell'applicazione di Office e alcuni tipi possono esporre metodi o proprietà diversi in contesti diversi.  
  
 [!INCLUDE[appliesto_all](../vsto/includes/appliesto-all-md.md)]  
  
 I progetti di Visual Basic. **Option Strict** dove non è attiva e Visual c destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)] può utilizzare direttamente i tipi che utilizzano queste funzionalità di associazione tardiva.  
  
## Esecuzione del cast implicita ed esplicita dei valori restituiti dell'oggetto  
 Molti metodi e proprietà degli assembly di interoperabilità primari di Microsoft Office restituiscono i valori <xref:System.Object> poiché possono restituire diversi tipi di oggetti.  Ad esempio, la proprietà <xref:Microsoft.Office.Tools.Excel.Workbook.ActiveSheet%2A> restituisce un <xref:System.Object> perché il valore restituito può essere un oggetto <xref:Microsoft.Office.Interop.Excel.Worksheet> o <xref:Microsoft.Office.Interop.Excel.Chart>, in base al foglio attivo.  
  
 Quando un metodo o una proprietà restituisce <xref:System.Object>, è necessario convertire in modo esplicito \(in Visual Basic\) l'oggetto al tipo corretto nei progetti di Visual Basic. in cui **Option Strict** è attivata.  Non è necessario eseguire il cast in modo esplicito dei valori restituiti di <xref:System.Object> nei progetti di Visual Basic. **Option Strict** dove non è attiva.  
  
 Nella maggior parte dei casi, nella documentazione di riferimento vengono elencati i possibili tipi di valore restituito per un membro che restituisce un <xref:System.Object>.  La conversione o il cast dell'oggetto determina l'attivazione di IntelliSense per tale l'oggetto nell'editor del codice.  
  
 Per informazioni sulla conversione in Visual Basic, vedere [Implicit and Explicit Conversions &#40;Visual Basic&#41;](/dotnet/visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions) e [Funzione CType &#40;Visual Basic&#41;](/dotnet/visual-basic/language-reference/functions/ctype-function).  
  
### Esempi  
 Nell'esempio di codice seguente viene illustrato come eseguire il cast di un oggetto a un tipo specifico in un progetto di Visual Basic. in cui **Option Strict** è attivata.  In questo tipo di progetto, è necessario eseguire esplicitamente il cast della proprietà di <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> a <xref:Microsoft.Office.Interop.Excel.Range>.  In questo esempio viene richiesto un progetto Excel a livello di documento con una classe del foglio di lavoro denominata `Sheet1`.  
  
 [!code-vb[Trin_VstcoreProgramming#9](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#9)]  
  
 Nell'esempio di codice seguente viene dimostrato come eseguire in modo implicito il cast di un oggetto a un tipo specifico in un progetto di Visual Basic dove **Option Strict** non è attiva o in un progetto di Visual C\# che ha [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] come destinazione.  In questi tipi di progetti, viene eseguito il cast in modo implicito della proprietà <xref:Microsoft.Office.Tools.Excel.WorksheetBase.Cells%2A> a un <xref:Microsoft.Office.Interop.Excel.Range>.  In questo esempio viene richiesto un progetto Excel a livello di documento con una classe del foglio di lavoro denominata `Sheet1`.  
  
 [!code-csharp[Trin_VstcoreProgramming#10](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/CS/Sheet1.cs#10)]
 [!code-vb[Trin_VstcoreProgramming#10](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreProgramming/VB/Sheet1.vb#10)]  
  
## Accesso ai membri disponibili solo tramite associazione tardiva  
 Alcune proprietà e metodi negli assembly di interoperabilità primari di Office sono disponibili solo tramite associazione tardiva.  Nei progetti di Visual Basic. in cui **Option Strict** è attiva o in Visual c destinati a [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] o [!INCLUDE[net_v45](../vsto/includes/net-v45-md.md)], è possibile utilizzare le funzionalità di associazione tardiva in questi linguaggi per accedere ai membri ad associazione tardiva.  Nei progetti di Visual Basic. **Option Strict** dove è attiva, è necessario utilizzare la reflection per accedere a questi membri.  
  
### Esempi  
 Nell'esempio di codice seguente viene dimostrato come accedere ai membri associati in modo tardivo in un progetto di Visual Basic dove **Option Strict** non è attiva o in un progetto di Visual C\# che ha [!INCLUDE[net_v40_short](../sharepoint/includes/net-v40-short-md.md)] come destinazione.  In questo esempio viene eseguito l'accesso alla proprietà **Name** associata in modo tardivo della finestra di dialogo **Apri file** in Word.  Per utilizzare questo esempio, eseguirlo dalla classe `ThisDocument` o `ThisAddIn` del progetto Word.  
  
 [!code-csharp[Trin_VstcoreWordAutomation#122](../snippets/csharp/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/CS/ThisDocument.cs#122)]
 [!code-vb[Trin_VstcoreWordAutomation#122](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#122)]  
  
 Nell'esempio di codice seguente viene illustrato come utilizzare la reflection per eseguire la stessa attività in un progetto di Visual Basic. in cui **Option Strict** è attivata.  
  
 [!code-vb[Trin_VstcoreWordAutomation#102](../snippets/visualbasic/VS_Snippets_OfficeSP/Trin_VstcoreWordAutomation/VB/ThisDocument.vb#102)]  
  
## Vedere anche  
 [Scrittura di codice nelle soluzioni Office](../vsto/writing-code-in-office-solutions.md)   
 [Parametri facoltativi nelle soluzioni Office](../vsto/optional-parameters-in-office-solutions.md)   
 [Utilizzo del tipo dinamico &#40;Guida per programmatori C&#35;&#41;](/dotnet/csharp/programming-guide/types/using-type-dynamic)   
 [Option Strict Statement](/dotnet/visual-basic/language-reference/statements/option-strict-statement)   
 [Reflection &#40;C&#35; e Visual Basic&#41;](http://msdn.microsoft.com/library/5d1d1bcf-08de-4d0b-97a8-912d17c00f26)   
 [Progettazione e creazione di soluzioni Office](../vsto/designing-and-creating-office-solutions.md)  
  
  